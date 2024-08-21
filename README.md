# Вопросы и ответы на собеседования для JS developer'a

***1. Что такое асинхронность***

  Асинхронность в JavaScript (JS) позволяет выполнять операции, не блокируя основной поток выполнения кода. Это означает, что другие части кода могут продолжать выполняться, пока ожидаются результаты выполнения асинхронных операций, таких как запросы к серверу, чтение файлов и таймеры. 
  Сразу после каждой макрозадачи движок исполняет все задачи из очереди микрозадач перед тем, как выполнить следующую макрозадачу или отобразить изменения на странице, или сделать что-то ещё.
  - сначала добавляется в стек вызовов (call stack) и передаётся к WebApi
  - удаляется из call stack
  - после успешного ответа передается в Task queue ()
  - Event Loop проверяет если 

  [Очень полезный сайт](https://learn.javascript.ru/event-loop)

***CoreJS***
- **qs.stringify()** converts a JavaScript object or array into a query string, which is typically used in URL parameters.
- The $ prefix can be a convention for indicating that a function or property is related to the framework or library’s internal workings, not something the user would typically need to modify
  
***2. Vue***
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
- **Vue.use** is used to install a Vue plugin. The plugin is typically an object or a function that provides functionality and is meant to be used across the entire Vue application. A plugin object usually has an install method. This method is called by Vue.use and receives the Vue constructor as an argument. The install method is where the plugin can add functionality to Vue, such as global components, directives, mixins, or prototype methods.

***3. Components***
- mixins like traits, store methods, functionality
- Vuex store data

  

