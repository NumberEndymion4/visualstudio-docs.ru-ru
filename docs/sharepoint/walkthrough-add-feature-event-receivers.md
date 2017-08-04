---
title: "Пошаговое руководство. Добавление приемников событий компонентов"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "разработка приложений SharePoint в Visual Studio, расширенные средства создания пакетов"
  - "разработка приложений SharePoint в Visual Studio, приемники событий"
  - "разработка приложений SharePoint в Visual Studio, приемники событий компонента"
ms.assetid: fbd44c33-2c27-4d57-abca-21cddc16fbc3
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Пошаговое руководство. Добавление приемников событий компонентов
  Приемники событий компонентов — это методы, выполняемые при возникновении следующих событий в SharePoint, связанных с компонентами:  
  
-   установка компонента;  
  
-   включение компонента;  
  
-   отключение компонента;  
  
-   удаление компонента.  
  
 В этом пошаговом руководстве показано, как добавить приемник событий в компонент проекта SharePoint.  В этом примере демонстрируются следующие задачи.  
  
-   Создание пустого проекта с приемником событий компонента.  
  
-   Работа с методом **FeatureDeactivating**.  
  
-   Добавление объявлений в список Announcements с помощью объектной модели проекта SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   Поддерживаемые выпуски Microsoft Windows и SharePoint.  Для получения дополнительной информации см. [Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Создание проекта приемника событий компонента  
 Сначала необходимо создать проект, в котором будет содержаться приемник событий компонента.  
  
#### Создание проекта с приемником событий компонента  
  
1.  В строке меню последовательно выберите пункты **Файл**, **Создать**, **Проект**, чтобы открыть диалоговое окно **Новый проект**.  
  
2.  Разверните узел **SharePoint**, расположенный в области **Visual C\#** или **Visual Basic**, и выберите узел **2010**.  
  
3.  На панели **Шаблоны** выберите шаблон **Проект SharePoint 2010**.  
  
     Этот тип проекта предназначен для приемников событий компонентов, поскольку для них нет шаблона проекта.  
  
4.  В поле **Имя** введите FeatureEvtTest и нажмите кнопку **ОК**, чтобы открыть **Мастер настройки SharePoint**.  
  
5.  На странице **Укажите сайт и уровень безопасности для отладки** введите URL\-адрес сайта сервера SharePoint, в который требуется добавить пользовательский элемент поля, или примите расположение по умолчанию \(http:\/\/\<*system name*\>\/\).  
  
6.  В разделе **Какова степень доверия для этого решения SharePoint?** выберите **Развернуть как решение фермы**.  
  
     Дополнительные сведения о сравнительных особенностях обезвреженных решений и решений фермы см. в разделе [Замечания об обезвреженных решениях](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Нажмите кнопку **Готово**, а затем обратите внимание, что компонент с именем Feature1 находится в узле **Компоненты**.  
  
## Добавление приемника событий в компонент  
 Теперь добавьте в компонент приемник событий и добавьте код, выполняемый при отключении этого компонента.  
  
#### Добавление приемника событий в компонент  
  
1.  Откройте контекстное меню для узла компонентов, а затем выберите **Добавить компонент**, чтобы создать компонент.  
  
2.  В узле **Компоненты** откройте контекстное меню для **Feature1**, а затем выберите **Добавить приемник событий**, чтобы добавить приемник событий в компонент.  
  
     В компонент Feature1 добавится файл кода.  В данном случае он будет иметь имя Feature1.EventReceiver.cs или Feature1.EventReceiver.vb, в зависимости от языка программирования, используемого в проекте.  
  
3.  Если проект написан на [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], добавьте следующий код в начало приемника событий, если он еще не находится там:,  
  
     [!code-csharp[SP_FeatureEvt#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  Класс приемника событий содержит несколько закомментированных методов, действующих как события.  Замените метод **FeatureDeactivating** следующим кодом.  
  
     [!code-csharp[SP_FeatureEvt#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#2)]
     [!code-vb[SP_FeatureEvt#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_featureevt/vb/features/feature1/feature1.eventreceiver.vb#2)]  
  
## Тестирование приемника событий компонента  
 Затем отключите компонент, чтобы проверить, выдаст ли метод **FeatureDeactivating** объявление в список объявлений в SharePoint.  
  
#### Тестирование приемника событий компонента  
  
1.  Задайте для свойства **Активная конфигурация развертывания** проекта значение **Без активации**.  
  
     Это предотвратит активацию компонента в SharePoint и позволит выполнить отладку приемников событий компонентов.  Дополнительные сведения см. в разделе [Отладка решений SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
2.  Нажмите клавишу **F5** для запуска проекта и его развертывания в SharePoint.  
  
3.  В верхней части веб\-страницы SharePoint откройте меню **Действия сайта**, а затем выберите **Параметры сайта**.  
  
4.  В разделе **Действия сайта** на странице **Параметры сайта** выберите ссылку **Управление компонентами сайта**.  
  
5.  На странице **Компоненты** нажмите кнопку **Включить** рядом с компонентом **FeatureEvtTest Feature1**.  
  
6.  На странице **Компоненты**, нажмите кнопку **Деактивировать** рядом с компонентом **FeatureEvtTest Feature1**, а затем выберите ссылку **Деактивировать этот компонент**, подтверждающую отключения компонента.  
  
7.  Нажмите кнопку **Домой**.  
  
     Обратите внимание, что после отключения компонента появилось объявление в списке **Announcements**.  
  
## См. также  
 [Практическое руководство. Создание приемника событий](../sharepoint/how-to-create-an-event-receiver.md)   
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  