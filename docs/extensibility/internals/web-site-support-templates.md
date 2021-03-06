---
title: Шаблоны веб-сайта поддержки | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af8e0d845157b475e4a5527443f55286828023cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="web-site-support-templates"></a>Шаблоны веб-сайта поддержки
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Шаблоны проектов и элементов веб-сайтов предоставляют многократно используемых и настраиваемый веб-узел проектов и элементов, позволяющую ускорить процесс разработки устраняется необходимость для создания новых проектов веб-сайта и элементов с нуля. Дополнительные сведения о [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] шаблонов, см. раздел [Создание проекта и шаблонов элементов](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Папка шаблона проекта
 Шаблоны веб-проектов обычно устанавливаются на [*путь установки Visual Studio*] \Common7\IDE\ProjectTemplates\Web\\, каждый во вложенную папку с названием языка программирования веб-сайте.

## <a name="project-file"></a>Файл проекта
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки (IDE) требуется расширение файла проекта в качестве способа сопоставления шаблона к типу нужный проект. Поскольку веб-проектов не содержит файл проекта, с расширением WEBPROJ расширение файла для пустой проект регистрируется сопоставить шаблон типа проекта.

 При необходимости можно добавить строку имени языка с шаблоном, чтобы включить веб-проекта системы задать язык по умолчанию в **Добавление нового элемента** диалоговое окно для элементов на основе шаблона. Строка должна быть первой строки файла. Имя должно соответствовать имя, зарегистрированное в группе AddItemLanguageName при регистрации обработчика IntelliSense и имя, зарегистрированное в группе Subtype(VsTemplate) проекта. Дополнительные сведения см. в разделе [веб-сайта поддержки атрибуты](../../extensibility/internals/web-site-support-attributes.md).

 Если строка не существует, веб-проекта системы пытается определить язык по умолчанию, в зависимости от расширения атрибута и файл языка страниц, добавлены в веб-проект с помощью шаблона проекта.

## <a name="project-templates"></a>Шаблоны проектов
 Шаблоны проектов веб-сайта используются для создания нового веб-сайтов в ответ на **новый веб-сайт** на **файл** меню. В настоящее время поддерживаются три типа проектов веб-сайта:

-   Пустой веб-сайтов

-   Проекты веб-сайтов

-   Проекты веб-службы

### <a name="empty-web-site-projects"></a>Пустой веб-сайтов
 Эти файлы создать новый пустой веб-сайт в ответ на **пустой веб-сайт** команду, которая доступна после выбора **файл** > **новый веб-сайт**:

-   EmptyWeb.vstemplate

     Файл шаблона, который служит для создания новой пустой веб-сайт.

-   EmptyWeb.webproj

     Этот файл является артефактом система шаблона проекта. Он соответствует ссылки файла проекта в файле EmptyWeb.vstemplate.

### <a name="web-site-projects"></a>Проекты веб-сайтов
 Эти файлы создать новый веб-сайт в ответ на **веб-сайт ASP.NET** команду, которая доступна после выбора **файл** > **новый веб-сайт**:

-   Default.aspx

     Домашняя страница по умолчанию для нового веб-сайта. Атрибут Language задает язык фонового кода и атрибута CodeFile указывает зависимый файл, содержащий код фонового кода, связанный с этой страницей.

-   Default.aspx. *расширения*

     Зависимый файл, содержащий код codebehind на домашнюю страницу по умолчанию. Определяет язык codebehind *расширения* этого файла.

-   web.config.

     Корневой файл конфигурации web.site.

-   WebApplication.vstemplate

     Файл шаблона, который определяет содержимое решение веб-узла и вызывает принудительное создание папки App_Data.

-   WebApplication.webproj

     Этот файл является артефактом система шаблона проекта. Он соответствует ссылки файла проекта в файле WebApplication.vstemplate.

### <a name="web-service-projects"></a>Проекты веб-службы
 Эти файлы создать новый веб-сайт в ответ на **веб-службы ASP.NET** команду, которая доступна после выбора **файл** > **новый веб-сайт**:

-   Service.asmx

     HTML-страницу для веб-службу. Атрибут Language задает язык фонового кода и атрибут CodeBehind указывает зависимый файл, содержащий код фонового кода, связанный с этой службой.

-   Служба. *Расширение*

     Зависимый файл, который реализует класс службы. Определяет язык codebehind *расширения* этого файла.

-   web.config.

-   Корневой файл конфигурации web.site.

-   WebService.vstemplate

     Файл шаблона, который определяет содержимое решение веб-узла и вызывает принудительное создание папки App_Data и App_Code. Служба. *расширения* файл копируется в папку App_Code.

-   WebService.webproj

     Этот файл является артефактом система шаблона проекта. Он соответствует ссылки файла проекта в файле WebService.vstemplate.

## <a name="project-item-template-folder"></a>Папка шаблонов элемента проекта
 Веб-шаблонов элемента проекта обычно устанавливаются в [*путь установки Visual Studio*] \Common7\IDE\ItemTemplates\Web\\, каждый во вложенную папку с именем, его веб-программирования, язык.

## <a name="project-item-templates"></a>Шаблоны элементов проекта
 Шаблоны элементов проекта веб-сайта можно использовать для добавления новых веб-страниц на веб-сайт в ответ на **Добавление существующего элемента** команды. В настоящее время поддерживаются следующие виды веб-страницы:

-   Новый класс

-   Новая HTML-страница

-   Новый веб-формы

-   Новая главная страница

### <a name="new-class"></a>Новый класс
 Этот шаблон создает новый исходный файл, определяющий пустым классом в ответ на **добавить новый класс** команды.

-   Класс. *Расширение*

     Исходный файл, который реализует пустой класс. Определяет язык codebehind *расширения* этого файла.

-   Class.vstemplate

     Файл шаблона, который создает исходный файл и определяет его содержимое.

### <a name="new-html-page"></a>Новая HTML-страница
 Этот шаблон создает новое веб-страницы в ответ на **добавить HTML-страницу** команды.

-   HTMLPage.htm

     Начальный содержимое веб-страницы. Этой веб-страницы обычно не имеет связанного codebehind зависимого файла. Для создания смарт-страницы с помощью файла связанного фонового кода, вместо этого используйте шаблон веб-форма.

-   HTMLPage.vstemplate

     Файл шаблона, который создает веб-страницы и определяет его содержимое.

### <a name="new-webform"></a>Новый веб-форма
 Этот шаблон создает новые смарт-веб-страницы в ответ на **добавить веб-форму** команды.

 Чтобы создать исходный файл зависимых фонового кода, выберите **поместить код в отдельный файл**. В противном случае создается одной веб-странице, имеет пустой блок сценария и нет \<% Page % > директивы подключить зависимого файла.

 Для создания страницы содержимого для выбранной главной странице выберите **выбрать главную страницу**.

-   WebForm.aspx

     Начальный содержимое веб-страницы. Эта веб-страница не имеет связанного codebehind зависимых файла.

-   WebForm_cb.aspx

     Начальный содержимое веб-страницы. Эта веб-страница есть файл зависимые связанные фонового кода.

-   Фонового кода. *Расширение*

     Зависимый файл, который реализует класс веб-форма. Определяет язык codebehind *расширения* этого файла.

-   ContentPage.aspx

     Содержимое начальной странице содержимого веб-страницы. Эта веб-страница не имеет связанного codebehind зависимых файла.

-   ContentPage_cb.aspx

     Содержимое начальной странице содержимого веб-страницы. Эта веб-страница есть файл зависимые связанные фонового кода.

-   WebForm.vstemplate

     Файл шаблона, определяющий содержимое новой веб-страницы и ее зависимый файл, если таковые имеются.

### <a name="new-master-page"></a>Создание главной страницы
 Этот шаблон создает новой главной страницы в ответ на **добавьте главной страницы** команды.

 Чтобы создать исходный файл зависимых фонового кода, выберите **поместить код в отдельный файл**. В противном случае создается одной веб-странице, имеет пустой блок сценария и нет \<% Page % > директивы подключить зависимого файла.

-   MasterPage.master

     Начальный содержимое главной страницы. Эта главная страница не имеет связанного codebehind зависимого файла.

-   MasterPage_cb.master

     Начальный содержимое главной страницы. Это главная страница имеет связанный codebehind зависимого файла.

-   Фонового кода. *расширения*

     Зависимый файл, который реализует класс главной страницы. Определяет язык codebehind *расширения* этого файла.

-   MasterPage.vstemplate

     Файл шаблона, определяющий содержимое новой главной страницы и ее зависимый файл, если таковые имеются.

## <a name="see-also"></a>См. также
 [Поддержка веб-сайтов](../../extensibility/internals/web-site-support.md)