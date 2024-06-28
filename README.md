# Вопросы и ответы на собеседования для JS developer'a

***1. Что такое асинхронность***

  Асинхронность в JavaScript (JS) позволяет выполнять операции, не блокируя основной поток выполнения кода. Это означает, что другие части кода могут продолжать выполняться, пока ожидаются результаты выполнения асинхронных операций, таких как запросы к серверу, чтение файлов и таймеры. 
  Сразу после каждой макрозадачи движок исполняет все задачи из очереди микрозадач перед тем, как выполнить следующую макрозадачу или отобразить изменения на странице, или сделать что-то ещё.
  - сначала добавляется в стек вызовов (call stack) и передаётся к WebApi
  - удаляется из call stack
  - после успешного ответа передается в Task queue ()
  - Event Loop проверяет если 

  [Очень полезный сайт](https://learn.javascript.ru/event-loop)
