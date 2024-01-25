# Flask API Routes and HTTP Operations Guide

This README file provides a comprehensive guide on declaring API routes, handling cookies, retrieving form data, and returning various HTTP status codes in a Flask web application.

## Table of Contents

1. [Declaring API Routes](#declaring-api-routes)
2. [Working with Cookies](#working-with-cookies)
3. [Retrieving Request Form Data](#retrieving-request-form-data)
4. [Returning HTTP Status Codes](#returning-http-status-codes)
5. [Examples](#examples)
6. [Contributing](#contributing)
7. [License](#license)

## 1. Declaring API Routes

In Flask, API routes are declared using the `@app.route()` decorator. This decorator associates a URL path with a Python function, making it accessible via HTTP requests.

```python
from flask import Flask

app = Flask(__name__)

@app.route('/api/v1/resource', methods=['GET'])
def get_resource():
    # Your logic to handle GET requests for the resource
    return jsonify({'message': 'Resource retrieved successfully'})
```

In the example above, the `get_resource` function is associated with the `/api/v1/resource` URL path and is accessible via HTTP GET requests.

## 2. Working with Cookies

Flask provides a convenient `request.cookies` object to interact with cookies. To set a cookie, use the `set_cookie` method:

```python
from flask import Flask, make_response

app = Flask(__name__)

@app.route('/set-cookie')
def set_cookie():
    resp = make_response('Cookie set successfully')
    resp.set_cookie('user_id', '123')
    return resp
```

To retrieve a cookie, use the `request.cookies` object:

```python
from flask import Flask, request

app = Flask(__name__)

@app.route('/get-cookie')
def get_cookie():
    user_id = request.cookies.get('user_id')
    return f'User ID: {user_id}'
```

## 3. Retrieving Request Form Data

To retrieve form data from a request, use the `request.form` object. This is commonly used for handling POST requests with form data.

```python
from flask import Flask, request

app = Flask(__name__)

@app.route('/submit', methods=['POST'])
def submit_form():
    username = request.form.get('username')
    password = request.form.get('password')
    # Your logic to process the form data
    return f'Form submitted: Username - {username}, Password - {password}'
```

## 4. Returning HTTP Status Codes

Flask allows you to return specific HTTP status codes along with your response. Use the `make_response` function to set the status code:

```python
from flask import Flask, jsonify, make_response

app = Flask(__name__)

@app.route('/not-found')
def not_found():
    response = make_response(jsonify({'error': 'Not Found'}), 404)
    return response
```

In this example, a 404 Not Found status code is returned along with a JSON response.

## 5. Examples

For more comprehensive examples, check the `examples` directory in this repository. It includes sample Flask applications demonstrating various use cases.

## 6. Contributing

If you find any issues or have suggestions for improvements, feel free to contribute by creating an issue or submitting a pull request. Your contributions are highly appreciated!

## 7. License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
