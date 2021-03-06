---
title: Создание среды разработки Node.js с контейнерами с помощью Kubernetes в облаке — шаг 3 — создание веб-приложения ASP.NET | Документы Майкрософт
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Быстрая разработка Kubernetes с контейнерами и микрослужбами в Azure
keywords: Docker, Kubernetes, Azure, AKS, служба контейнеров Azure, контейнеры
manager: douge
ms.openlocfilehash: 34e1f07e173ccba6aab561fb4795abbe938e0127
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Начало работы в подключенной среде с Node.js

Предыдущий шаг: [создание среды разработки Kubernetes в Azure](get-started-nodejs-02.md)

## <a name="create-a-nodejs-web-app"></a>Создание веб-приложения Node.Js
Загрузите код из GitHub, перейдя к https://github.com/Azure/vsce, и выберите **Клонировать или загрузить**, чтобы загрузить репозиторий GitHub в локальную среду. Код для этого руководства находится в `vsce/samples/nodejs/getting-started/webfrontend`.

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>Обновите файл содержимого
Подключенная среда связана не только с получением кода, выполняемого в Kubernetes. Это возможность быстро и последовательно отслеживать, как изменения кода вступают в силу в среде Kubernetes в облаке.

1. Найдите файл `./public/index.html` и внесите изменения в HTML. Например, можно изменить цвет фона страницы на оттенок синего:

```html
<body style="background-color: #95B9C7; margin-left:10px; margin-right:10px;">
```

2. Сохраните файл. Почти сразу в окне терминала вы увидите сообщение о том, что файл в выполняемом контейнере был изменен.
1. Перейдите в браузер и обновите страницу. Цвет изменится.

Что произошло? Изменения, вносимые в файлы содержимого, например HTML и CSS, не требуют перезапуска процесса Node.js, поэтому активная команда `vsce up` автоматически синхронизирует все измененные файлы содержимого непосредственно в выполняемом контейнере в Azure, тем самым обеспечивая возможность быстрого просмотра изменений.

### <a name="test-from-a-mobile-device"></a>Тест на мобильном устройстве
При открытии веб-приложения на мобильном устройстве вы заметите, что пользовательский интерфейс некорректно отображается на маленьком экране.

Чтобы устранить эту проблему, мы добавим метатег `viewport`:
1. Откройте файл `./public/index.html`
1. Добавьте метатег `viewport` в существующий элемент `head`:

```html
<head>
    <!-- Add this line -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
```

1. Сохраните файл.
1. Обновите браузер на устройстве. Теперь веб-приложение будет отображаться корректно. 

Это пример того, что некоторые проблемы невозможно обнаружить до тестирования на устройствах, где будет использоваться приложение. С помощью подключенных сред VS вы можете быстро выполнять итерацию кода и проверять изменения на целевых устройствах.

## <a name="update-a-code-file"></a>Обновление файла кода
Обновление файлов кода на стороне сервера требует чуть больше усилий, поскольку необходимо перезапустить приложение Node.js.

1. В окне терминала введите `Ctrl+C` (чтобы остановить `vsce up`).
1. Откройте файл кода с именем `server.js` и измените приветственное сообщение службы: 

```javascript
res.send('Hello from webfrontend running in Azure!');
```

3. Сохраните файл.
1. Запустите `vsce up` в окне терминала. 

Образ контейнера будет перестроен, а диаграмма Helm будет повторно развернута. Перезагрузите страницу браузера, чтобы увидеть изменения кода.


Но существует еще более *быстрый метод* создания кода, который мы обсудим в следующем разделе. 
> [!div class="nextstepaction"]
> [Отладка контейнера в Kubernetes](get-started-nodejs-04.md)
