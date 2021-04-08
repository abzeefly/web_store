Please include a brief write up to explain your thought process, these are example prompts

## What principles did you apply
I used basic Vue development principles of breaking down app into components and using components as a factory pattern to add similar components with different properties.
I used watchers for detecting changes and using them to update the products list, I used computed and lodash functions to create a sorted by price list and V-if, 
V-else-if, V-else and V-for to create these components iteratively with conditions.
I used bootstrap CSS and utilised bootstrap Vue layout components to make the website responsive and better looking.
I used the sidebar for user information and popover for cart.
I used a form input with V-model to get my search string with a watcher to filter the product list with that search string.
I used Heroku to deploy the static app.

## An explanation of decisions taken and their motivation
I used bootstrap CSS as I was comfortable using it. 
I did not use Vuex for store management due to time constraints and because I could just use #refs for what I needed.
I used a navbar to give an easier access to all the tools implemented.
I used card layout similar to amazon.com for my products for familiarity for the user.
I used the sidebar for user info for quick access and hiding capability, also used v-model and disabled properties to make quick and easy to edit user info.

## Motivation for tool selection
As there was a time constraint, I went with technologies I have used before and am familiar with the capabilities and limitations.

## If time is limited what you would have done given more time
I would use Vuex for state and store management
Implement a grid system and pagination for the products
Implement Add to Cart feature.
Toggle password field in user info from text to hidden and vice versa.
Make the app look better and implement a few changes for better responsiveness.
