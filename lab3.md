|Вопрос|Ответ|
|------|------|
|где хранится аргумент, передаваемый в функцию?|аргумент хранится в локальной переменной функции-обертки, потом передается в пользовательскую функцию при запуске|
|почему данные в куче?|если хранить данные на стеке, то при выходе из функции память деинициализируются, поскольку стеки не разделяются потоками. Тогда функция во втором потоке обратится по деинициализированной памяти|