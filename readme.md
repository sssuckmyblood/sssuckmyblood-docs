### Инструкция по установке программ для подключения к впн для всех платформ

**Шаг 1:** Получить профиль для подключения к серверу

**При установке NekoRay на ПК рекомендуется выбирать ядро sing-box как более стабильное. Но это опционально и тут можно эксперементировать с тем что работает лучше. Инструкция по настройки клиента для обоих ядер представлена ниже. Так же можно поменять текущее ядро и выполить настройки маршрутов и режима TUN для желаемого ядра NekoRay, инструкция для соответсвующих ядер внутри пунктов Установка NekoRay на ПК (Windows) Ядро - sing-box \ Установка NekoRay на ПК (Windows) Ядро - xray**

Список текущих работающих ВПН серверов:
- Helsinki - Finland - Aeza Network Канал связи до 1 Гбит\с
- Frankfurt am Main - Germany - Digital Ocean Канал связи до 2 Гбит\с

<details>
  <summary>Установка NekoRay на ПК (Windows) Ядро - sing-box </summary>

  ## Установка программы и подключение к серверу
  - Скачать программу с оффициального репозитория https://github.com/MatsuriDayo/nekoray/releases/download/3.26/nekoray-3.26-2023-12-09-windows64.zip
  - Распаковать загруженный .zip файл в удобное место на вашем компьютере
  - Открыть распакованную папку и запустить файл nekoray.exe, при запуске выбрать ядро sing-box
  - Если при запуске выдает ошибку DLL скачать и установить vc_redist https://aka.ms/vs/17/release/vc_redist.x64.exe


  - После запуска nekoray.exe, скопировать профиль VLESS который я скинул, нажать Программа и добавить профиль из буфера обмена
   <p align="center">
  <img src="https://github.com/user-attachments/assets/2691ab29-dcf1-4ab3-9dd9-cb0a0b7c9b93" alt="Описание изображения" style="margin: 20px;"/>
 </p>
    
  - Далее правой кнопкой мыши по появившейся строке профиля и нажать Запустить, слева от строки профиля должна появиться галочка - профиль активен
   
    <p align="center">
    <img src="https://github.com/user-attachments/assets/16d032a5-9b0b-4248-8907-16f7ab350725" alt="Описание изображения" style="margin: 20px;"/>
    </p>

