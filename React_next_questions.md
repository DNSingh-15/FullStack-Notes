# React

## 1. React
React is a JavaScript library for building user interfaces
* react is a unidireactional ( we can pass data only from parent to child component )

## 2. Components
Components are reusable pice of code 
#### Types ---
* Functional components
* Class components

## 3. props
props are argument passed into react component and it is data transfer method
* props is used for the data transfer from parent to child component

## 2. Hooks
Hooks are state and lifecycle methods in functional component.
* it is introduced in react 16 update
### a. useState
useState is a hook that allows to store and manage data
* state is mutable
* used for rendering dynamic changes
### b. useEffect
useEffect is a hook it's just like a function it runs on any render 
```
cindition rendering of useEffect 

const [count, setCount] = useState(0);
  useEffect(() => {
    document.title = `You clicked ${count} times`;
  },[]);     ============>>>>>>>> it runs only one time in the starting

const [count, setCount] = useState(0);
  useEffect(() => {
    document.title = `You clicked ${count} times`;
  },[count]);    ============>>>>>>>> it runs only when the count state 
```
### c. useRef
* useRef is a hook it allows to continue values between renders. ( alternative useState is not working then we have to go with useRef )
* useRef is used for dom manupulation
```
sometimes we have to do direct modification on the html like-
Focus, color, value etc we have to handle with useref 

exm-
 const inputRef = useRef();
 const handlebutton = () => {
      inputRef.current.focus();
      inputRef.current.style.color="red"
    }
  };
  return ( <input ref={inputRef} ... />
  <button onClick={handlebutton}></button>
);
```

  
### d. useContext 
useContext hook allows components to access data without any rely on props

### e,f. useMemo and useCallback
```
useMemo and useCallback are react hook and used for optimizing the application performance
* useMemo and useCallback are used to stop unneccessory call or render

useMemo =>
* useMemo Hook returns a memoized value.
* useMemo Hook only runs when one of its dependencies update.

useCallback=>
* useMemo Hook returns a memoized funtion.
* useCallback Hook only runs when one of its dependencies update.

learning => Technical Suneja youtube video
```

## 3. prop drilling
It is a process of passing data from one component to another component ( parent to child and child to parent )

## 4. difference between Virtual DOM and DOM
### Virtual DOM	
It is the virtual representation of Real DOM
* if we want to update one node then VDOm update that perticular node
* Faster updates	
* Cannot update HTML directly	

### DOM	
Document Object Model is a programming interface for web documents.
* High demand for memory and more wastage
* Slow updates
* Able to directly manipulate HTML

## 5. JSX
It is a file that is used in React

jsx give us the power to write HTML and Javascript combined
* browser is not supported the js file, Because JSX is not valid JavaScript, so browsers can't read it directly

## 8. Why is React widely used
1. because it has huge community and because of VDOM it is fast
2. UI testing becomes very easy.
3. high readability and easy understanding of code.
4. React can be used for both client-side and server-side with using of next.
5. It boosts application performance and efficiency.

### types
1. Local state.
2. Global state.
3. Server state => server state handles the server-side data introduced by the HTTP request
4. URL state.

## 9. events
event is an action that could be triggered by button click, mouse hover etc

## 10. Stateful and Stateless component
### Stateful
components that hold some state, means statefull components are keep tracking of changing data
* it has state

### Stateless
components wihtout any state management is called stateless component
* it doesn't have state, it has props
* components print out whatever is given

## 11. Optimize the performance method
1. code optmization
2. catching
3. node profiling
4. database management

## 12. slowly rendering React application
slow rendering in React is mostly because of the number of re-render operations

There are two main tools
1. memo() => Memo is a higher-order component, it is used to communicate something of immediate importance to people within a business or organization
2. PureComponent  => Its return value is only determined by its input values


## 13. lifecycle 
1. mounting => componentDIdMount()
2. updating => componentDIdUpdate()
3. unmounting => componentWillUnmount()

### purpose of using the constructor
It  is used to initialize the state and bind with event handlers

## 14. controlled component and an uncontrolled component
### controlled component
here state is managed by React and component's value is updated through its props
### uncontrolled component
here state is managed by the DOM and component's value is updated through its event handlers

## 15. "ref" attribute
"ref" attribute is used to get a reference to the DOM node

 It is used for handling focus, media playback, and animations.

## 16. React Fragment
It is a pattern to handle the multiple elements, without adding an extra node to the DOM
```
a. return (
    <React.Fragment>
      <ChildA />
      <ChildB />
      <ChildC />
    </React.Fragment>
  );
  
  b. return (
    <>
      <ChildA />
      <ChildB />
      <ChildC />
    </>
  );
  b.  return (
      <div>
        <td>Hello</td>
        <td>World</td>
      </div>
    );
```





# Next.js
## 1. Next.js
Next.js is a react framework for building server-rendered applications

Next.js gives the routing service 

## 2. optimize the performance in Next.js
Next.js provides performance optimizations, such as automatic 
1. caching => using memoization
2. server-side rendering.
3. lazy loading
4. code splitting

## 3. difference between getStaticProps and getServerSideProps 
getStaticProps is used to fetch data at build time

getServerSideProps is used to fetch data at request time



# Redux
Redux is a state management javascript library
* it has single store

<img title="a title" alt="Alt text" src="https://www.clariontech.com/hs-fs/hubfs/Image3-43.png?width=417&name=Image3-43.png">

## 1. Action
what to do

actions is an object that have a type filed it only tells what to do

## 2. Reducer
how to do 

reducer is a function that take the current state and action as argument and return new state

## 3. Store
Store is an object which holds the state of the applications
* here data is stored
* store brings together the state, action and reducers

methods --
1. createStore()  -- how to create store
2. dispatch() -- how to perform actions
3. getState() -- how to get current state value







 
