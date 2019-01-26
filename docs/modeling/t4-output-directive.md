---
title: T4 Output-Anweisung
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 25e59e4e0273e22a1b11ea9c3e0d593f70568758
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929652"
---
# <a name="t4-output-directive"></a>T4 Output-Anweisung

In Visual Studio Textvorlagen die `output` Direktive wird verwendet, um die Dateierweiterung und Codierung der umgewandelten Datei zu definieren.

 Wenn Ihr Visual Studio-Projekt eine Vorlagendatei, die mit dem Namen umfasst beispielsweise **MyTemplate.tt** enthält die folgende Anweisung:

 `<#@output extension=".cs"#>`

 Visual Studio generiert eine Datei namens **MyTemplate.cs**

 Die `output`-Anweisung ist in einer Laufzeitvorlage (vorverarbeiteten Vorlage) nicht erforderlich. Stattdessen erhält die Anwendung die generierte Zeichenfolge durch Aufruf von `TextTransform()`. Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Verwenden der Ausgabeanweisung

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 In jeder Textvorlage sollte es nicht mehr als eine `output`-Anweisung geben.

## <a name="extension-attribute"></a>Extension-Attribut
 Gibt die Dateierweiterung der generierten Textausgabedatei an.

 Der Standardwert ist **cs**

 Beispiele: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Akzeptierte Werte: Jede gültige Dateierweiterung

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