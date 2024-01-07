<br>
<H2>Задание B6.9.2</H2><br>

1. Создайте Ansible-роль, настраивающую кэширующий DNS-сервер dnsmasq. Примените ее. <br>
   Ответ: Была создана и настроена удалённом сервере  роль: <b>dnsmasq </b><br>
   Результат: Сервер был полность развёрнут и настроен при помощи Ansible <br>
<b>odmin@devops1:~$ ps aux | grep dnsmasq <br>
dnsmasq      708  0.0  0.2  12308  2620 ?        S    13:38   0:00 /usr/sbin/dnsmasq -x /run/dnsmasq/dnsmasq.pid -u <br>
dnsmasq -7 /etc/dnsmasq.d,.dpkg-dist,.dpkg-old,.dpkg-new --local-service <br>
--trust-anchor=.,20326,8,2,e06d44b80b8f1d39a95c0b0d7c65d08458e880409bbc683457104237c7f8ec8d <br></b>
       <br>
2. Напишите Ansible-playbook, создающий группу пользователей superusers, куда входят пользователи user2 и user3, и которая, выполнив sudo -i, <br> 
сможет повысить свои полномочия и стать root-пользователем.Можете использовать модуль lineinfile. У него есть параметр validate, позволяющий <br>
проверять сделанные изменения в файле. В документации есть пример валидации sudoers-файла.<br>
   Ответ: Был создан playbook <b>useradd.yml </b> который создаёт 2 новых пользователей <b>User2, User3</b> и гуппу <b>superysers</b> на удалённом сервере, 
   помещает пользователей в новую группу и добавляет их в <b>sudoer</b><br>
   Результат: Playbook успешно отработал <br>
<br><b>
root@localhost B6.9.2]# ssh -i /root/.ssh/user2 user2@192.168.200.110 <br>
Enter passphrase for key '/root/.ssh/user2':      <br>
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 5.4.0-135-generic x86_64)<br><br>

  Memory usage: 23%                IPv4 address for enp0s3: 192.168.200.110 <br>
<br>
Last login: Wed Dec  7 09:58:34 2022 from 192.168.1.111 <br>
user2@devops1:~$ sudo -i  <br>
root@devops1:~#  <br> </B>
<br>
3. Самостоятельно напишите Ansible-роль, настраивающую связку nginx+php-fpm и выдающую при обращении к главной странице веб-сервера информацию о php <br>
(содержимое index.php — <?php phpinfo();?>).<br>
Ответ: Была создана роль nginx+php-fpm. Были созданы настройки сайта для nginx и работы php-fpm. <br>
Результат: Playbook успешно отработал: <br>
   Страница index.php с кодом <?php phpinfo();?> успешно отрабатывает. <br>
   Результат можно увидеть на скриншоте: <b>phpifo.JPG </b> <br><br>


<br>
4.Дополните роль из п.3: пусть DocumentRoot будет в директории /opt/nginx/ansible. Используйте handler для перечитывания конфигурации nginx. <br>
Ответ: Был изменён модуль конфигурации и путь к сайту на <b>/opt/nginx/ansible</b> также был добавлен <b>handler </b><br> который вызывался для рестарта nginx сервера.
