# proxychains
Настройка прокси в Linux. Proxechains-ng


sudo yum install git gcc
sudo yum remove proxychains
git clone https://github.com/rofl0r/proxychains-ng.git
cd proxychains-ng/
./configure --prefix=/usr --sysconfdir=/etc

make
sudo make install
sudo make install-config

После установки ProxyChains-ng осталось отредактировать файл настройка прокси-цепочек: /etc/proxychains.conf. Открываем его текстовым редактором:
vim /etc/proxychains.conf

По умолчанию здесь прописано использование сети Tor, поэтому эту строку мы просто закоментируем (#/etc/proxychains.conf). Теперь нам нужен прокси-сервер. Что бы было как в фильме, я нашёл на https://premproxy.com Эстонский прокси, но пока я это писал он перестал работать (наглядный пример всех прелестей бесплатного прокси). Но, в связи с тем, что это, принципиально ни на что не влияет, мы возьмём рабочий прокси и используем его.

Если твоя цель анонимность, не используй transparent proxy — это прозрачный прокси, он не скрывает ip.

В конец файла proxychains.conf, там где ProxyLixt, дописываем:
http    31.209.96.50    57482

Сохраняем изменения. Теперь чтобы направить трафик любой утилиты или приложения через прокси, достаточно перед командой запуска добавить proxychains4. Например, если мы хотим проверить под каким ip мы обращаемся к сайтам (это будет ip прокси-сервера), нужно написать в терминале:
proxychains4 wget -qO- eth0.me

Точно также мы можем, например, запустить браузер Firefox через прокси:

proxychains4 firefox





