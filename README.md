# finalproject
#Food Analyzer. Group members: Carrie Goodian, Aaron Duke, Noah Marinelli


from nutritionix import Nutritionix
nix = Nutritionix(app_id="557650c9", api_key="b3c987d0bdb894c210751635b54c082d")

while True:
    user_input = input("Enter a food or type 'quit': ")
    r_var = nix.search(user_input, results="0:1").json()
    food = nix.item(id=r_var['hits'][0]['_id']).json()
    if user_input == 'quit':
        print('Stick around to check out the food blog!💃🏻')
        import webbrowser
        import time

        time.sleep(2)
        webbrowser.open('http://www.sproutedkitchen.com/recipes/')
        break
    print("* Dietary Fiber: ", food['nf_dietary_fiber'])
    print("* Calories: ", food['nf_calories'])
    print("* Calories From Fat: ", food['nf_calories_from_fat'])
    print("* Cholesterol: ", food['nf_cholesterol'])
    print("* Sugars: ", food['nf_sugars'])
    print("* Total Fat: ", food['nf_total_fat'])
    print("* Total Carbohydrates: ", food['nf_total_carbohydrate'])   
