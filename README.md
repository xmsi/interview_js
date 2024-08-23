# Вопросы и ответы на собеседования для JS developer'a

### ***1. Что такое асинхронность***

  Асинхронность в JavaScript (JS) позволяет выполнять операции, не блокируя основной поток выполнения кода. Это означает, что другие части кода могут продолжать выполняться, пока ожидаются результаты выполнения асинхронных операций, таких как запросы к серверу, чтение файлов и таймеры. 
  Сразу после каждой макрозадачи движок исполняет все задачи из очереди микрозадач перед тем, как выполнить следующую макрозадачу или отобразить изменения на странице, или сделать что-то ещё.
  - сначала добавляется в стек вызовов (call stack) и передаётся к WebApi
  - удаляется из call stack
  - после успешного ответа передается в Task queue ()
  - Event Loop проверяет если 

  [Очень полезный сайт](https://learn.javascript.ru/event-loop)

### ***CoreJS***
- **qs.stringify()** converts a JavaScript object or array into a query string, which is typically used in URL parameters.
- The $ prefix can be a convention for indicating that a function or property is related to the framework or library’s internal workings, not something the user would typically need to modify
- **Object Literal**
```
let keyName = "isAvailable";
let myObject = { [keyName]: false };

console.log(myObject); // Output: { isAvailable: false }
console.log(myObject.isAvailable); // Output: false
```
- **ObjectDestruturing** when you extract innner objects variables to your new variable: const {sm1, sm2} = obj
  
### ***2. Vue***
- пустой **template** можно использовать как обёртку для if, for, etc
- **props:** Used for receiving data from a parent component. They act as external inputs and can be validated and given default values.\
  They are also reactive, but you should not change them in childs, instead create internal duplicate of prop.
- **data():** Defines the internal state of the component. It is reactive and changes to these properties will automatically update the view.
- Globally add mixin to all components, and you can use them whenever you want with $this.someComputedProperty
  ```
  install (Vue) {
    Vue.mixin({
      computed: {
  ```
- **Vue.use** is used to install a Vue plugin. The plugin is typically an object or a function that provides functionality and is meant to be used across the entire Vue application. A plugin object usually has an **install** method. This method is called by Vue.use and receives the Vue constructor as an argument. The install method is where the plugin can add functionality to Vue, such as global components, directives, mixins, or prototype methods.
- **Accessing child components:** If you assign a ref attribute to a child component in the template, this.$refs will hold a reference to the child component instance. This allows you to access the child component's data and methods directly from the parent component.
```
<template>
  <ChildComponent ref="child" />
</template>

<script>
export default {
  mounted() {
    this.$refs.child.childMethod()
  }
}
</script>

```

#### Vuex

In Vuex, the `actions` constant is an object where you define functions (known as "actions") that can contain asynchronous operations and commit mutations to change the state in a Vuex store. Actions are useful when you need to perform operations like API calls, timers, or any asynchronous tasks before committing a mutation to update the state.

### Why Use Vuex Actions?

1. **Asynchronous Operations**: Actions allow you to perform async operations (e.g., fetching data from an API) before committing mutations to update the state.

2. **Centralized Logic**: They help centralize complex logic that might involve multiple steps or conditions, ensuring that your components remain focused on the UI logic.

3. **Maintainability**: By keeping asynchronous and complex logic in actions, your code becomes easier to maintain and test.

### Example of Usage

Suppose you have a Vuex store managing a list of products, and you need to fetch the product list from an API:

```javascript
// store.js
import Vue from 'vue';
import Vuex from 'vuex';
import axios from 'axios';

Vue.use(Vuex);

export const store = new Vuex.Store({
  state: {
    products: [],
  },
  mutations: {
    setProducts(state, products) {
      state.products = products;
    },
  },
  actions: {
    async fetchProducts({ commit }) {
      try {
        const response = await axios.get('/api/products');
        commit('setProducts', response.data);
      } catch (error) {
        console.error('Failed to fetch products:', error);
      }
    },
  },
});
```

### Explanation

- **State**: The `state` contains the data managed by the store, in this case, an array of `products`.
  
- **Mutations**: The `setProducts` mutation directly modifies the `products` array in the state. **mutations** are functions that directly modify the state of the store. Unlike actions, mutations are synchronous, meaning they make changes to the state immediately. They are the only way to change the state in Vuex, ensuring that state changes are trackable and predictable.  To trigger a mutation, you use the **commit** method. This is how you apply changes to the state.

- **Actions**:
  - The `fetchProducts` action is defined inside the `actions` object.
  - It uses `axios` to make an asynchronous request to fetch products from an API endpoint.
  - Once the data is fetched, the `commit` method is used to call the `setProducts` mutation, updating the state with the new list of products.
  - In Vuex, when you define an action, it receives a context object as its first argument. This context object provides several properties and methods that you can use to interact with the Vuex store. Some of the key properties and methods include:

    - state: The current state of the Vuex store.
    - commit: A method used to commit mutations.
    - dispatch: A method used to dispatch other actions.
    - getters: The store's getters.

### Using the Action in a Component

To use the `fetchProducts` action in a Vue component, you can dispatch it using `this.$store.dispatch`:

```javascript
<template>
  <div>
    <button @click="loadProducts">Load Products</button>
    <ul>
      <li v-for="product in products" :key="product.id">{{ product.name }}</li>
    </ul>
  </div>
</template>

<script>
import { mapActions, mapState } from 'vuex';

export default {
  computed: {
    ...mapState(['products']),
  },
  methods: {
    ...mapActions(['fetchProducts']),
    loadProducts() {
      this.fetchProducts();
    },
  },
};
</script>
```

### Explanation

- **`mapState`**: This maps the `products` state to a computed property, allowing the component to access the list of products.

- **`mapActions`**: This maps the `fetchProducts` action to a method in the component. You can then call `this.fetchProducts()` to dispatch the action.

- **Component Method**: The `loadProducts` method is tied to a button click and calls the `fetchProducts` action.

### Summary

- **Vuex Actions** are defined in the `actions` constant and are used to handle asynchronous tasks or complex logic before committing mutations.
- They help keep your components clean and focused on the UI, while the business logic is handled centrally in the store.
- Actions are dispatched using `this.$store.dispatch` or by using `mapActions` in your components.


### Lifecycle 

- **Mounted** called after the component has been mounted to the DOM, which means it is used when you need to perform actions that require the component to be fully rendered and available in the DOM. Initializing data or making API calls; Integrating third-party libraries; Setting up event listeners

***3. Components***
- mixins like traits, store methods, functionality
- Vuex store data

  

