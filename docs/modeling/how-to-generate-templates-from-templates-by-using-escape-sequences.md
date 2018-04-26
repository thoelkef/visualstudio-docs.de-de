---
title: 'Gewusst wie: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 13ca6a9aef2f0944ba1f42c849d9f8079a56a82b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
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