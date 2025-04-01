# Weather Application

## Overview
This full-stack weather application allows users to retrieve current weather data by entering a zip code. It features user authentication and interacts with a PostgreSQL database for managing user information. The backend is powered by Java, while the frontend is built using Vue.js, and weather data is fetched from the OpenWeather API.

## Technologies Used
- **Frontend**: Vue.js for building a responsive and interactive UI
- **Backend**: Java for handling user authentication and communication with the database
- **Database**: PostgreSQL for storing user credentials and other related data
- **API Integration**: OpenWeather API for retrieving weather data
- **Axios** for making API requests
- **Vuex** for state management
- **Vue Router** for navigation and authentication handling

## Features
- ✅ User authentication (login, register, and logout)
- ✅ Weather data retrieval by entering a zip code
- ✅ Responsive design for a seamless experience on both desktop and mobile devices
- ✅ Secure backend authentication with JWT tokens
- ✅ Route protection based on authentication status (users must be logged in to access weather data)
- ✅ Data fetched from OpenWeather API and displayed in an intuitive format

## How It Works
1. **User Authentication**  
   Users can register, log in, and log out. Upon logging in, a JWT token is stored in local storage, which is used to authenticate the user in subsequent requests.
   
2. **Weather Data Retrieval**  
   After logging in, users can input a zip code to fetch weather data from the OpenWeather API. The data is displayed in a user-friendly format, showing the current weather information.
   
3. **Routing and Navigation**  
   The application uses Vue Router to manage navigation. Certain routes (such as the weather page) are protected and require the user to be authenticated. If the user is not logged in, they will be redirected to the login page.

4. **Frontend and Backend Interaction**  
   The frontend is built using Vue.js and makes HTTP requests to the backend (Java) using Axios. The backend handles user authentication and serves as a middleman for interacting with the OpenWeather API.

## Setup and Running Instructions

### Prerequisites
- Java 8+ (for the backend)
- PostgreSQL (for the database)
- Node.js (for the frontend)
- OpenWeather API key (sign up on [OpenWeather](https://openweathermap.org/api))

### Backend Setup
1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/weather-app.git
    cd weather-app/java
    ```

2. Set up your database:
   - Create a PostgreSQL database for your project.
   - Update the `application.properties` file with your database credentials.

3. Start the backend:
    ```bash
    mvn spring-boot:run
    ```

### Frontend Setup
1. Navigate to the frontend directory:
    ```bash
    cd weather-app/vue
    ```

2. Install dependencies:
    ```bash
    npm install
    ```

3. Set up the OpenWeather API key:
   - Create a `.env` file and add the API key:
     ```bash
     VITE_OPENWEATHER_API_KEY=your_openweather_api_key
     ```

4. Run the frontend:
    ```bash
    npm run dev
    ```

### Running the Application
1. Open the frontend in your browser.
2. Register a new account or log in with an existing one.
3. Once logged in, navigate to the "Weather" page to enter a zip code and view the current weather data.

## API Endpoints Used

- **Weather Data**  
  This endpoint fetches weather data based on the zip code provided by the user, and it requires the user to be logged in for authentication.

  **Endpoint**:  
  `GET /weather?zip={zipcode}`

  **Parameters**:  
  - `zip` (required): The zip code for which weather data will be retrieved.

  **Authentication**:  
  The endpoint requires the user to be authenticated. The logged-in user's information is accessed via the `Principal` object, and the corresponding weather data is returned.

  **Response**:  
  A `WeatherDto` object containing the weather data for the specified zip code.

## API Key Setup

To interact with the OpenWeather API, you'll need to obtain a free API key. Follow these steps to get your key:

1. Visit the [OpenWeather API website](https://openweathermap.org/api).
2. Sign up for a free account if you haven't already.
3. After logging in, go to the "API keys" section in your account dashboard.
4. Copy the generated API key.

Once you have your API key, you need to add it to your project:

1. Create a `.env` file in the frontend directory (where your project resides).
2. Add the following line to the `.env` file:
   ```bash
   VITE_OPENWEATHER_API_KEY=your_api_key_here
