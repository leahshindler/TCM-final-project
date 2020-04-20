# TCM-final-project
Jamie Begleiter/Leah Shindler final project

import requests, json, pprint # for the API data

print('What holiday is coming up next?')
holiday = input()

url = f'https://api.spoonacular.com/recipes/random?number=1&tags={holiday}&apiKey=6f873121665c40adb0c1fa22d3b87c09'
response = requests.get(url)
response.raise_for_status()  # check for errors

# load json data
jsonData = json.loads(response.text)

celebrating = 'yes'
cook = 'no'
answer = 'yes'

print('Are you going to be celebrating this holiday?')
celebrating = input()
if celebrating == 'yes':
    print('Are you going to cook for the meal?')
    cook = input()
    if cook == 'no':
        print('Me neither.')
    else:
        print('Would you like a recipe?')  # ask user if they want to receive a recipe
        answer = input()
        if answer == 'yes':
            print('Here is your recipe:')
            pprint.pprint(jsonData)
        else:
            print('Okay, enjoy your holiday.')
else:
    print('Okay, have a nice day.')







