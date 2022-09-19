Данный код позволяет запустить виртуальное приложение на локальном компьютере, в котором можно выбрать тип данных и сами файлы, которые необходимо переместить на сервер
## 1. Запуск приложения
Необходимо перейти в папку содержащую скрипт с кодом, а затем активировать его из командной строки:
```
python3 simple.py
# или python, если установлена более старая версия python
```
Если терминал выдает ошибки, связанные с отсутствием некоторых пакетов в питоне, необходимо их загрузить следующими командами (первым делом проверить наличие менеджера питоносвких пакетов pip3 - если установлена версия python 3.0 и выше):
```
sudo apt-get update
sudo apt-get -y install python3-pip
pip3 --version
```
Затем, установить недостающие пакеты (пакеты shutil, os и sys обычно стандартно присутствуют при установке python):
```
pip3 install PyQt6
pip3 install scp
pip3 install os-sys
pip3 install paramiko
pip3 install shutil
pip3 install hashlib
```
## 2. Изменение кода для работы с лабораторных компьютеров:
Так как код писался на локальном компьютере, в него необходимо внести изменения перед тем, как запускать его на лабораторных машинах. Все места, которые необходимо изменить отмечены в коде с помощью:
```
# !!!
# нужно что-то поменять
```
* Примечание: в целях сохранения конфиденциальности credentials для входа на сервер были прописаны в .bashrc файле в корневой папке локального компьютера (затем значения переменных вызываются в основном коде). Однако, при желании можно вписать нужные значения (IP, USER, PASSWORD, PORT) непосрдественно в сам код (line 118)
## 3. Работа в приложении
После запуска приложения из командной строки приложение открывается в следующем виде:<br><br>
![initial](https://github.com/andrewstapran1543/File_Transfer_Server/blob/main/initial.png)<br><br>
Для того, чтобы начать перенос файлов, первым делом необходимо выбрать папку, из которой перенос будет произведен. Это делается нажатием кнопки "Select the folder" - откроется диалоговое окно, с возможностью выбора папки:<br><br>
![browser](https://github.com/andrewstapran1543/File_Transfer_Server/blob/main/browser.png)<br><br>
Выбрав нужную папку, нажимаем "OK" - путь до папки будет отображен вместо надписи "Enter path to folder":<br><br>
![file_path](https://github.com/andrewstapran1543/File_Transfer_Server/blob/main/file_path.png)<br><br>
Затем выбираем нужный тип данных из dropdown листа:
<li>CMA - хромосомный микроматричный анализ</li>
<li>Exomes_GenoLab - экзомное секвенирование (нa GenoLab)</li>
<li>NIPT - неинвазивная пренатальная диагностика</li>
<li>Other_divisions - данные из других отделов</li><br><br>
![my_dropdown](https://github.com/andrewstapran1543/File_Transfer_Server/blob/main/dropdown.png)<br><br>
Наконец, нажимаем на кнопку "Trasfer the files" - появится окошко с предупреждением. Нужно убедиться, что выбран правильный тип данных - если все так, нажимаем кнопку "Yes":<br><br>
![my_warning](https://github.com/andrewstapran1543/File_Transfer_Server/blob/main/warning.png)<br><br>
На экране отобразится название перемещаемого файла, а также начнет заполняться progress bar, показывающий успешность переноса файла. Под названием файла отображается объем уже перенесенной на сервер информации и общий размер файла (в Mb):<br><br>
![my_transfer](https://github.com/andrewstapran1543/File_Transfer_Server/blob/main/transfer.png)<br><br>
Если трансфер файлов успешно завершен - программа выдаст надпись заглавным буквами и жирным шрифтом: "ФАЙЛЫ БЫЛИ УСПЕШНО ПЕРЕМЕЩЕНЫ НА СЕРВЕР". Если содержимое исходного файла на локальном компьютере совпадает с содержимым перенесенного на сервер файла, под первой надписью появится: "HASH-СУММЫ ФАЙЛОВ СОВПАДАЮТ". Наконец, progress bar полностью заполнится, что означает завершение переноса файла с локального компьютера на сервер:<br><br>
![my_checkings](https://github.com/andrewstapran1543/File_Transfer_Server/blob/main/checkings.png)<br><br>
