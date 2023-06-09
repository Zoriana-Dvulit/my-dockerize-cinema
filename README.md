# Dockerize-DRF-Cinema

**Installing using GitHub**
Clone the repository:
git clone https://github.com/Zoriana-Dvulit/Dockerize-DRF-Cinema.git

Сhange directory :
$ cd Dockerize-DRF-Cinema

**_Run with Docker_**

1. Build the Docker image:
   docker build -t cinema-app .

2. Run the Docker container:
   docker run -p 8000:8000 cinema-app
   The API will now be available at http://localhost:8000/.

Note: If you make any changes to the code, you will need to rebuild the Docker image before running the container again.

Alternatively, you can also run the API locally without Docker by following these steps:

Run locally

1. Create a virtual environment:
   python -m venv venv
2. Activate the virtual environment:
   source venv/bin/activate
3. Install the necessary packages:
   pip install -r requirements.txt
4. Migrate the database:
   python manage.py migrate
5. Run the development server:
   python manage.py runserver
   The API will now be available at http://localhost:8000/.

## Environment Variables

This project uses environment variables to store sensitive information. To set up the environment variables:

1. Copy the `.env_sample` file and rename it to `.env`.

2. Replace the sample values in the `.env` file with your actual values.

3. Add `.env` to the `.gitignore` file to prevent sensitive information from being committed to the Git repository.

4. Install the `python-dotenv` library to load the environment variables from the `.env` file:
    pip install python-dotenv

5. Import the `dotenv` library at the top of your Django `settings.py` file:
    import dotenv
    dotenv.load_dotenv()

6. Use the `os` library to get the values of your environment variables in the `settings.py` file:
    SECRET_KEY = os.getenv("DJANGO_SECRET_KEY")

**Note:** You can find samples of the required environment variables in the `.env_sample` file.


## Registering and Logging In

To use our API, you'll need to create an account and log in to authenticate your requests. 

Here's how you can do that:
1. Register 
To register for an account, send a POST request to /api/auth/register/) with your email, username and password
You should receive a response with a token field that you'll need to use to authenticate future requests. 
2. Login
To log in to your account, send a POST request to /api/auth/login/ with your email and password
You should receive a response with a token field that you'll need to use to authenticate future requests.
3. Authenticating Requests
To authenticate your requests, you'll need to include an Authorization header in your request with the value
Token <your-token> where <your-token> is the token you received when you registered or logged in.

## API Endpoints Descriptions

**Cinema API Endpoints**

Movies

[GET] /api/cinema/ - Receive a list of movies

[GET] /api/cinema/int:pk/ - Receive details of a specific movie

[POST] /api/cinema/ - Create a new movie

[PUT] /api/cinema/int:pk/ - Update details of a specific movie

[DELETE] /api/cinema/int:pk/ - Delete a specific movie

Actors

[GET] /api/cinema/actors/ - Receive a list of actors

[GET] /api/cinema/actors/int:pk/ - Receive details of a specific actor

[POST] /api/cinema/actors/ - Create a new actor

[PUT] /api/cinema/actors/int:pk/ - Update details of a specific actor

[DELETE] /api/cinema/actors/int:pk/ - Delete a specific actor

**User API Endpoints**

[GET] /api/user/ - Receive a list of users

[GET] /api/user/int:pk/ - Receive details of a specific user

[POST] /api/user/ - Create a new user

[PUT] /api/user/int:pk/ - Update details of a specific user

[DELETE] /api/user/int:pk/ - Delete a specific user
