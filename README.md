
# Recipes App

A simple and interactive web application for searching and saving your favorite meals. Built with **HTML**, **CSS**, and **JavaScript**, this app fetches meal data from [TheMealDB API](https://www.themealdb.com/) and allows users to explore recipes, mark favorites, and view detailed meal information.

## Features
- **Meal Search**: Search for meals by name using the search bar.
- **Random Meal**: Displays a random meal on page load.
- **Favorite Meals**: Save your favorite meals for quick access.
- **Meal Details**: Click on a meal to view detailed information (ingredients, instructions, etc.).
- **Responsive Design**: Works seamlessly on both desktop and mobile devices.

---

## Technologies Used
- **Frontend**: HTML, CSS, JavaScript.
- **API Integration**: Fetches meal data from [TheMealDB API](https://www.themealdb.com/).
- **Local Storage**: Saves favorite meals locally in the browser.

---

## How to Use
1. Clone or download the repository.
2. Open the `index.html` file in your browser.
3. Use the search bar to find meals.
4. Click on a meal to view its details.
5. Mark meals as favorites by clicking the heart icon.
6. View your favorite meals in the "Favorite Meals" section.

---

## Code Overview

### HTML Structure
The HTML file defines the structure of the app:
- **Search Bar**: Allows users to input search terms.
- **Favorite Meals Section**: Displays a list of favorited meals.
- **Meals Section**: Displays search results or random meals.
- **Popup Container**: Shows detailed meal information in a popup.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Recipes App</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css" />
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.1/dist/css/bootstrap.min.css" rel="stylesheet" />
    <link rel="stylesheet" href="style.css">
    <script src="scripts.js" defer></script>
</head>
<body>
  <div class="mobile-container">
      <header>
          <input type="text" id="search-term" />
          <button id="search"><i class="fas fa-search"></i></button>
      </header>
      <div class="fav-container">
          <h3>Favorite Meals</h3>
          <ul class="fav-meals" id="fav-meals"></ul>
      </div>
      <div class="meals" id="meals"></div>
      <p style="display: flex; text-align: center; justify-content: center; color:red;font-size: 13px;">
         Mayouf©2023</p>
  </div>
  <div class="popup-container hidden" id="meal-popup">
      <div class="popup">
          <button id="close-popup" class="close-popup">
              <i class="fas fa-times"></i>
          </button>
          <div class="meal-info" id="meal-info"></div>
      </div>
  </div>
</body>
</html>

### JavaScript Functionality
The JavaScript code handles the app's logic, including fetching data from the API, managing favorites, and displaying meal details.

#### Key Functions:
1. **`getRandomMeal()`**: Fetches a random meal from the API and displays it.
2. **`getMealById(id)`**: Fetches a meal by its ID.
3. **`getMealsBySearch(term)`**: Fetches meals based on a search term.
4. **`addMeal(mealData, random)`**: Adds a meal to the DOM.
5. **`addMealLS(mealId)`**: Saves a meal ID to local storage.
6. **`removeMealLS(mealId)`**: Removes a meal ID from local storage.
7. **`fetchFavMEals()`**: Fetches and displays favorited meals.
8. **`showMealInfo(mealData)`**: Displays detailed meal information in a popup.

```javascript
const mealPopup = document.getElementById("meal-popup");
const mealInfoEl = document.getElementById("meal-info");
const popupCloseBtn = document.getElementById("close-popup");
const mealsEL = document.getElementById("meals");
const favoriteContainer = document.getElementById("fav-meals");
const searchTerm = document.getElementById("search-term");
const searchBtn = document.getElementById("search");

// Fetch and display a random meal on page load
getRandomMeal();

// Fetch and display favorited meals
fetchFavMEals();

// Event listener for search button
searchBtn.addEventListener("click", async () => {
  mealsEL.innerHTML = ""; // Clear previous results
  const search = searchTerm.value;
  const meals = await getMealsBySearch(search);
  if (meals) {
    meals.forEach((meal) => {
      addMeal(meal);
    });
  }
});

// Event listener to close the meal details popup
popupCloseBtn.addEventListener("click", () => {
  mealPopup.classList.add("hidden");
});
```

---

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/MarkMayouf/Recipe_Application.git
   ```
2. Open the `index.html` file in your browser.

---

## Contributing
Contributions are welcome! If you'd like to improve the app, feel free to fork the repository and submit a pull request.

-
