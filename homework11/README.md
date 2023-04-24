# Взаимодействие TCP клиентов через сервер

## Задание

Разработать клиент-серверное приложение, использующее TCP/IP и реализующее следующие взаимодействия: клиент №1 передает сообщения серверу, который перенаправляет их клиенту №2. В качестве исходных данных задавать: IP-адрес
 сервера, порт сервера. Эти данные можно задавать либо в командной
строке, либо с использованием функций стандартного ввода.

Передаваемое сообщение задается из стандартного ввода в цикле. То есть, можно передать не одно а несколько сообщений от клиента №1 клиенту №2. При передаче сообщения "The End" необходимо завершить работу как клиентов, так и сервера.

Приложение
 должно функционировать в конфигурациях от одного до трех компьютеров с
различными комбинациями размещения клиентов и сервера.

## Решение

Для решения были написаны программы [server](./server.c) сервер обработчик. Он инициализирует введенный порт, а затем ждет два подключения от клиентов. После подключения сервер читает сообщение от подключившегося клиента и принимает его тип (`sender` или `receiver`). Далее сервер принимает сообщения от *sender* и перенаправляет из в *receiver*. При получении сообщения `The End` сервер завершает работу.

Программа [sender](./sender.c) отправитель. Она запрашивает у пользователя ввод IP адреса сервера и порта. После подключения к серверу, программа запрашивает у пользователя ввод сообщения для отправки. После отправки сообщения, программа снова запрашивает сообщение для отправки. При получении сообщения `The End` программа завершает работу.

Программа [receiver](./receiver.c) получатель. Она запрашивает у пользователя ввод IP адреса сервера и порта. После подключения к серверу, программа ожидает получения сообщения от сервера. При получении сообщения `The End` программа завершает работу.