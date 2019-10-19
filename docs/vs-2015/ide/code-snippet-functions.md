---
title: Codeausschnittfunktionen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 92533b90e6a2da9f29a67d13c6e0eee2c31dbcfe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620230"
---
# <a name="code-snippet-functions"></a>Codeausschnittfunktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Es stehen drei Funktionen zur Verfügung, die mit [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Codeausschnitten verwendet werden können. Funktionen werden im Element [Function](https://msdn.microsoft.com/572c5549-5821-4e15-8ecd-0fa86c1c65df) (Funktion) des Codeausschnitts angegeben. Informationen zum Erstellen von Codeausschnitten finden Sie unter [Codeausschnitte](../ide/code-snippets.md).

## <a name="functions"></a>Funktionen
 In der folgenden Tabelle werden die verfügbaren Funktionen für die Verwendung mit dem `Function`-Element in Codeausschnitten beschrieben.

|Funktion|BESCHREIBUNG|Sprache|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Es werden eine switch-Anweisung sowie mehrere case-Anweisungen für die vom `EnumerationLiteral`-Parameter angegebenen Member der Enumeration generiert. Der `EnumerationLiteral`-Parameter muss entweder ein Verweis auf ein Enumerationsliteral oder auf einen Enumerationstyp sein.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|
|`ClassName()`|Gibt den Namen der Klasse zurück, die den eingefügten Ausschnitt enthält.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|
|`SimpleTypeName(` `TypeName` `)`|Reduziert den *TypeName*-Parameter auf seine einfachste Form im Kontext, in dem der Ausschnitt aufgerufen wurde.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Verwendung der `GenerateSwitchCases`-Funktion veranschaulicht. Wenn dieser Ausschnitt eingefügt wird und eine Enumeration in das `$switch_on$`-Literal eingefügt wird, generiert das `$cases$`-Literal eine `case`-Anweisung für jeden Wert in der Enumeration.

```
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

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Verwendung der `ClassName`-Funktion veranschaulicht. Wenn dieser Ausschnitt eingefügt wird, wird das `$classname$`-Literal mit dem Namen der einschließenden Klasse an diesem Speicherort in der Codedatei ersetzt.

```
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
            <Code Language="vjsharp" Format="CData">
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

## <a name="example"></a>Beispiel
 In diesem Beispiel wird die Verwendung der `SimpleTypeName`-Funktion veranschaulicht. Wenn dieser Codeausschnitt in eine Codedatei eingefügt wird, wir das `$SystemConsole$`-Literal mit der einfachsten Form des Typs <xref:System.Console> im Kontext ersetzt, in dem der Ausschnitt aufgerufen wurde.

```
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

## <a name="see-also"></a>Siehe auch
 [Function-Element (IntelliSense-Code Ausschnitte)](https://msdn.microsoft.com/572c5549-5821-4e15-8ecd-0fa86c1c65df) [Code Ausschnitte Schema Referenz](../ide/code-snippets-schema-reference.md)
