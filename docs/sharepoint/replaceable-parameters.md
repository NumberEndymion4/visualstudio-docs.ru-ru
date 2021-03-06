---
title: Подстановочные параметры | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86d6b08d209703f73901d7a839c731e1a9a63fdd
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2018
---
# <a name="replaceable-parameters"></a>Подстановочные параметры
  Подстановочные параметры или *маркеры*, можно использовать в файлах проекта для представления значений элементов решения SharePoint, фактические значения не известны во время разработки. Они действуют аналогично стандартным токенам шаблонов [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [параметров шаблона](/visualstudio/ide/template-parameters).  
  
## <a name="token-format"></a>Формат маркера  
 Токены начинаться и заканчиваться символом доллара ($). В развертывании маркеры, используемые заменяются фактическими значениями во время упаковки проекта в пакет решения SharePoint (WSP-файл). Например, маркер **$SharePoint.Package.Name$** может разрешаться в строку «Тестовый пакет SharePoint».  
  
## <a name="token-rules"></a>Правила токенов  
 Токены, применяются следующие правила:  
  
-   Токены можно помещать в любом месте в строке.  
  
-   Токен не может занимать несколько строк.  
  
-   Тот же токен может быть указан несколько раз в той же строке и в том же файле.  
  
-   Можно указать различные маркеры в той же строке.  
  
 Токены, которые не соответствуют этим правилам, игнорируются без предоставления предупреждения или ошибки.  
  
 Замена токенов значениями строки выполняется немедленно после преобразования манифеста. Эта замена позволяет пользователю изменять шаблоны манифеста с маркерами.  
  
### <a name="token-name-resolution"></a>Разрешение имен токенов  
 В большинстве случаев токен разрешается в конкретное значение независимо от того, где он содержится. Тем не менее если маркер относится к пакету или компонент, значение токена зависит от которой он содержится. Например, если компонент находится в пакет, токен `$SharePoint.Package.Name$` разрешается в значение «Пакет а». Если же компонент находится в пакете Б, затем `$SharePoint.Package.Name$` разрешается в «пакет б».  
  
## <a name="tokens-list"></a>Список токенов  
 В следующей таблице перечислены доступные токены.  
  
|name|Описание|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Имя файла содержащего проекта, такие как «NewProj.csproj».|  
|$SharePoint.Project.FileNameWithoutExtension$|Имя файла содержащего проекта без расширения имени файла. Например, «NewProj».|  
|$SharePoint.Project.AssemblyFullName$|Отображаемое имя (строгое имя) проекта, содержащего выходной сборки.|  
|$SharePoint.Project.AssemblyFileName$|Имя проекта, содержащего выходной сборки.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Имя проекта, содержащего выходной сборки без расширения имени файла.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Токен открытого ключа, содержащего проекта выходной сборки, преобразованное в строку. (16 символов «x2» шестнадцатеричном формате.)|  
|$SharePoint.Package.Name$|Имя пакета.|  
|$SharePoint.Package.FileName$|Имя файла определения содержащего пакета.|  
|$SharePoint.Package.FileNameWithoutExtension$|Имя файла определения содержащего пакета (без расширения).|  
|$SharePoint.Package.Id$|Идентификатор содержащего пакета SharePoint. Если компонент используется в нескольких пакетах, это значение будет изменено.|  
|$SharePoint.Feature.FileName$|Имя файла определения содержащего компонента, например Feature1.feature.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Имя файла определения компонента без расширения имени файла.|  
|$SharePoint.Feature.DeploymentPath$|Имя папки, содержащей компонент в пакете. Этот токен соответствует свойству «Путь развертывания» в конструкторе компонентов. Например, значение — «Project1_Feature1».|  
|$SharePoint.Feature.Id$|Идентификатор SharePoint, содержащей функции. Этот маркер, как все токены функциональным уровнем, могут использоваться только в файлах, включенных в пакет с помощью компонента, не добавляется непосредственно пакета вне компонента.|  
|$SharePoint.ProjectItem.Name$|Имя элемента проекта (не имя файла), как получено из **ISharePointProjectItem.Name**.|  
|$SharePoint.Type. \<GUID >. AssemblyQualifiedName$|Имя типа, включающее наименование сборки и соответствующее идентификатору [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] токена. Идентификатор [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] задается символами в нижнем регистре в формате, аналогичном формату Guid.ToString("D") (т. е. "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx").|  
|$SharePoint.Type. \<GUID >. FullName$|Полное имя типа, соответствующее идентификатору GUID в токене. Формат идентификатора GUID, производится в нижнем регистре и соответствует формату Guid.ToString("D") (т. е xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
  
## <a name="adding-extensions-to-the-token-replacement-file-extensions-list"></a>Добавление расширений для замещения токена список расширений файлов  
 Несмотря на то, что теоретически токены можно использовать в любом файле, к которой принадлежит элемент включена в пакет, по умолчанию проекта SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] выполняет поиск токенов только в пакет файлы, файлы манифеста и файлов, имеющих следующие расширения:  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Веб-части  
  
-   DWP  
  
 Эти расширения определены в `<TokenReplacementFileExtensions>` элемент в файле Microsoft.VisualStudio.SharePoint.targets, расположенном в... \\< программные файлы\>папки \MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools.  
  
 Тем не менее, можно добавить дополнительные расширения файлов в список. Добавить `<TokenReplacementFileExtensions>` элемент в любую группу свойств в файле проекта SharePoint, определенном перед \<Import > файла целевых объектов SharePoint.  
  
> [!NOTE]  
>  Поскольку замена токенов осуществляется после компиляции проекта, не следует добавлять расширения файлов для типов файлов, которые компилируются, например .cs, .vb или RESX. Токены заменяются только в файлах, которые не были скомпилированы.  
  
 Например, чтобы добавить в список расширений имен файлов для замещения токена расширения имени файла «.myextension» и «.yourextension», необходимо добавить следующую команду, чтобы `.csproj` файла:  
  
```xml  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 Расширения можно добавить непосредственно в TARGETS-файл. Тем не менее, поскольку в этом изменяет список расширений для всех проектов SharePoint, размещенных в локальной системе не только свои собственные. Это может быть удобно, когда в системе только один разработчик или если это требуется для большинства проектов. Тем не менее так как он зависит от системы, этот подход не является переносимым и таким образом, рекомендуется добавляются все расширения, файл проекта вместо.  
  
## <a name="see-also"></a>См. также  
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  