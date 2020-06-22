[![Build Status](https://travis-ci.com/cococolacode/react-redux.svg?branch=master)](https://travis-ci.com/cococolacode/react-redux)

## Getting Started
To learn redux we must first understand what state is. <br>
 **_what is a state?_** <br>
*The simple answer is, It's a place where the data comes from.*<br>
 *In other words, “state” is what allows you to create components that are dynamic and interactive.*<br>
*Example*
``` javascript
Class MyClass extends React.Component { 
   this.state = { value : "my-new-value" }; 
  render(){
  return <div>{ths.state.value}</div>;// this will return the my-new-value
 }
}
```
**_What is redux?_**<br>
*Redux is a predictable state container for JavaScript apps.*<br>
**_Merits_**<br>
 * _It helps apps to scale by providing a way to manage state through a unidirectional data flow model._
 * _redux devTools is awosome._<br>
 ### Redux flow
 All data in redux application follows the same lifecycle patterns which  make the app logics more predicable and easy to learn.<br>
 * store
 * actions
 * reducers<br>
 
### Installation 
``` terminal 
yarn add react-redux redux
```
> *redux --> for creating store*<br>
> *React Redux requires React 16.8.3 or later.*

 **Let's create our first store**
 ``` javascript
 import {createStore} from 'redux';
 
 function reducer(){ //reducer 
 return 'this is a stae'
 }
 const store = createStore(reducer); //passing reducer function as a argument to createStore.
 console.log(store); // output: this is a state, since the reduce 'this is a state'. 
 ```
 We have successfully created our first store.<br>
 *Let's create an action, which is basically just an object with a type and a payload*
 ``` javascript
 //increment action
 const increment = {
     type:'INCREMENT',
     payload:1
 }
 
 //decrement action
 const decrement = {
       type:'DECREMENT',
       payload:1
 }
 
 ```
 *Let's dispatch our action,* 
 ``` javascript 
 store.dispatch([increment, decrement]) --> it will first dispatch increment and then decrement
 ```
 The above gives you a basic idea on how redux works.Now, let's dive into deep.<br />
 **Reducer** <br />
 reducer have two parameters - _initial state of a reducer and the action_. It listens to every single action that is send.So, there needs to be figuring out what to do differently for each action.
```javascript
 reducer(state,action){
 const {type, payload} = action;
 switch(type){
 case 'INCREMENT':
       return state+payload;
 case 'DECREMENT':
       return state-payload;
 }
}
 ```
 _It should prints the action type and payload in console as below._<br>
 ![redux](https://user-images.githubusercontent.com/47861774/57584969-3e2c0480-7501-11e9-8770-a39dc0c4c996.png)
 
 ### Combining ruducers
 Let's combine a reducers into a single reducer to pass into our store.<br>
 _Assume that, we got 2 reducers - productsReducer & usersReduser_
 ``` javascript
 //products reducer
 const productsReducer = (state = [],action) => {
   return state;
 }
 
 //users reducers
 const usersReducer = (state = [],action) => {
   return state;
 }
 ```
 *combination*
 ``` javascript
 import {combineReducers} from 'redux'; //importing combineReducers from redux 
 const allReducers = combineReducers({ 
    products:productsReducers,
    users:usersReducers
 });
 ```
 we can pass this combine reducers  to our store.
 ``` javascript
  const store = createStore(allReducers);
 ```
 Now, our store looks a lot more like a real world store in an application that is prepared to scale.
 
 ### Setting an initial state for the store
 Some time we want to pre-populate our store with datas. For that, we normally pass our initial state as a second argument when creating a store.
 ``` javascript
    const store = createStore(allReducers,
    {
       products:[{name:'samsung galaxy J7 prime'}],
       users:[{name:'bhupen'}]
    });
 ```
 

 


