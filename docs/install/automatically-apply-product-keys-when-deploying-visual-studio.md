---
title: Автоматическое применение ключей продуктов при развертывании Visual Studio
description: Сведения о применении ключей продуктов программными средствами при развертывании Visual Studio.
ms.date: 08/14/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 122fbaa30b90eb7cb5f7cb5de210e86155573833
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Автоматическое применение ключей продуктов при развертывании Visual Studio

Ключ продукта можно применить программным способом в составе сценария, используемого для автоматизации развертывания Visual Studio. Ключи продуктов могут быть заданы на устройстве программно во время установки Visual Studio или после ее завершения.

## <a name="apply-the-license-after-installation"></a>Применение лицензии после установки

 Чтобы активировать установленную версию Visual Studio с помощью ключа продукта, выполните на конечных компьютерах служебную программу `StorePID.exe` в автоматическом режиме. `StorePID.exe` — это служебная программа, которая устанавливается вместе с Visual Studio 2017 в следующем расположении по умолчанию: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 Запустите `StorePID.exe` с повышенными привилегиями, используя агент System Center или командную строку с повышенными привилегиями. Введите ключ продукта и код продукта Майкрософт (MPC).

>[!IMPORTANT]
> В ключе продукта необходимо указывать дефисы.

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

 В следующем примере показано использование командной строки для применения лицензии к Visual Studio 2017 Enterprise, для которой MPC имеет значение 08860, с помощью ключа продукта `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, при условии, что установка выполнена в расположение по умолчанию:

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 В следующей таблице перечислены коды MPC для каждого выпуска Visual Studio:

| Visual Studio 2013                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

Если `StorePID.exe` успешно применен к ключу продукта, для параметра `%ERRORLEVEL%` возвращается значение 0. При обнаружении ошибок возвращается один из следующих кодов в зависимости от состояния ошибки:

| Error                     | Код |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="get-support"></a>Техническая поддержка

Иногда возникают проблемы. При сбое установки Visual Studio см. инструкции по [устранению неполадок и исправлению ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Если описанные выше действия не устраняют проблему, вы можете обратиться к нам за помощью в чате в реальном времени (только на английском языке). Дополнительные сведения см. на [странице поддержки Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ниже приведены несколько дополнительных вариантов:

* Вы можете сообщить о проблемах с продуктом в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Оно доступно как в Visual Studio Installer, так и в Visual Studio IDE.
* Вы можете оставить предложение о продукте на форуме [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Вы можете просматривать описания проблем и искать решения в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/).
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio). (Требуется учетная запись [GitHub](https://github.com/).)

## <a name="see-also"></a>См. также

* [Установка Visual Studio](../install/install-visual-studio.md)
* [Создание автономной установки Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
