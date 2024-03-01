from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/hello', methods=['GET'])
def hello():
    name = request.args.get('name')
    if name:
        return jsonify({'message': 'Hello, {}!'.format(name)})
    else:
        return jsonify({'message': 'Hello, World!'})

@app.route('/post_example', methods=['POST'])
def post_example():
    data = request.json
    if data and 'name' in data:
        return jsonify({'message': 'Received POST request with name: {}'.format(data['name'])})
    else:
        return jsonify({'message': 'Please provide a name in the POST request.'})

if __name__ == '__main__':
    app.run(debug=True)
