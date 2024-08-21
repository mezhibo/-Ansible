**Основная часть**

1. Попробуйте запустить playbook на окружении из test.yml, зафиксируйте значение, которое имеет факт some_fact для указанного хоста при выполнении playbook.

2. Найдите файл с переменными (group_vars), в котором задаётся найденное в первом пункте значение, и поменяйте его на all default fact.

3. Воспользуйтесь подготовленным (используется docker) или создайте собственное окружение для проведения дальнейших испытаний.

4. Проведите запуск playbook на окружении из prod.yml. Зафиксируйте полученные значения some_fact для каждого из managed host.

5. Добавьте факты в group_vars каждой из групп хостов так, чтобы для some_fact получились значения: для deb — deb default fact, для el — el default fact.

6. Повторите запуск playbook на окружении prod.yml. Убедитесь, что выдаются корректные значения для всех хостов.

7. При помощи ansible-vault зашифруйте факты в group_vars/deb и group_vars/el с паролем netology.

8. Запустите playbook на окружении prod.yml. При запуске ansible должен запросить у вас пароль. Убедитесь в работоспособности.

9. Посмотрите при помощи ansible-doc список плагинов для подключения. Выберите подходящий для работы на control node.

10. В prod.yml добавьте новую группу хостов с именем local, в ней разместите localhost с необходимым типом подключения.

11. Запустите playbook на окружении prod.yml. При запуске ansible должен запросить у вас пароль. Убедитесь, что факты some_fact для каждого из хостов определены из верных group_vars.

12. Заполните README.md ответами на вопросы. Сделайте git push в ветку master. В ответе отправьте ссылку на ваш открытый репозиторий с изменённым playbook и заполненным README.md.

13. Предоставьте скриншоты результатов запуска команд.



**Решение**

Скачиваем репу и запускаем все по дефолту, и видим что все работает.

![alt text](https://github.com/mezhibo/-Ansible/blob/1d648c7a48582874725cee6fd329975770cfece7/IMG/1.jpg)


В файлах папки group_vars меняем значение сообщения на "all default fact" и запускаем

![alt text](https://github.com/mezhibo/-Ansible/blob/1d648c7a48582874725cee6fd329975770cfece7/IMG/2.jpg)


Ставим докер-контейнеры centos7 и ubuntu и выполняем для них плейбук изменив значение переменнаых на deb default fact для ubuntu и el default fact для centos

![alt text](https://github.com/mezhibo/-Ansible/blob/1d648c7a48582874725cee6fd329975770cfece7/IMG/3.jpg)


Теперь Волтом шифруем наши файлы сообщений для каждого типа ОС


![alt text](https://github.com/mezhibo/-Ansible/blob/1d648c7a48582874725cee6fd329975770cfece7/IMG/4.jpg)


И тперь выполняем плейбук, но уже при шифрованных данных. Вводим пароль заданный ранее, и видим что плейбук отрабатывает даже при шифрованных значениях.

![alt text](https://github.com/mezhibo/-Ansible/blob/1d648c7a48582874725cee6fd329975770cfece7/IMG/5.jpg)


Выведем список доступных плагинов 

![alt text](https://github.com/mezhibo/-Ansible/blob/1d648c7a48582874725cee6fd329975770cfece7/IMG/6.jpg)


И теперь в инфентори файл для нашего окружения пропишем сам наш хост, и выполним плейбук уже на все 3 инстанса


![alt text](https://github.com/mezhibo/-Ansible/blob/1d648c7a48582874725cee6fd329975770cfece7/IMG/7.jpg)


[ССЫЛКА НА ФАЙЛЫ](https://github.com/mezhibo/mnt-homeworks/tree/355a7c64ab9d781fac1937b71725e32e11f5dc7f/08-ansible-01-base/playbook)





