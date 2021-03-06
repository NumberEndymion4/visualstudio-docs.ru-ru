---
title: 'Как: проверка параметров свойства IIS | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acd232b76ece37737833d071c8551d1319d4f151
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-verify-iis-property-settings"></a>Практическое руководство. Проверка параметров свойства IIS
Можно задать свойства для веб-приложения с помощью средства администрирования IIS. Чтобы приложение выполнялось, эти свойства должны быть заданы правильно. Поэтому проверка этих параметров часто является необходимым шагом в устранении неполадок.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>Проверка параметров IIS для веб-приложения  
  
1.  Откройте **Администрирование** окна: на **запустить** последовательно выберите пункты **программы**и нажмите кнопку **Администрирование**. Если **Администрирование** не отображается в **программы** меню, то следует искать его в **панели управления**.  
  
    -   В Windows 2000, выберите **Диспетчер служб Интернета**.  
  
    -   В Windows XP выберите **Internet Information Services**.  
  
    -   В Windows Server 2003 дважды щелкните **управление сервером**.  
  
         **Управление сервером** открывается окно. В разделе **сервера приложений**, нажмите кнопку **управление этим сервером приложения**.  
  
         **Сервера приложений** открывается окно. Откройте **Диспетчер Internet Information Services (IIS)** на левой панели.  
  
2.  В диалоговом окне выберите дерево элемента управления узлами для своего компьютера. Нажмите кнопку **веб-сайтов** узел и выберите узел веб-приложения. Это может быть узел веб-узла и, таким образом, элементом одного уровня с **веб-сайт по умолчанию** узла или виртуального каталога узла под существующим узлом веб-сайта.  
  
3.  Щелкните правой кнопкой мыши веб-приложение и в контекстном меню щелкните **свойства**.  
  
4.  Проверьте параметры безопасности для веб-приложения:  
  
    1.  В веб-приложении **свойства** окно, нажмите кнопку **Безопасность каталога** и нажмите кнопку **изменить**.  
  
    2.  В **методы проверки подлинности** выберите **разрешить анонимный доступ** и **встроенную проверку подлинности Windows** , если они еще не выбраны.  
  
    3.  Нажмите кнопку **ОК** закрыть **методы проверки подлинности** диалоговое окно.  
  
5.  Для приложения сервера ATL необходимо проверить, связана ли команда DEBUG с расширением ISAPI. Дополнительные сведения см. в разделе [как: связать команда DEBUG с расширением](http://msdn.microsoft.com/en-us/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6.  Для [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] приложения, убедитесь, что виртуальному каталогу для приложения задано имя приложения в **Диспетчер Internet Information Services (IIS)**, **Диспетчер служб Интернета** или  **Службы IIS**.  
  
    1.  В веб-приложении **свойства** выберите **каталога** вкладку, если приложение находится в виртуальном каталоге, или **домашний каталог** вкладку, если приложение находится в веб-сайт.  
  
    2.  Убедитесь, что имя в **локальный путь** соответствует имени каталога, в котором приложение было развернуто.  
  
    3.  В разделе **параметры приложения**, введите имя корневого каталога, содержащего приложение.  
  
    4.  Нажмите кнопку **ОК** закрыть **свойства** диалоговое окно.  
  
7.  Для [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] приложение, нажмите кнопку **ASP.NET** и убедитесь, что правильная версия [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] указано.  
  
8.  Нажмите кнопку **ОК** закрыть **свойства** диалоговое окно.  
  
9. Нажмите кнопку **ОК** закрыть **Диспетчер Internet Information Services (IIS)**, **Диспетчер служб Интернета**, или **Internet Information Services**диалоговое окно.  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок](../debugger/debugging-web-applications-troubleshooting.md)