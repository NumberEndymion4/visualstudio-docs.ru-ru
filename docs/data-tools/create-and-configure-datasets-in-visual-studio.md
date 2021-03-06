---
title: Создание и Настройка наборов данных в Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8cbe95887e9a29fa98932a18c240bc558201fc43
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Создание и Настройка наборов данных в Visual Studio

Объект *dataset* — это набор объектов, хранения данных из базы данных в памяти и поддерживает отслеживание изменений, чтобы включить создание, чтение, обновление и удаление (CRUD) операций с этими данными, без необходимости всегда необходимо подключение к базе данных. Наборы данных были разработаны для простой *форм на основе данных* бизнес-приложений. Для новых приложений рассмотрите возможность использования Entity Framework для хранения и модели данных в памяти. Для работы с наборами данных, должны иметь базовых знаний о основными понятиями баз данных.

Можно создать типизированный <xref:System.Data.DataSet> класс в Visual Studio во время разработки с помощью **мастер настройки источника данных**. Сведения о создании наборов данных программным путем см. в разделе [Создание набора данных (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Создать новый набор данных с помощью мастера настройки источника данных

1.  На **проекта** меню, нажмите кнопку **добавить новый источник данных** запуск **мастер настройки источника данных**.

2.  Выберите тип источника данных, который вы будете подключаться.

     ![Мастер настройки источника данных](../data-tools/media/data-source-configuration-wizard.png "мастера настройки источника данных")

3.  Для баз данных выберите базы данных, которые будут источником данных для набора данных.

     ![Выбор источника данных соединения](../data-tools/media/data-source-choose-a-connection.png "источника данных выберите соединение")

4.  Выберите таблицы (или отдельных столбцов), хранимые процедуры, функции и представления из базы данных, который необходимо представить в наборе данных.

     ![Выберите объекты базы данных](../data-tools/media/raddata-chose-objects.png "raddata выбрал объектов")

5.  Нажмите кнопку **Готово**.

6.  Набор данных отображается как узел в **обозревателе решений**:

     ![Набор данных в обозревателе решений](../data-tools/media/dataset-in-solution-explorer.png "набора данных в обозревателе решений")

     Щелкните этот узел и набор данных отображается в **конструктора наборов данных**. Обратите внимание, что каждая таблица в наборе данных содержит связанный объект TableAdapter, который представлен в нижней. Адаптер таблицы используется для заполнения набора данных и при необходимости отправлять команды в базу данных.

     ![Конструктор наборов данных](../data-tools/media/dataset-designer.png "конструктора наборов данных")

7.  Отношение линии, соединяющие таблицы представляют связи между таблицами, как определено в базе данных. По умолчанию ограничения внешнего ключа в базе данных представляются в виде связь только с обновления и удаления правил, значение none. Как правило это самое интересное. Тем не менее, можно щелкнуть строки, чтобы вызвать **отношения** диалоговое окно, где можно изменить поведение иерархических обновлений. Дополнительные сведения см. в разделе [отношения в наборах данных](../data-tools/relationships-in-datasets.md) и [иерархическое обновление](../data-tools/hierarchical-update.md).

     ![Диалоговое окно отношение объекта DataSet](../data-tools/media/raddata-relation-dialog.png "диалоговое окно raddata отношения")

8.  Щелкните таблицу, адаптер таблицы или имя столбца в таблице для просмотра его свойств в **свойства** окна. Можно изменить некоторые значения здесь. Просто помните, что изменения вносятся набора данных, а не базы данных-источника.

     ![Свойства столбца набора данных](../data-tools/media/dataset-column-properties.png "свойства столбца набора данных")

9. Можно добавить новые таблицы или адаптеры таблиц набора данных, или добавить новые запросы для существующих адаптеров таблиц или укажите новые связи между таблицами путем перетаскивания этих элементов из **элементов** вкладки. На этой вкладке отображается после **конструктора наборов данных** находится в фокусе.

     ![Набор данных элементов](../data-tools/media/raddata-dataset-toolbox.png "raddata элементов набора данных")

10. После этого может потребоваться указать способ заполнения набора данных с данными. Для этого используйте **мастер настройки адаптера таблицы**. Дополнительные сведения см. в разделе [заполнения набора данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Добавить таблицу базы данных или другого объекта в существующий набор данных

Эта процедура демонстрирует добавление таблицы из той же базе данных, который использовался для создания набора данных сначала.

1.  Щелкните узел набора данных в **обозревателе решений** для переноса фокуса в конструкторе наборов данных.

2.  Нажмите кнопку **источники данных** вкладку в левом поле Visual Studio, или введите `Data Sources` в **быстрого запуска**.

3.  Щелкните правой кнопкой мыши узел набора данных и выберите **Настройка источника данных с помощью мастера**.

     ![Контекстное меню источника данных](../data-tools/media/data-source-context-menu.png "контекстное меню источника данных")

4.  Используйте мастер, чтобы указать, какие дополнительные таблицы, хранимые процедуры или другого объекта базы данных, чтобы добавить в набор данных.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Добавление отдельной таблицы к набору данных

1.  Откройте свой набор данных в **конструктора наборов данных**.

2.  Перетащите <xref:System.Data.DataTable> класса из **DataSet** вкладке **элементов** на **конструктора наборов данных**.

3.  Добавьте столбцы для определения таблицы данных. Щелкните правой кнопкой мыши в таблице и выберите **Добавить > столбец**. Используйте **свойства** окно, чтобы задать тип данных столбца и ключ, при необходимости.

4.  Автономный таблицы должны реализовать `Fill` логику в изолированных таблиц, чтобы их можно заполнить данными. Сведения о заполнении отдельной таблицы. в разделе [заполнение DataSet из объекта DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>См. также

- [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)