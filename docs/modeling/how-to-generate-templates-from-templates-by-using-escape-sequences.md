---
title: "How to: Generate Templates from Templates By Using Escape Sequences | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, generating templates from templates"
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 35
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 35
---
# How to: Generate Templates from Templates By Using Escape Sequences
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können eine Textvorlage erstellen, die eine andere Textvorlage als generierte Textausgabe erstellt.  Dazu müssen Sie die Textvorlagentags mit Escapesequenzen abgrenzen.  Wenn Sie keine Escapesequenzen verwenden, hat die generierte Textvorlage eine vordefinierte Bedeutung.  Weitere Informationen zur Verwendung von Escapesequenzen in Textvorlagen finden Sie unter [Using Escape Sequences in Text Templates](../modeling/using-escape-sequences-in-text-templates.md).  
  
### So generieren Sie innerhalb einer Textvorlage eine Textvorlage  
  
-   Verwenden Sie den umgekehrten Schrägstrich \(\\\) als Escapezeichen, um die erforderlichen Markuptags in der Textvorlage für Direktiven, Anweisungen, Ausdrücke und Klassenfunktionen in einer separaten Textvorlagendatei zu erzeugen.  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## Beispiel  
 Im folgenden Beispiel werden Escapezeichen verwendet, um aus einer Textvorlage eine Textvorlage zu erzeugen.  Die `output`\-Direktive legt den Zieldateityp auf den Textvorlagendateityp \(.tt\) fest.  
  
```c#  
\<#@ output extension=".tt" \#>  
\<#@ assembly name="System.Xml.dll" \#>  
\<#@ import namespace="System.Xml" \#>  
\<#  
XmlDocument xDoc = new XmlDocument();  
//System.Diagnostics.Debugger.Break();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {\#>  
           \<#= attr.Name \#>  
       \<#}  
     }  
\#>  
```  
  
 Die generierte Textausgabe ist eine Textvorlage.  
  
```  
<#@ output extension=".tt" #>  
<#@ assembly name="System.Xml.dll" #>  
<#@ import namespace="System.Xml" #>  
<#  
XmlDocument xDoc = new XmlDocument();  
//System.Diagnostics.Debugger.Break();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {#>  
           <#= attr.Name #>  
       <#}  
     }  
#>  
```