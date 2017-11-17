---
title: 'Vorgehensweise: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: "35"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 421b8a8bde2bb383889bcb58915fa8a3acb027cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Gewusst wie: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen
Sie können eine Textvorlage erstellen, die eine andere Textvorlage als die generierte Textausgabe wird erstellt. Zu diesem Zweck müssen Sie Escapesequenzen verwenden, die Text Vorlagentags abgrenzen. Wenn Sie keine Escapesequenzen verwenden, wird die generierte Textvorlage eine vordefinierte Bedeutung haben. Weitere Informationen zum Verwenden von Escapesequenzen in Textvorlagen finden Sie unter [mithilfe von Escapesequenzen in Textvorlagen](../modeling/using-escape-sequences-in-text-templates.md).  
  
### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Eine Textvorlage in einer Textvorlage generieren  
  
-   Verwenden Sie den umgekehrten Schrägstrich (\\) als Escapezeichen zum Erzeugen der erforderlichen Markuptags innerhalb der Vorlage "Text" für Richtlinien, Anweisungen, Ausdrücke und Funktionen in einer separaten Textvorlagendatei Klasse.  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Escape-Zeichen eine Textvorlage in einer Textvorlage erzeugt. Die `output` Richtlinie legt den Zieltyp für die Datei auf den Dateityp des Text-Vorlage (TT).  
  
```csharp  
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
  
 Die generierte Textausgabe wird eine Textvorlage.  
  
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