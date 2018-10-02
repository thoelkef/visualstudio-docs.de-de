---
title: 'Vorgehensweise: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7cc523aed43dfbe3339c3f3cc054c09b39a4f060
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521998"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Gewusst wie: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [wie: Generieren von Vorlagen aus Vorlagen durch Verwenden von Escapesequenzen](https://docs.microsoft.com/visualstudio/modeling/how-to-generate-templates-from-templates-by-using-escape-sequences).  
  
Sie können eine Textvorlage erstellen, die einer anderen Textvorlage als Ausgabe generierte Text erstellt. Zu diesem Zweck müssen Sie Escapesequenzen verwenden, der Textvorlagentags abgrenzen. Wenn Sie nicht Escapesequenzen verwenden, müssen Ihre Vorlage generierte Text eine vordefinierte Bedeutung. Weitere Informationen zum Verwenden von Escapesequenzen in Textvorlagen finden Sie unter [mithilfe von Escapesequenzen in Textvorlagen](../modeling/using-escape-sequences-in-text-templates.md).  
  
### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Um eine Textvorlage in einer Textvorlage zu generieren.  
  
-   Verwenden Sie den umgekehrten Schrägstrich (\\) als Escapezeichen verwenden, erstellen die notwendigen Markuptags in die Textvorlage für Anweisungen, Anweisungen, Ausdrücke und Funktionen in einer separaten Textvorlagendatei Klasse.  
  
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



