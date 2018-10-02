---
title: T4 Output-Anweisung
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 624afd32a9b0f44e3190fba7e3b126663b96f6f4
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860198"
---
# <a name="t4-output-directive"></a>T4 Output-Anweisung

In Visual Studio Textvorlagen die `output` Direktive wird verwendet, um die Dateierweiterung und Codierung der umgewandelten Datei zu definieren.

 Wenn Ihr Visual Studio-Projekt eine Vorlagendatei, die mit dem Namen umfasst beispielsweise **MyTemplate.tt** enthält die folgende Anweisung:

 `<#@output extension=".cs"#>`

 Visual Studio generiert eine Datei namens **MyTemplate.cs**

 Die `output`-Direktive ist in einer Laufzeitvorlage (vorverarbeiteten Vorlage) nicht erforderlich. Stattdessen erhält die Anwendung die generierte Zeichenfolge durch Aufruf von `TextTransform()`. Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Verwenden der Ausgabeanweisung

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

 Gültige Werte: Gültige Dateierweiterung.

## <a name="encoding-attribute"></a>Encoding-Attribut
 Gibt die zu verwendende Codierung bei der Generierung der Ausgabedatei an. Beispiel:

 `<#@ output encoding="utf-8"#>`

 Der Standardwert ist die Codierung, die von der Textvorlagendatei verwendet wird.

 Gültige Werte: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Systemstandard)

 Im Allgemeinen können Sie die WebName-Zeichenfolge oder die CodePage-Zahl aller von <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> zurückgegebenen Codierungen verwenden.