# WPcabLinksLoader_batch
A simple batch script for downloading cab files from multiple links by selecting the txt file containing them from the WP cab links archive, carefully and lovingly assembled by @Empyreal96 at https://github.com/Empyreal96/WPCabLinks.db
Legal notice: _This script is provided "as is", and I am not responsible for its misuse. However, this script is safe and can be safely run by you on your PC. You can safely study its source code._

# **How to use:**
You need to run the script and confirm the launch as an administrator (the request will be sent automatically). Then select the file (recommended .txt without other links, although the script supports the rehabilitation of the content and the correct download of links). Be careful about the file that you choose to download and make sure that its contents are safe.
After the operation is completed, the corresponding created directory with cab files and the download log will open through the explorer. Then you can use the Universal Updater from the author @FadilFadz01 (https://github.com/fadilfadz01/Universal_Updater/releases).

For any problem, write to me in tg @OchkinArtem or create an Issue on github with an indication of the nature of the problem and the log file, and also specify the file version.

**Important!** Valid URIs are supported. Example of a part of an open .txt file (links with whitespace):
`http://download.windowsupdate.com/c/msdownload/update/software/dflt/2016/09/microsoft.base.weh.data.spku_9505f7ebd89aeca5b3f4d86dbecdfca3587dadf1.cab
http://download.windowsupdate.com/c/msdownload/update/software/dflt/2016/09/microsoft.base.weh.mainos.spku_ed303665672edd1f522b95c98c439876e2dc0670.cab
http://download.windowsupdate.com/c/msdownload/update/software/dflt/2016/09/microsoft.base.weh.mainos_lang_af-za.spku_018dc0877038e8b2153bdbd2b48a25af6509f88e.cab
http://download.windowsupdate.com/c/msdownload/update/software/dflt/2016/09/microsoft.base.weh.mainos_lang_ar-sa.spku_69281c4764269b8291180f77f8ab2fe1881f0fd4.cab
http://download.windowsupdate.com/c/msdownload/update/software/dflt/2016/09/microsoft.base.weh.mainos_lang_az-latn-az.spku_45ff10087403d34ea8de8c835e7b10893e0407c1.cab
http://download.windowsupdate.com/c/msdownload/update/software/dflt/2016/09/microsoft.base.weh.mainos_lang_be-by.spku_f1c340318a53a299bb7e59de376a450b697bef78.cab`

_If this does not match your file, it is recommended that you find a compatible file with a set of links._

**System requirements:**
Windows 10 (19045.x) and Windows 11 script, as a rule, works by default (click and run). On my laptop with Win11 26200 and installed .The Net framework works fine, but on older systems you may need to check for availability.Net Framework 4.5 vs Powershell 3.0+. It is recommended to use a version not lower than Windows 8 (the script has been tested on Win10/11 x64, arm64 Windows should also work without problems, as well as x86-32).
Well, obviously, Internet access is required :) to access Windows Update servers.

# **Как использовать:**
Вам требуется запустить скрипт и подтвердить запуск от имени администратора (запрос будет послан автоматически). Затем выберите файл (рекомендуется .txt без иных ссылок, хотя скриптом поддерживается некоторая санация содержимого и корректное скачивание множества ссылок). Будьте внимательны к тому файлу, который вы выбираете для скачивания и убедитесь в безопасности его содержимого.
После завершения операции через проводник откроется соответствующий созданный каталог с cab-файлами и логом скачивания. Затем вы можете использовать Universal Updater от автора @FadilFadz01 (https://github.com/fadilfadz01/Universal_Updater/releases).

По любой проблеме пишите мне в тг @OchkinArtem или создавайте Issue на гитхабе с указанием на характер проблемы  и log-файл, а также прошу указывать версию файла.

Важно! Поддерживаются валидные uri. Пример части из открытого txt-файла:
http://download.windowsupdate.com/c/msdownload/update/software/dflt/2016/09/microsoft.base.weh.data.spku_9505f7ebd89aeca5b3f4d86dbecdfca3587dadf1.cab
http://download.windowsupdate.com/c/msdownload/update/software/dflt/2016/09/microsoft.base.weh.mainos.spku_ed303665672edd1f522b95c98c439876e2dc0670.cab
http://download.windowsupdate.com/c/msdownload/update/software/dflt/2016/09/microsoft.base.weh.mainos_lang_af-za.spku_018dc0877038e8b2153bdbd2b48a25af6509f88e.cab
http://download.windowsupdate.com/c/msdownload/update/software/dflt/2016/09/microsoft.base.weh.mainos_lang_ar-sa.spku_69281c4764269b8291180f77f8ab2fe1881f0fd4.cab
http://download.windowsupdate.com/c/msdownload/update/software/dflt/2016/09/microsoft.base.weh.mainos_lang_az-latn-az.spku_45ff10087403d34ea8de8c835e7b10893e0407c1.cab
http://download.windowsupdate.com/c/msdownload/update/software/dflt/2016/09/microsoft.base.weh.mainos_lang_be-by.spku_f1c340318a53a299bb7e59de376a450b697bef78.cab
_Если это не соответствует вашему файлу, вам рекомендуется найти совместимый файл с набором ссылок, однако вы можете попробовать использовать текущий скрипт и свой файл или внести изменения в скрипт для себя или предложить коммит_

**Системные требования:**
Системные требования:
В Windows 10 (19045.x) и Windows 11 скрипт, как правило, работает по дефолту (нажми и работай). На моём ноутбуке с Win11 26200 и установленным .Net framework всё работает без проблем, однако на более старых системах вам может потребоваться проверить наличие .Net Framework 4.5 vs Powershell 3.0+. Рекомендуется использование версии не ниже Windows 8 (работа скрипта проверена на Win10/11 x64, arm64 Windows также должна работать без проблем, как и x86-32).
Ну и, очевидно, требуется доступ к интернету :) для доступа к серверам Windows Update.

