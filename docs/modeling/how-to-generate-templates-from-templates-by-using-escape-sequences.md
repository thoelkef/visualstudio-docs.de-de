---
title: Verwenden von Escapesequenzen zum Generieren von Vorlagen aus Vorlagen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1460b03a027a2b33844edc7d617f8b5f21208772
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594642"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Gewusst wie: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen
Sie können eine Textvorlage erstellen, die eine andere Textvorlage als generierte Textausgabe erstellt. Zu diesem Zweck müssen Sie Escapesequenzen verwenden, um die Textvorlagen Tags zu beschreiben. Wenn Sie keine Escapesequenzen verwenden, weist die generierte Textvorlage eine vordefinierte Bedeutung auf. Weitere Informationen zum Verwenden von Escapesequenzen in Textvorlagen finden Sie unter Verwenden von Escapesequenzen [in Textvorlagen](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>So generieren Sie eine Textvorlage aus einer Textvorlage

- Verwenden Sie den umgekehrten Schrägstrich ( \\ ) als Escapezeichen, um die erforderlichen Markup Tags in der Textvorlage für Direktiven, Anweisungen, Ausdrücke und Klassen Funktionen in einer separaten Textvorlagen Datei zu erstellen.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden Escapezeichen verwendet, um eine Textvorlage aus einer Textvorlage zu erstellen. Die- `output` Direktive legt den Ziel Dateityp auf den Textvorlagen-Dateityp (. tt) fest.

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

 Bei der generierten Textausgabe handelt es sich um eine Textvorlage.

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
