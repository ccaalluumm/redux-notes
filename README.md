# Redux Notes
Redux is a predictable state container for JS (JavaScript apps). Most notable, it provides state management, but also live code editing and time-travelling debugging.

## Redux Store
In Redux, there is only a single state object, responsible for the entire state of an app. This is called the store. Therefore, any component willing to manipulate state must do so
through the Redux store.

State flow is unidirectional, making it easier to manage and track state.

### Creating a store
The Redux store is an object, created via the `createStore()` method. This method takes a `reducer` function as a required argument. Example: `const store = Redux.createStore(reducer)

### Accessing the store
The store can be accessed via the `getState()` function, which is called upon a Redux store object

### Reducers (Handling Actions)
When an action is dispatched to the store, a reducer function will handle the state modificatin that takes place in response to recieving of an action.

A reducer always takes two arguments: `state` and `action`, and always return a new state.

This is all a reducer funciton will do, ever. No more, no less.

Another law is that state is read-only. The implication of this being that the reducer function must always return a new copy of state, and never modify state directly.

#### Combining Reducers
Redux provides the `combineReducers` method:

```javascript
const rootReducer = Redux.combineReducers({
    auth: authenticationReducers,
    notes: notesReducer
});
```


### Listeners
Listener functions can be subscribed to the store. These functions are called whenever an action is dispatched against the store. `store.subscribe(callback())`.

## Actions
All state updates in Redux are trigered by dispatching actions. An action is a JS object, containing information about an action event that has occured.

Actions are assigned a type, and may carry data.

```javascript
let action = {
    type: 'LOGIN'
}
```

### Creators
A Creator is simply a function that returns an action.

### Dispatching
The Redux store has a build in method called `dispatch`, which accepts a creator as an argument.
