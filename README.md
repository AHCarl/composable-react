# Inheritance and Composition

Over time, programmers have developed various ways to reuse code.
Low level abstractions for reusing code include:
* Functions, which create resuseable processes
* Classes, which create reuseable bundles of related data and behavior

Higher level methods for resusing code include:
* **Inheritance**, which allows more specific classes to inherit traits of more generic (parent) classes
* **Composition**, which allows specific entities to be composed of more generic "building blocks"

Watch this vido on composition and inheritance: https://youtu.be/wfMtDGfHWpA, then answer the questions below.

## Questions

1. Answer the commented questions:

1. ```javascript
   const barkable = (state) => ({
       bark: () => 'Woof',
       whimper: () => 'MmmmmmmmMMMM...'
   })
   
   const driveable = (state) => ({
       drive: () => state.position = state.position + 1
   })
   
   const robotDog = (name, position) => {
   	const state = { name, position }
       return { ...barkable(state), ...driveable(state)}
   }
   
   let k9 = robotDog(k9, 4)
   
   // a. What methods will k9 have?
   // b. How many properties will k9 have?
   
   k9.drive()
   
   // c. What would k9.position evaluate to?
   ```

2. Answer the commented questions:

   ```javascript
   const barkable = (state) => ({
       bark: () => 'Woof',
       whimper: () => 'MmmmmmmmMMMM...'
   })
   
   const driveable = (state) => ({
       drive: () => state.position = state.position + 1
   })
   
   const barkableAndDriveable ( state ) => ({   
   	...barkable(state), ...driveable(state)
   })
   // ^^ Creating a more specific thing by configuring less specific things
   
   const robotDog = (name, position) => {
   	return barkableAndDriveable({ name, position })
   }
   
   let k9 = robotDog(k9, 4)
   
   // a. Is this k9 unit any different than the last one?
   // b. Would it make sense to say that barkableAndDriveable is composed of barkable and driveable:
   //		i. From a programming perspective?
   //		ii. From a logical/common sense perspective?
   ```

   3. How could compositional thinking be applied to React?
      1. Check out these docs as you think it through: https://reactjs.org/docs/higher-order-components.html
   4. How have we already used composition in React?
   5. How could composition help us "cross-cut" the concern of maintain our state?