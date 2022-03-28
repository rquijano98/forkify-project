# Forkify Project

## Description

Forkify is a recipe application with custom recipe uploads. This application allows you to search for hundreds of recipes by using keywords (e.g. type in cheese, several recipes with the word "cheese" in it are rendered). These results are fetched via the Forkify API (https://forkify-api.herokuapp.com/v2). This application also allows you to upload your own personal recipes that only you have access to when you run the application. This personal uploading is also done via the Forkify API by using a unique key that you can retrieve by going to the actual API page.

_**Disclaimer**: This project was created as part of an online course. The HTML and Sass files were downloaded and not personally created by me (they were provided directly by the course instructor as this was a course focusing on primarily JavaScript). I do not have a deep understanding of the Sass like I do with the HTML and JavaScript._

## How to Run the Application

### Getting Started

<ins>**NOTE**</ins>: These instructions assume the user has Node.js and Node package manager (npm) installed already.

1. Download or clone the "forkify-project" repository from GitHub.
2. Open a terminal and navigate to the newly created directory, which should just be called "forkify-project."
3. Obtain and input a key into the newly downloaded application (see **Get Key for Adding Recipes** below and complete all 5 of those steps before moving on to step 4).
4. In the forkify-project directory, type "npm i" and hit enter in order to install the necessary dependencies for running the application.
5. After dependencies have been installed, type "npm start" and hit enter in order to run the application.
6. Open http://localhost:1234 where the application should be running.

### Get Key for Adding Recipes

1. Go to the following page: https://forkify-api.herokuapp.com/v2.
2. Click on the red button that says "Generate your API key."
3. Copy the key.
4. Navigate to config.js in the forkify-project/js directory on your machine.
5. Replace the value of KEY in the config.js file with the copied key.

### Changing Settings

There are a few settings of this application that can be changed by changing certain values in config.js (which is found in the folder called "js" in the forkify-project directory):

- **API URL**: This should not be changed by the user of this application.

- **Amount of time that passes before a fetch from the API is considered unsuccessful**: This time (in seconds) is determined by TIMEOUT_SEC. If the API takes longer than this time to fetch data, then a timeout message is shown to the user.

- **Amount of recipes listed (off to the left after a user searches a key word) per pagination page**: The amount of recipe listings per page is controlled by RES_PER_PAGE.

- **API key that allows user to upload recipes:** This can be updated by copying and pasting a generated key (how to get a key is explained in the "Get Key for Adding Recipes section) into the value of KEY.

- **Amount of seconds that pass before the modal window (which renders after you attempt a recipe upload) closes**: This is controlled by changing MODAL_CLOSE_SEC.

## Highlights

### Search Functionality

1. The user can type any keyword into the search bar at the top of the page. After hitting enter or pressing search, a list of recipes at the left of the application will be rendered.
2. If there are no recipes to match the keyword, a message will appear at the left application that informs the user of this.

### List of Rendered Recipes

1. After the user has made a successful search, all recipes containing that word will be rendered off to the left of the page.
2. If there are more than a certain threshold number of recipes that get rendered (this threshold number is determined in config.js), then pagination occurs. There will be buttons at the bottom of the list that allow the user to jump to different pages of recipes. If the threshold number of recipes for pagination is not met, no pagination will occur and there will not be buttons at the bottom of the list that allow the user to jump to different pages of recipes.
3. When one of these recipes in the list is clicked on, the details of the recipe are rendered on the right side of the page.

### Detailed Recipe Rendering (What is Rendered After Clicking on a Recipe in the Recipe List)

1. After clicking on a recipe in the recipe list, the details of that recipe get rendered off to the right of the page. This detailed rendering includes a picture, a name, time to prepare, servings, recipe ingredients, and a button at the bottom that redirects the user to the page that contains the preparation directions.
2. The servings for a recipe can be changed. Pressing the + or - sign changes the servings for a particular recipe. The quantity of ingredients changes accordingly.
3. Clicking the orange bookmark icon (which is the orange circular button to the right of the "Servings - +" section) bookmarks a recipe. This bookmark will persist even after a reload because the bookmark is saved in local storage. Clicking the bookmark icon again will unbookmark the recipe.

### Bookmarked Recipes

1. To access all recipes that have been bookmarked, the user can click on the "BOOKMARKS" button, which is on the very right of the header that also contains the search bar. When this is clicked, a list of all of the recipes that the user has bookmarked is rendered.
2. The user can click on any of the items in this bookmarks list, and the details of that recipe get rendered on the page.

### Add Recipes

1. To add recipes, the user first needs to input their own personal API key into config.js (how this is done is discussed in the **Getting Key for Adding Recipes** section above).
2. The user can add recipes by clicking on the "ADD RECIPE" button, which is just to the left of the "BOOKMARKS" button. A form should pop up that has fields where the user can input information about a recipe they want to upload.
3. Form validation is present. If the user attempts to enter inputs into any of the fields that are not acceptable, the recipe will not upload when they press the orange upload button and they instead will be shown a prompt that tells them what they need to change.
4. If a recipe is successfully uploaded, the user will always be able to find their own recipe by searching for it (as long as they are using the same API key, they will have access to all of the recipes they have uploaded).
5. A successfully uploaded recipe is automatically bookmarked.

<ins>**NOTE**</ins>: A current shortcoming of this application is that whenever the user successfully uploads a recipe (or, in some instances, when they are shown an error message regarding an invalid input), they must reload the page entirely to be able to upload another recipe. If they try to upload another recipe before reloading, they simply will be shown the modal window that tells them whatever their error message was before (if they had invalid input before) or that will tell them "Recipe was successfully uploaded!" (if they had just successfully uploaded before).
