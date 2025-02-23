import requests
import config

def get_weather(api_key, location):
    url = f"http://api.openweathermap.org/data/2.5/weather?q={location}&appid={api_key}&units=metric"
    response = requests.get(url)
    if response.status_code == 200:
        data = response.json()
        temp = data['main']['temp']
        humidity = data['main']['humidity']
        weather_description = data['weather'][0]['description']
        print(f"Location: {location}")
        print(f"Temperature: {temp}°C")
        print(f"Humidity: {humidity}%")
        print(f"Weather: {weather_description}")
    else:
        print("Error: Unable to fetch weather data")

def main():
    api_key = config.API_KEY
    location = input("Enter the city name or ZIP code: ")
    get_weather(api_key, location)

if __name__ == "__main__":
    main()
