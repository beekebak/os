| Вопрос | Ответ |
|--------|-------|
| Почему именно лимит 32750? | Лимит связан с максимальным количеством областей виртуальной памяти (VMA), которые может использовать процесс. Это число можно проверить через команду: `cat /proc/sys/vm/max_map_count`, где оно равно 65530. При создании потока выделяются минимум две VMA: одна для стека, другая для guard page. |
| Как проверяли количество VMA при создании потоков? | Отключить guard page через `pthread_attr_setguardsize(&attr, 0)` и запустить программу, которая считает количество потоков. Запуск программы с 32749 потоками вывел близкое к лимиту значение VMA. Пример вывода: `cat /proc/pid/maps | wc -l` → 65528. |
| Какой был вывод по количеству VMA для одного потока? | Когда создавался один поток, результат был:  32. Для двух потоков результат:  34. |
| Почему иногда вывод 32749, а часто 32750, где один поток потерялся| Точно есть понимание, что кто то отжирает 1 vma, и поэтому математика не сходится, но пока непонтяно кто |
