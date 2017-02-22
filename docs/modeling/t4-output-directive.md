---
title: "T4 Output Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 4
caps.handback.revision: 4
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 Output Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Textvorlagen wird die `output`\-Direktive zum Definieren der Dateierweiterung und Codierung der umgewandelten Datei verwendet.  
  
 Wenn zum [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekt beispielsweise eine Vorlagendatei mit dem Namen **MyTemplate.tt** gehört, die die folgende Direktive enthält:  
  
 `<#@output extension=".cs"#>`  
  
 erstellt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eine Datei mit dem Namen **MyTemplate.cs**  
  
 Die `output`\-Direktive ist in einer Laufzeitvorlage \(vorverarbeiteten Vorlage\) nicht erforderlich.  Stattdessen erhält die Anwendung die generierte Zeichenfolge durch Aufruf von `TextTransform()`.  Weitere Informationen finden Sie unter [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## Verwenden der Ausgabedirektive  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 In jeder Textvorlage sollte es nicht mehr als eine `output`\-Direktive geben.  
  
## extension\-Attribut  
 Gibt die Dateierweiterung der generierten Textausgabedatei an.  
  
 Der Standardwert ist **.cs**  
  
 Beispiele:  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Akzeptierte Werte:  
 Jede gültige Dateierweiterung  
  
## encoding\-Attribut  
 Gibt die zu verwendende Codierung bei der Generierung der Ausgabedatei an.  Beispiel:  
  
 `<#@ output encoding="utf-8"#>`  
  
 Der Standardwert ist die Codierung, die von der Textvorlagendatei verwendet wird.  
  
 Akzeptierte Werte:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` \(Systemstandard\)  
  
 Im Allgemeinen können Sie die WebName\-Zeichenfolge oder die CodePage\-Zahl aller von <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> zurückgegebenen Codierungen verwenden.