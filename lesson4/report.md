# Описание кода

## Общее описание

Данный код создает и использует FIFO (First In First Out) для передачи строки между двумя процессами - писателем и читателем.

Однако программа работает не стабильно, иногода поток не передается а остается там же и при перезапуске файл читает то же сообщение, что он и отправил.