---
title: Функции фрагмента кода
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ead5a3f15f5ba7f586c9dfcec86fb309cbda391f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="code-snippet-functions"></a>Функции фрагмента кода

С фрагментами кода C# можно использовать три функции. Функции указываются в элементе [Function](../ide/code-snippets-schema-reference.md#function) фрагмента кода. Сведения о создании фрагментов кода см. в статье [Фрагменты кода](../ide/code-snippets.md).

## <a name="functions"></a>Функции

Следующая таблица описывает функции, доступные для использования с элементом `Function` во фрагментах кода.

|Функция|Описание:|Язык|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Формирует оператор switch и набор операторов case для членов перечисления, заданных параметром `EnumerationLiteral`. Параметр `EnumerationLiteral` должен быть ссылкой на литерал перечисления или тип перечисления.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|
|`ClassName()`|Возвращает имя класса, содержащего вставленный фрагмент кода.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|
|`SimpleTypeName(` `TypeName` `)`|Редуцирует параметр *TypeName* до его простейшей формы в контексте, в котором был вызван фрагмент.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|

## <a name="example"></a>Пример

В следующем примере показано, как использовать функцию `GenerateSwitchCases`. При вставке данного фрагмента и вводе перечисления в литерал `$switch_on$` литерал `$cases$` создает оператор `case` для каждого значения в перечислении.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>switch</Title>
            <Shortcut>switch</Shortcut>
            <Description>Code snippet for switch statement</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>expression</ID>
                    <ToolTip>Expression to switch on</ToolTip>
                    <Default>switch_on</Default>
                </Literal>
                <Literal Editable="false">
                    <ID>cases</ID>
                    <Function>GenerateSwitchCases($expression$)</Function>
                    <Default>default:</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    switch ($expression$)
                    {
                        $cases$
                    }
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="example"></a>Пример

В следующем примере показано, как использовать функцию `ClassName`. При вставке этого фрагмента литерал `$classname$` заменяется именем включающего класса в этом месте файла кода.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Common constructor pattern</Title>
            <Shortcut>ctor</Shortcut>
            <Description>Code Snippet for a constructor</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>type</ID>
                    <Default>int</Default>
                </Literal>
                <Literal>
                    <ID>name</ID>
                    <Default>field</Default>
                </Literal>
                <Literal default="true" Editable="false">
                    <ID>classname</ID>
                    <ToolTip>Class name</ToolTip>
                    <Function>ClassName()</Function>
                    <Default>ClassNamePlaceholder</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp" Format="CData">
                <![CDATA[
                    public $classname$ ($type$ $name$)
                    {
                        this._$name$ = $name$;
                    }
                    private $type$ _$name$;
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="example"></a>Пример

Этот пример показывает, как использовать функцию `SimpleTypeName`. При вставке этого фрагмента в файл кода литерал `$SystemConsole$` заменяется простейшей формой типа <xref:System.Console> в контексте, в котором фрагмент был вызван.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Console_WriteLine</Title>
            <Shortcut>cw</Shortcut>
            <Description>Code snippet for Console.WriteLine</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal Editable="false">
                    <ID>SystemConsole</ID>
                    <Function>SimpleTypeName(global::System.Console)</Function>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    $SystemConsole$.WriteLine();
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>См. также

- [Элемент Function](../ide/code-snippets-schema-reference.md#function)
- [Справочник по схеме фрагментов кода](../ide/code-snippets-schema-reference.md)
