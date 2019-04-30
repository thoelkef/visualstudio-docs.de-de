---
title: T4 Output-Direktive | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9262ec994ec847c38ec8d5c1ad95010a929cc4ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62549528"
---
# <a name="t4-output-directive"></a>T4 Output-Direktive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Textvorlagen wird die `output`-Anweisung zum Definieren der Dateierweiterung und Codierung der umgewandelten Datei verwendet.  
  
 Beispielsweise wenn Ihre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Projekt enthält eine Vorlagendatei, die mit dem Namen **MyTemplate.tt** enthält die folgende Anweisung:  
  
 `<#@output extension=".cs"#>`  
  
 Klicken Sie dann [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert eine Datei namens **MyTemplate.cs**  
  
 Die `output`-Anweisung ist in einer Laufzeitvorlage (vorverarbeiteten Vorlage) nicht erforderlich. Stattdessen erhält die Anwendung die generierte Zeichenfolge durch Aufruf von `TextTransform()`. Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="using-the-output-directive"></a>Verwenden der Ausgabeanweisung  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 In jeder Textvorlage sollte es nicht mehr als eine `output`-Anweisung geben.  
  
## <a name="extension-attribute"></a>Extension-Attribut  
 Gibt die Dateierweiterung der generierten Textausgabedatei an.  
  
 Der Standardwert ist **cs**  
  
 Beispiele:  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Akzeptierte Werte:  
 Jede gültige Dateierweiterung  
  
## <a name="encoding-attribute"></a>Encoding-Attribut  
 Gibt die zu verwendende Codierung bei der Generierung der Ausgabedatei an. Zum Beispiel:  
  
 `<#@ output encoding="utf-8"#>`  
  
 Der Standardwert ist die Codierung, die von der Textvorlagendatei verwendet wird.  
  
 Akzeptierte Werte:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` (Systemstandard)  
  
 Im Allgemeinen können Sie die WebName-Zeichenfolge oder die CodePage-Zahl aller von <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> zurückgegebenen Codierungen verwenden.
