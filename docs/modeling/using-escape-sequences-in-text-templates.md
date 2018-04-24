---
title: Verwenden von Escapesequenzen in Textvorlagen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ef3cb58c9352e81fc959dfdd2ddebd354e834fbf
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="using-escape-sequences-in-text-templates"></a>Verwenden von Escapesequenzen in Textvorlagen
Sie können Escapesequenzen in Textvorlagen zum Generieren von Vorlagen-Tags für Text und (im C#-Code nur) zum Steuerelement Escapezeichen und die Anführungszeichen stehen.

 Um öffnende und schließende Tags für eine standardmäßige Codeblock in die Ausgabedatei drucken, versehen Sie die Tags wie folgt:

```
\<# ... \#>
```

 Sie können auch mit anderen Text Vorlage Richtlinie und Code-Block Tags vornehmen.

 Enthält ein TextBlock Zeichenfolgen verwendet, um die Vorlagen-Tags für Text mit Escapezeichen versehen, können Sie die folgenden Escapesequenzen verwenden:

-   Wenn eine Vorlage Texttag eine gerade Anzahl von Escapezeichen vorangestellt wird (\\) Zeichen von der Vorlage Parser wird die Hälfte der Escape-Zeichen und der Folge als Vorlage Texttag enthalten. Z. B. wenn in der Vorlage "Text" vier-Escape-Zeichen vorhanden sind, es werden zwei "\\" Zeichen in der generierten Datei.

-   Wenn die Vorlage Texttag eine ungerade Anzahl von Escapezeichen vorangestellt wird (\\) Zeichen d. h., der Vorlagenparser enthält die Hälfte der der "\\"-Zeichen sowie das Tag selbst (\<# or #>). Das Tag ist nicht als Vorlage Texttag werden.

-   Wenn ein Escapezeichen (\\) Zeichen vorkommt, wird an anderer Stelle in beliebiger Reihenfolge als die, in dem sie ein Steuerzeichen noch ein öffnendes ohne schließendes Anführungszeichen (nur c#) versieht, wird das Zeichen direkt ausgegeben werden.

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)