- **Перед включением TUN режима, необходимо удалить с компьютера различные Radmin VPN, Hamachi, OpenVPN или выключить их туннельные интерфейсы в настройках сети Windows. Эти программы создают свои туннельные интерфейсы и могут мешать работе туннельного интерфейса NekoRay. NekoRay так же крайне плохо и не стабильно работает если установлен антивирус**

  - После этого выбрать режим TUN или режим системного прокси. Одно из двух, вместе они работать не будут. Сначала выбираем режим TUN, проверяем работает ли интернет и другие заблокированные сервисы. **Если что-то не работает, не загружается, попробуйте сначала выключить впн и перезагрузить ПК, тунельный интерфейс иногда багает.** Если ничего не работает - пробуем режим системного прокси. Если и так ничего не работает - пишем мне.
   
    <p align="center">
    <img src="https://github.com/user-attachments/assets/717211b3-3ea6-445b-85a0-f3479894ed00" alt="Описание изображения" style="margin: 20px;"/>
    </p>
    
   ## Настройка маршрутизации

   - Сверху в программе нажимаем Настройки, выбираем строку Настройки маршрутов
     <p align="center">
     <img src="https://github.com/user-attachments/assets/2d630915-a0af-46a4-a13e-7241af2c6254" alt="Описание изображения" style="margin: 20px;"/>
     </p>
     
   - Далее следуем шагам на скрине. Outboud по-умолчанию должен быть bypass.
     
      <p align="center">
     <img src="https://github.com/user-attachments/assets/a352da1a-7cf6-46dc-b2f0-617fee74bbf1" alt="Описание изображения" style="margin: 20px;"/>
     </p>

   - В редакторе JSON слева удаляем весь текст и вставляем туда правила маршрутизации (ссылка на файл с набором маршрутов ниже, его нужно открыть и скопировать весь текст оттуда)
       <p align="center">
       <img src="https://github.com/user-attachments/assets/9987ef4d-557f-4fb0-8628-564569023377" alt="Описание изображения" style="margin: 20px;"/>
      </p>
      <p align="center">
     <img src="https://github.com/user-attachments/assets/ca69450a-25b9-49cf-860c-26d05bd3da13" alt="Описание изображения" style="margin: 20px;"/>
      </p>
      
     - Ссылка на правила маршрутизации: [Правила маршрутизации](https://raw.githubusercontent.com/sssuckmyblood/sssuckmyblood-vpn-docs/refs/heads/main/routes-sign-box.json)
           
     - ДАЛЕЕ нужно настроить режим TUN только на определенные приложения  (Если вам сложно и с этого пункта вы НИЧЕГО не понимаете, напишите мне, разберемся). В программе нажимаем Настройки, выбираем строку Настройки TUN-режима. Убедитесь что включена опция "Встроенный TUN*".
Включите "Режим белого списка". Укажите, какие процессы необходимо проксировать. Например, чтобы проксировать только Discord, добавьте в список __Discord.exe__ и __Updater.exe__, затем нажмите "OK". Список процессов, которые будет проксироваться, чувствителен к регистру.
После выполнения этих действий Nekoray будет проксировать только Discord, а все остальные соединения будут проходить без VPN. Это особенно важно для онлайн-игр. Для проксирования браузеров используйте следующие имена процессов, это позволит открывать Дискорд, Ютуб, Инстаграмм, Твиттер, ЧатГПТ в браузере:

Google Chrome: chrome.exe

Yandex Browser: browser.exe

Mozilla Firefox: firefox.exe

Microsoft Edge: msedge.exe

Opera Browser: opera.exe

Safari (Windows): safari.exe

Brave Browser: brave.exe

Spotify: Spotify.exe

   <p align="center">
     <img src="https://github.com/user-attachments/assets/1dd1158e-fd24-4451-bd34-31a5fa3ca41d" alt="Описание изображения" style="margin: 20px;"/>
  </p>

   <p align="center">
     <img src="https://github.com/user-attachments/assets/f059502b-c8f7-4112-9a33-8fed17c551f6" alt="Описание изображения" style="margin: 20px;"/>
  </p>
  


  

</details>
<details>
  <summary>Установка NekoRay на ПК (Windows) Ядро - xray </summary>

  ## Установка программы и подключение к серверу
  - Скачать программу с оффициального репозитория https://github.com/MatsuriDayo/nekoray/releases/download/3.26/nekoray-3.26-2023-12-09-windows64.zip
  - Распаковать загруженный .zip файл в удобное место на вашем компьютере
  - Открыть распакованную папку и запустить файл nekoray.exe, при запуске выбрать ядро xray
  - Если при запуске выдает ошибку DLL скачать и установить vc_redist https://aka.ms/vs/17/release/vc_redist.x64.exe


  - После запуска nekoray.exe, скопировать профиль VLESS который я скинул, нажать Программа и добавить профиль из буфера обмена
   <p align="center">
  <img src="https://github.com/user-attachments/assets/2691ab29-dcf1-4ab3-9dd9-cb0a0b7c9b93" alt="Описание изображения" style="margin: 20px;"/>
 </p>
    
  - Далее правой кнопкой мыши по появившейся строке профиля и нажать Запустить, слева от строки профиля должна появиться галочка - профиль активен
   
    <p align="center">
    <img src="https://github.com/user-attachments/assets/16d032a5-9b0b-4248-8907-16f7ab350725" alt="Описание изображения" style="margin: 20px;"/>
    </p>

- **Перед включением TUN режима, необходимо удалить с компьютера различные Radmin VPN, Hamachi, OpenVPN или выключить их туннельные интерфейсы в настройках сети Windows. Эти программы создают свои туннельные интерфейсы и могут мешать работе туннельного интерфейса NekoRay. NekoRay так же крайне плохо и не стабильно работает на Windows 10, особенно на старых сборках (на более новых вроде терпимо).**

  - После этого выбрать режим TUN или режим системного прокси. Одно из двух, вместе они работать не будут. Сначала выбираем режим TUN, проверяем работает ли интернет и другие заблокированные сервисы. **Если что-то не работает, не загружается, попробуйте сначала выключить впн и перезагрузить ПК, тунельный интерфейс иногда багает.** Если ничего не работает - пробуем режим системного прокси. Если и так ничего не работает - пишем мне.
   
    <p align="center">
    <img src="https://github.com/user-attachments/assets/717211b3-3ea6-445b-85a0-f3479894ed00" alt="Описание изображения" style="margin: 20px;"/>
    </p>
    
   ## Настройка маршрутизации

   - Сверху в программе нажимаем Настройки, выбираем строку Настройки маршрутов
     <p align="center">
     <img src="https://github.com/user-attachments/assets/2d630915-a0af-46a4-a13e-7241af2c6254" alt="Описание изображения" style="margin: 20px;"/>
     </p>
     
   - Далее следуем шагам на скрине. Outboud по-умолчанию должен быть bypass.
     
      <p align="center">
     <img src="https://github.com/user-attachments/assets/a352da1a-7cf6-46dc-b2f0-617fee74bbf1" alt="Описание изображения" style="margin: 20px;"/>
     </p>

   - В редакторе JSON слева удаляем весь текст и вставляем туда правила маршрутизации (ссылка на файл с набором маршрутов ниже, его нужно открыть и скопировать весь текст оттуда)
       <p align="center">
       <img src="https://github.com/user-attachments/assets/9987ef4d-557f-4fb0-8628-564569023377" alt="Описание изображения" style="margin: 20px;"/>
      </p>
      <p align="center">
     <img src="https://github.com/user-attachments/assets/ca69450a-25b9-49cf-860c-26d05bd3da13" alt="Описание изображения" style="margin: 20px;"/>
      </p>
      
     - Ссылка на правила маршрутизации: [Правила маршрутизации](https://raw.githubusercontent.com/sssuckmyblood/sssuckmyblood-vpn-docs/refs/heads/main/routes.json)
           
     - ДАЛЕЕ нужно настроить режим TUN только на определенные приложения (Если вам сложно и с этого пункта вы НИЧЕГО не понимаете, напишите мне, разберемся). В программе нажимаем Настройки, выбираем строку Настройки TUN-режима. 
Включите "Режим белого списка". Укажите, какие процессы необходимо проксировать. Например, чтобы проксировать только Discord, добавьте в список __Discord.exe__ и __Updater.exe__, затем нажмите "OK". Список процессов, которые будет проксироваться, чувствителен к регистру.
После выполнения этих действий Nekoray будет проксировать только Discord, а все остальные соединения будут проходить без VPN. Это особенно важно для онлайн-игр. Для проксирования браузеров используйте следующие имена процессов, это позволит открывать Дискорд, Ютуб, Инстаграмм, Твиттер, ЧатГПТ в браузере:

Google Chrome: chrome.exe

Yandex Browser: browser.exe

Mozilla Firefox: firefox.exe

Microsoft Edge: msedge.exe

Opera Browser: opera.exe

Safari (Windows): safari.exe

Brave Browser: brave.exe

Spotify: Spotify.exe

   <p align="center">
     <img src="https://github.com/user-attachments/assets/1dd1158e-fd24-4451-bd34-31a5fa3ca41d" alt="Описание изображения" style="margin: 20px;"/>
  </p>

   <p align="center">
     <img src="https://github.com/user-attachments/assets/6de60899-f04d-46b1-9f58-b0ffad3fef4e" alt="Описание изображения" style="margin: 20px;"/>
  </p>
  


  

</details>
<details>
  <summary> Поменять ядро Nekoray </summary>
  
  - Перейти в Основные настройки.
  
  - Открыть раздел Ядро.
  
  - Выбрать ядро sing-box или xray.


   <p align="center">
  <img src="https://github.com/user-attachments/assets/bf056604-bbfa-4c2b-86b7-86fb623454a1" alt="Описание изображения" style="margin: 20px;"/>
 </p>
  <p align="center">
  <img src="https://github.com/user-attachments/assets/355bc9e1-305a-4886-8686-724d43dfcfa9" alt="Описание изображения" style="margin: 20px;"/>
 </p>
    


  

</details>

<details>
  <summary>Установка NekoBox на Android</summary>
  
   ## Установка программы и подключение к серверу
   
  - Скачать программу с оффициального репозитория https://github.com/MatsuriDayo/NekoBoxForAndroid/releases/download/1.3.2/NB4A-1.3.2-arm64-v8a.apk
    
  - Скопировать профиль VLESS который я скинул, запустить программу и следовать скринам
    ![image](https://github.com/user-attachments/assets/d5052197-9cfb-427b-b285-72bdfd64a3dc)
    
  - Для подключения нажать на круг со значком снизу экрана
    ![image](https://github.com/user-attachments/assets/be6fee40-1c07-41eb-8402-7bd168b3b08f)
    
</details>

</details>

<details>
  <summary>Установка FoXray на IOS</summary>
  
   ## Установка программы и подключение к серверу
   
  - Скачать программу из App Store https://apps.apple.com/us/app/foxray/id6448898396
    
  - Скопировать профиль VLESS который я скинул, запустить программу и следовать скринам
    
    ![image](https://github.com/user-attachments/assets/d7454fd7-45b6-4e70-b2cd-0f55ad833a05)
    
  - Разрешить вставку
    
    ![image](https://github.com/user-attachments/assets/9401c89b-14d0-45f6-bd6d-6923453bb05a)

  - И нажать на зачек справа от профиля - он запустится

    
</details>
