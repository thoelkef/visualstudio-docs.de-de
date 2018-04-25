---
title: T4 Output-Direktive
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 231781ee06088fef73f33fa84e9b53825f5f6a82
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="t4-output-directive"></a>T4 Output-Direktive

In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Textvorlagen wird die `output`-Direktive zum Definieren der Dateierweiterung und Codierung der umgewandelten Datei verwendet.

 Beispielsweise, wenn Ihre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Projekt enthält eine Vorlagendatei mit dem Namen **MyTemplate.tt** enthält die folgende Anweisung:

 `<#@output extension=".cs"#>`

 Klicken Sie dann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert eine Datei namens **MyTemplate.cs**

 Die `output`-Direktive ist in einer Laufzeitvorlage (vorverarbeiteten Vorlage) nicht erforderlich. Stattdessen erhält die Anwendung die generierte Zeichenfolge durch Aufruf von `TextTransform()`. Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Verwenden der Ausgabedirektive

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 In jeder Textvorlage sollte es nicht mehr als eine `output`-Direktive geben.

## <a name="extension-attribute"></a>Extension-Attribut
 Gibt die Dateierweiterung der generierten Textausgabedatei an.

 Der Standardwert ist **cs**

 Beispiele: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Zulässige Werte: Jede gültige Dateierweiterung.

## <a name="encoding-attribute"></a>Encoding-Attribut
 Gibt die zu verwendende Codierung bei der Generierung der Ausgabedatei an. Beispiel:

 `<#@ output encoding="utf-8"#>`

 Der Standardwert ist die Codierung, die von der Textvorlagendatei verwendet wird.

 Zulässige Werte: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Systemstandard)

 Im Allgemeinen können Sie die WebName-Zeichenfolge oder die CodePage-Zahl aller von <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> zurückgegebenen Codierungen verwenden.