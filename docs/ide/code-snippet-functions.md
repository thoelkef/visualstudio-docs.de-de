---
title: "Codeausschnittfunktionen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Codeausschnitte [Visual Studio], Funktionen"
  - "IntelliSense-Codeausschnitte, Funktionen"
  - "Ausschnitte [Visual Studio], Funktionen"
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Codeausschnittfunktionen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Drei Funktionen stehen für die Verwendung mit [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Codeausschnitten zur Verfügung.  Funktionen werden im [Function](http://msdn.microsoft.com/de-de/572c5549-5821-4e15-8ecd-0fa86c1c65df)\-Element des Codeausschnitts angegeben.  Informationen zum Erstellen von Codeausschnitten finden Sie unter [Codeausschnitte](../ide/code-snippets.md).  
  
## Funktionen  
 In der folgenden Tabelle werden die zur Verwendung mit dem `Function`\-Element in Codeausschnitten verfügbaren Funktionen beschrieben.  
  
|Funktion|Beschreibung|Sprache|  
|--------------|------------------|-------------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Generiert eine switch\-Anweisung und eine Gruppe von case\-Anweisungen für die Member der durch den `EnumerationLiteral`\-Parameter angegebenen Enumeration.  Der `EnumerationLiteral`\-Parameter muss entweder ein Verweis auf ein Enumerationsliteral oder ein Enumerationstyp sein.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`ClassName()`|Gibt den Namen der Klasse zurück, die den eingefügten Ausschnitt enthält.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|Reduziert den *TypeName*\-Parameter im Kontext, in dem der Ausschnitt aufgerufen wurde, auf seine einfachste Form.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `GenerateSwitchCases`\-Funktion veranschaulicht.  Wenn dieser Ausschnitt eingefügt und eine Enumeration in das `$switch_on$`\-Literal eingegeben wird, generiert das `$cases$`\-Literal eine `case`\-Anweisung für jeden Wert in der Enumeration.  
  
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
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `ClassName`\-Funktion veranschaulicht.  Wenn dieser Ausschnitt eingefügt wird, wird das `$classname$`\-Literal an dieser Stelle in der Codedatei durch den Namen der einschließenden Klasse ersetzt.  
  
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
  
## Beispiel  
 Dieses Beispiel veranschaulicht die Verwendung der `SimpleTypeName`\-Funktion.  Wenn dieser Ausschnitt in eine Codedatei eingefügt wird, wird das `$SystemConsole$`\-Literal in dem Kontext, in dem der Ausschnitt aufgerufen wurde, durch die einfachste Form des <xref:System.Console>\-Typs ersetzt.  
  
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
  
## Siehe auch  
 [Function Element \(Intellisense Code Snippets\)](http://msdn.microsoft.com/de-de/572c5549-5821-4e15-8ecd-0fa86c1c65df)   
 [Schemareferenz für Codeausschnitte](../ide/code-snippets-schema-reference.md)