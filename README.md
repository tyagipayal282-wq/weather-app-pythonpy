# weather-app-pythonpy
INTERN ID :- CITS2279
FULL NAME- PAYAL TYAGI
TOPIC - WEATHER APP
SOURCE CODE --
 import requests

# Enter your API key here
API_KEY = "YOUR_API_KEY"

# Take city name as input
city = input("Enter city name: ")

# API URL
url = f"https://api.openweathermap.org/data/2.5/weather?q={city}&appid={API_KEY}&units=metric"

try:
    response = requests.get(url)
    data = response.json()

    if data["cod"] != 200:
        print("City not found!")
    else:
        city_name = data["name"]
        country = data["sys"]["country"]
        temperature = data["main"]["temp"]
        feels_like = data["main"]["feels_like"]
        humidity = data["main"]["humidity"]
        pressure = data["main"]["pressure"]
        weather = data["weather"][0]["description"]
        wind_speed = data["wind"]["speed"]

        print("\n===== Weather Report =====")
        print(f"City       : {city_name}, {country}")
        print(f"Temperature: {temperature}°C")
        print(f"Feels Like : {feels_like}°C")
        print(f"Weather    : {weather.capitalize()}")
        print(f"Humidity   : {humidity}%")
        print(f"Pressure   : {pressure} hPa")
        print(f"Wind Speed : {wind_speed} m/s")

except requests.exceptions.RequestException:
    print("Unable to connect to the server.")
