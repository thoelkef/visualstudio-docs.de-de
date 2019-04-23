---
title: 'Vorgehensweise: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35047c6c0887d02f3adcba763de05b8d4a1cd00b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042482"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Vorgehensweise: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen
Sie können eine Textvorlage erstellen, die einer anderen Textvorlage als Ausgabe generierte Text erstellt. Zu diesem Zweck müssen Sie Escapesequenzen verwenden, der Textvorlagentags abgrenzen. Wenn Sie nicht Escapesequenzen verwenden, müssen Ihre Vorlage generierte Text eine vordefinierte Bedeutung. Weitere Informationen zum Verwenden von Escapesequenzen in Textvorlagen finden Sie unter [mithilfe von Escapesequenzen in Textvorlagen](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Um eine Textvorlage in einer Textvorlage zu generieren.

- Verwenden Sie den umgekehrten Schrägstrich (\\) als Escapezeichen verwenden, erstellen die notwendigen Markuptags in die Textvorlage für Anweisungen, Anweisungen, Ausdrücke und Funktionen in einer separaten Textvorlagendatei Klasse.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Escape-Zeichen eine Textvorlage, die von einer Textvorlage erzeugt. Die `output` Richtlinie legt den Zieltyp für die Datei auf den Dateityp des Text-Vorlage (TT).

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