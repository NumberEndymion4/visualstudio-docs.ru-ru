---
title: Реализация генераторы одного файла | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71db8036634cfc266db3c585c48317262f48b367
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-single-file-generators"></a>Реализация генераторы одного файла
Пользовательский инструмент — иногда называют генератора единственного файла — можно использовать для расширения [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] и [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] систем в проекта [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Настраиваемое средство — это COM-компонент, реализующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейса. Через этот интерфейс, пользовательский инструмент преобразует одного входного файла в один выходной файл. Результат преобразования может быть исходного кода, или любой другой выход, полезно. Два примера файлы пользовательского кода, создаваемых средством — код, созданный в ответ на изменения в визуальный конструктор и файлы, созданные с помощью языка описания веб-служб (WSDL).  
  
 При загрузке пользовательского инструмента или при сохранении входной файл, система проекта вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> метода и передает ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> интерфейс обратного вызова, при котором средство сообщения о ходе выполнения для пользователя.  
  
 Выходной файл, который создает пользовательский инструмент добавляется в проект ссылки на входной файл. Система проекта автоматически определяет имя выходного файла, на основе строки, возвращенные реализацию пользовательского инструмента <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Необходимо реализовать пользовательский инструмент <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейса. При необходимости поддерживать пользовательские средства <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> интерфейс для извлечения сведений из источника, отличного от входного файла. В любом случае, прежде чем использовать пользовательский инструмент, его необходимо зарегистрировать в системе или в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] локального реестра. Дополнительные сведения о регистрации пользовательских средств см. в разделе [регистрации генераторы одиночных файлов](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>См. также  
 [Предоставление типов конструкторам визуальных элементов](../../extensibility/internals/exposing-types-to-visual-designers.md)