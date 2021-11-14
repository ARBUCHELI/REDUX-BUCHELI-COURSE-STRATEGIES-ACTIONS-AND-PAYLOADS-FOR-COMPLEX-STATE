# REDUX-BUCHELI-COURSE-STRATEGIES-ACTIONS-AND-PAYLOADS-FOR-COMPLEX-STATE

# REDUX-LESSONS-INSTRUCTOR-ANDRES-R.-BUCHELI

## Usage:

The initialState structure has been defined and you know that the state of this application has 3 slices: allRecipes, favoriteRecipes, and searchTerm. Now, you can begin thinking about how the user will trigger changes to these slices of state through actions.

Remember, actions in Redux are represented by plain JavaScript objects that have a type property and are dispatched to the store using the store.dispatch() method. 

When an application state has multiple slices, individual actions typically only change one slice at a time. Therefore, it is recommended that each action’s type follows the pattern 'sliceName/actionDescriptor', to clarify which slice of state should be updated.

For example, in a todo application with a state.todos slice, the action type for adding a new todo might be 'todos/addTodo'.

For the Recipes application, what do you think some of the action type strings might be? What user interactions might trigger them to be dispatched?

Write some of your ideas down before revealing the actions you will be using:

* 1. 'allRecipes/loadData': This action will be dispatched to fetch the needed data from an API right when the application starts.

* 2. 'favoriteRecipes/addRecipe': This action will be dispatched any time the user clicks on the ❤️ icon of a recipe from the full set of recipes.

* 3. 'favoriteRecipes/removeRecipe': This action will be dispatched any time the user clicks on the 💔 icon of a recipe from their list of favorites.

* 4. 'searchTerm/setSearchTerm': This action will be dispatched any time the user changes the text of the search input field to filter the full set of recipes.

* 5. 'searchTerm/clearSearchTerm': This action will be dispatched any time the user clicks on the “X” button next to the search input field.


It’s also important to consider which of these actions will have a payload — additional data passed to the reducer in order to carry out the desired change-of-state. For example, consider the actions for the searchTerm slice:

```
store.dispatch({ 
  type: 'searchTerm/setSearchTerm', 
  payload: 'Spaghetti' 
});
// The resulting state: { ..., searchTerm: 'Spaghetti' }

 
store.dispatch({ 
  type: 'searchTerm/clearSearchTerm' 
});
// The resulting state: { ..., searchTerm: '' }
```

* When the learner types in a search term, that data needs to be sent to the store so that the React components know which recipes to render and which to hide.

* When the user clears the search field, no additional data needs to be sent because the store can simply set the search term to be an empty string again.
Once you have a clear idea of the types of actions that will be dispatched in your application, when they will be dispatched, and what payload data they will carry, the next step is to make action creators.

Remember, action creators are functions that return a formatted action object.

Action creators enable Redux programmers to re-use action object structures without typing them out by hand and they improve the readability of their code, particularly when dealing with bulky payloads.
