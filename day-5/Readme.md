# HLS - Training day 5

# React Redux

**Goals**
In this tutorial, we will build a small blog app. It will fetch posts and comments from an API. I've created the same app with both plain Redux, and Redux Toolkit (RTK), the officially sanctioned toolset for Redux. Here are the links to the source and demos of both the plain and RTK versions.

**What is Redux?**
Redux is a state container for JavaScript applications. Normally with React, you manage state at a component level, and pass state around via props. With Redux, the entire state of your application is managed in one immutable object. Every update to the Redux state results in a copy of sections of the state, plus the new change.

**Why should I use Redux?**
- Easily manage global state - access or update any part of the state from any Redux-connected component
- Easily keep track of changes with Redux DevTools - any action or state change is tracked and easy to follow with Redux. The fact that the entire state of the application is tracked with each change means you can easily do time-travel debugging to move back and forth between changes.
-
## Redux Overview
Before we get into the code, let's look at the different parts of Redux and how they work together.
Redux is made up of actions, reducers, state and the store. Each thing does one specific task. Lets take an example:

![](https://www.freecodecamp.org/news/content/images/2021/04/ReduxDataFlowDiagram-49fa8c3968371d9ef6f2a1486bd40a26-1.gif)

First at all, I want to tell you, today will be boring. If you're feel boring, You can watch some video youtube
- English: https://www.youtube.com/watch?v=CVpUuw9XSjY
- Vietnamese: https://www.youtube.com/watch?v=Sq_Qt8PWf_Y

### Actions
An action sends data from your application to the Redux store. An action is conventionally an object with two properties: type and (optional) payload. The type is generally an uppercase string (assigned to a constant) that describes the action. The payload is additional data that may be passed.

```
Type:
const TODO_ADD_TASK = 'TODO_ADD_TASK'

const addTask = (task) => ({ type: TODO_ADD_TASK, payload: task })
```

### Reducers
A reducer is a function that takes two parameters: state and action. A reducer is immutable and always returns a copy of the entire state. A reducer typically consists of a switch statement that goes through all the possible action types.

```
const initialState = {
  todos: [
    {id: 1, text: 'Eat'},
    {id: 2, text: 'Sleep'},
  ],
  loading: false,
  hasErrors: false,
}

function todoReducer(state = initialState, action) {
  switch (action.type) {
    case TODO_ADD_TASK:
      return {
        ...state,
        todos: [action.payload, ...state.todos],
      }
    default:
      return state
  }
}
```

### Store
The Redux application state lives in the store, which is initialized with a reducer. When used with React, a <Provider> exists to wrap the application, and anything within the Provider can have access to Redux.

```
import {createStore} from 'redux'
import {Provider} from 'react-redux'
import reducer from './reducers'

const store = createStore(reducer)

render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root'),
)
```

## Homework

After you have a very basic concepts in Redux. And you will research redux advanced with the keyword
- Redux thunk: https://github.com/reduxjs/redux-thunk
- Redux selector: https://redux.js.org/usage/deriving-data-selectors

## Reference
- **Learning Resources**
https://redux.js.org/introduction/learning-resources
