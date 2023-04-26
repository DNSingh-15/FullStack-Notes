## React

### 1. React
React is a JavaScript library for building user interfaces
* react is a unidireactional ( we can pass data only from parent to child component )

### 2. Hooks
Hooks are functions that allow to use the state and other features in functional components

* it is introduced in react 18 update

### 3. prop drilling
It is a process of passing data from one component to another component ( parent to child and child to parent )


## Next.js
### 1. Next.js
Next.js is a react framework for building server-rendered applications

Next.js gives the routing service 

### 2. optimize the performance in Next.js
Next.js provides performance optimizations, such as automatic 
1. caching => using memoization
2. server-side rendering.
3. lazy loading
4. code splitting

### 3. difference between getStaticProps and getServerSideProps 
getStaticProps is used to fetch data at build time

getServerSideProps is used to fetch data at request time



## Redux
Redux is a state management library

<img title="a title" alt="Alt text" src="https://www.clariontech.com/hs-fs/hubfs/Image3-43.png?width=417&name=Image3-43.png">

### 1. Action
what to do

actions is an object that have a type filed it only tells what to do

### 2. Reducer
how to do 

reducer is a function that take the current state and action as argument and return new state

### 3. Store
Store is an object which holds the state of the applications
* here data is stored
* store brings together the state, action and reducers

methods --
1. createStore()  -- how to create store
2. dispatch() -- how to perform actions
3. getState() -- how to get current state value







 
