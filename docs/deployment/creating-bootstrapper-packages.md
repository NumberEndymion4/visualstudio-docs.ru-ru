---
title: Создание пакетов загрузчика
ms.custom: ''
ms.date: 05/02/2018
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 234f89f2d0a28c0836ee06df4c49c3ab60f102ce
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="create-bootstrapper-packages"></a>Создание пакетов загрузчика
Программа установки — это общий установщик, который можно настроить на обнаружение и установку распространяемых компонентов, таких как файлы установщика Windows (.MSI) и исполняемые программы. Установщик также называется начальным загрузчиком. Он программируется с помощью набора XML манифестов, определяющих метаданные для управления установкой компонента.  Каждый распространяемый компонент или необходимых компонентов, который отображается на **необходимые компоненты** используется диалоговое окно для ClickOnce пакета начального загрузчика. Пакет начальной загрузки — это группа директорий и файлов, в которых содержатся файлы манифеста, описывающие порядок установки необходимого компонента. 
  
Сначала начальный загрузчик проверяет, установлены ли необходимые компоненты. Если нет, то начальный загрузчик показывает лицензионные соглашения. Как только конечный пользователь примет условия лицензионного соглашения, начнется установка необходимых компонентов. Если все необходимые компоненты обнаружены, начальный загрузчик просто запустит установщик приложения.  
  
## <a name="create-custom-bootstrapper-packages"></a>Создать пакеты пользовательского загрузчика  
Для создания манифестов начального загрузчика с помощью редактора XML в Visual Studio. Пример создания пакета загрузчика см. в разделе [Пошаговое руководство: Создание пользовательского загрузчика с предупреждением о конфиденциальности](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
Чтобы создать пакет начального загрузчика, можно создать манифест продукта, для каждого локализации и версия компонента, а также манифест пакета.
  
* Манифест продукта *product.xml*, содержит все метаданные не зависящий от языка, для пакета. Здесь находятся общие метаданные для всех локализованных версий распространяемого компонента.  Чтобы создать этот файл, в разделе [как: создание манифеста продукта](../deployment/how-to-create-a-product-manifest.md).
  
* Манифест пакета, *package.xml*, содержит метаданные для конкретного языка; обычно они содержат локализованные сообщения об ошибках. Компонент должен содержать хотя бы один манифест пакета для каждой локализованной версии. Чтобы создать этот файл, в разделе [как: создание манифеста пакета](../deployment/how-to-create-a-package-manifest.md).
  
После создания этих файлов необходимо сохранить манифест продукта в папку с именем стандартного начального загрузчика. Файл манифеста пакета следует переместить в папку с именем языкового стандарта. Например, если манифест пакета создан для распространения на английском языке, то файл необходимо положить в папку с названием "en". Повторите эту процедуру для каждого языкового стандарта, например "ja" для японского языка и "de" для немецкого. Окончательный пользовательский пакет начального загрузчика может иметь следующую структуру папок.  

    ```
    CustomBootstrapperPackage
      product.xml
      CustomBootstrapper.msi
      de
        eula.rtf
        package.xml
      en
        eula.rtf
        package.xml
      ja
        eula.rtf
        package.xml
    ```
  
Затем скопируйте распространяемые файлы в папку начального загрузчика. Для получения дополнительной информации см. [How to: Create a Localized Bootstrapper Package](../deployment/how-to-create-a-localized-bootstrapper-package.md).
 
    *\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
    
или  
    
    *\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
  
Определить расположение папки начального загрузчика можно по значению **Путь** в следующем разделе реестра:  
  
    *HKLM\Software\Microsoft\GenericBootstrapper\11.0*
  
В 64-разрядных системах используйте следующий раздел реестра:  
  
    *HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0*
  
Каждый распространяемый компонент создается в своей подпапке в каталоге пакетов. Продукт манифеста и распространяемые файлы должны быть помещены в эту папку. Локализованные версии манифестов компонента и пакета могут быть помещены в подпапки в соответствии с именем языка и региональных параметров.  
  
После копирования этих файлов в папку начального загрузчика, пакет начального загрузчика автоматически появится в Visual Studio **необходимые компоненты** диалоговое окно. Если пакет пользовательского загрузчика не появился, закройте и снова откройте **необходимые компоненты** диалоговое окно. Дополнительные сведения см. в разделе [Prerequisites Dialog Box](../ide/reference/prerequisites-dialog-box.md).  
  
В следующей таблице перечислены свойства, которые заполняются начальным загрузчиком автоматически.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|ApplicationName|Имя приложения.|  
|ProcessorArchitecture|Процессор и количество бит на слово в платформе, для которой предназначен исполняемый файл. В эти значения входят:<br /><br /> -Intel<br />-IA64<br />— AMD64|  
|[Version9x](https://msdn.microsoft.com/en-us/library/aa372490\(v=vs.140\).aspx)|Номер версии для операционных систем Microsoft Windows 95, Windows 98 и Windows ME. Синтаксис версии — Major.Minor.ServicePack.|  
|[VersionNT](https://msdn.microsoft.com/en-us/library/aa372495\(v=vs.140\).xaspx)|Номер версии для операционных систем Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 и Windows 7. Синтаксис версии — Major.Minor.ServicePack.|  
|[VersionMSI](https://msdn.microsoft.com/en-us/library/aa372493\(v=vs.140\).aspx)|Версия сборки установщика Windows (msi.dll), который запускается во время установки.|  
|[AdminUser](https://msdn.microsoft.com/en-us/library/aa367545\(v=vs.140\).aspx)|Данное свойство устанавливается, если пользователь имеет права администратора. Значения — true или false.|  
|InstallMode|Режим установки показывает, откуда должен быть установлен компонент. В эти значения входят:<br /><br /> -HomeSite: необходимые компоненты установлены с веб-сайта поставщика.<br />-SpecificSite: необходимые компоненты установлены из выбранного расположения.<br />-SameSite: необходимые компоненты установлены в том же расположении, что и приложение.|  
  
## <a name="separating-redistributables-from-application-installations"></a>Отделение распространяемых компонентов от установок приложения  
Размещение распространяемых файлов в проектах установки можно предотвратить. Для этого необходимо создать список распространяемых компонентов в папке RedistList каталога .NET Framework:  
  
`%ProgramFiles%\Microsoft.NET\RedistList`  
  
Список распространяемых компонентов — это XML-файл, которому необходимо присвоить имя в следующем формате: *Название компании*.*Название компонента*.RedistList.xml. Таким образом, например, если компонент называется Datawidgets и разработан компанией Acme, используйте *Acme.DataWidgets.RedistList.xml*. Пример содержания списка распространяемых компонентов:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Установка необходимых компонентов для приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Диалоговое окно «необходимые условия»](../ide/reference/prerequisites-dialog-box.md)   
 [Продукт и справочник по схемам пакета](../deployment/product-and-package-schema-reference.md)   
 [Используйте загрузчик Visual Studio 2005 для запуска установки](http://go.microsoft.com/fwlink/?LinkId=107537)