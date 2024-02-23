# FastAPI OAuth 2.0 Example

This is a basic FastAPI application demonstrating the OAuth 2.0 authorization flow using an authorization code grant. The example simulates user authorization with an external OAuth 2.0 provider.

## Installation

1. Make sure you have [Poetry](https://python-poetry.org/) installed:

    ```bash
    curl -sSL https://install.python-poetry.org | python3 -
    ```

2. Clone this repository:

    ```bash
    git clone https://github.com/your-username/fastapi-oauth-example.git
    cd fastapi-oauth-example
    ```

3. Install dependencies using Poetry:

    ```bash
    poetry install
    ```

## Configuration

### Step 1: Create a Discord Application

Go to the Discord Developer Portal.
Click on the "New Application" button in the top right corner.
Enter a name for your application and click the "Create" button.

### Step 2: Set Up OAuth2

In your application settings, navigate to the "OAuth2" tab on the left sidebar.
In the "Redirects" section, click the "Add Redirect" button. This is where Discord will redirect users after they authorize your application.
For development purposes, you can use <http://localhost:8000/login/callback> as your redirect URI. Replace 8000 with the port your FastAPI server is running on.

### Step 3: Get Your Client ID and Client Secret

In the "General Information" tab, scroll down to the "Client Information" section. Here, you will find your CLIENT ID. Copy this value.
Scroll down further to the "Client Secret" section. Click on the "Copy" button to copy your CLIENT SECRET.

**Note**: Keep your client secret secure. Do not share it publicly.

### Step 4: Use in FastAPI Application

Now that you have your CLIENT ID, CLIENT SECRET, and Redirect URL, you can use them in your FastAPI application. Update the .env file or directly set these values in your Python code where necessary.

```env
DISCORD_CLIENT_ID=your_client_id
DISCORD_CLIENT_SECRET=your_client_secret
DISCORD_REDIRECT_URI=<http://localhost:8000/login/callback>
```

Replace your_client_id and your_client_secret with the values you obtained from the Discord Developer Portal.

Customize the DISCORD_SCOPES variable based on your application's requirements. The default scope in the example is set to:

```env
DISCORD_SCOPES=identify email guilds guilds.join guilds.members
```

You can adjust this string to include only the scopes your application needs. Refer to the Discord [OAuth2 documentation](https://discord.com/developers/docs/topics/oauth2#shared-resources-oauth2-scopes) for a list of available scopes.

## Usage

### Run the FastAPI server

```bash
poetry run python main.py dev
```

Open your browser and navigate to <http://localhost:8000/>.

Follow the OAuth 2.0 authorization flow by clicking on the login link.

After successful authorization, the server will print an access token.

Feel free to customize it further based on your specific needs.
