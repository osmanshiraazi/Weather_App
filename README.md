﻿# Weather App

This is a simple weather app that allows users to search for the weather in any city. The app uses the OpenWeatherMap API to fetch weather data.

## Getting Started

To get started, clone the repository and install the dependencies.

```
git clone https://github.com/your-username/weather-app.git
cd weather-app
npm install
```

## Running the App

To run the app, simply run the following command:

```
npm start
```

The app will be available at http://localhost:3000.

## Code Explanation

The code for this app is relatively simple. The main file is `index.js`. This file contains the following code:

```
import React, { useState, useEffect } from "react";
import axios from "axios";

const App = () => {
  const [weather, setWeather] = useState(null);
  const [city, setCity] = useState("Delhi");

  useEffect(() => {
    axios
      .get(
        `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${process.env.REACT_APP_OPENWEATHERMAP_API_KEY}`
      )
      .then((response) => {
        setWeather(response.data);
      });
  }, [city]);

  return (
    <div>
      <h1>Weather in {city}</h1>
      <ul>
        <li>Temperature: {weather?.main?.temp}°F</li>
        <li>Feels like: {weather?.main?.feels_like}°F</li>
        <li>Humidity: {weather?.main?.humidity}%</li>
        <li>Wind speed: {weather?.wind?.speed} mph</li>
        <li>Wind direction: {weather?.wind?.deg}°</li>
      </ul>
    </div>
  );
};

export default App;
```

This code first imports the necessary React and axios libraries. It then defines a functional component called `App`. The `App` component has two state variables: `weather` and `city`. The `weather` state variable stores the weather data for the current city, and the `city` state variable stores the name of the current city.

