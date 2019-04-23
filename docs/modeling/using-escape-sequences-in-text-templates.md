---
title: Verwenden von Escapesequenzen in Textvorlagen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c88c9c8769051724855d292bfefb56f69cb8dee
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053168"
---
# <a name="using-escape-sequences-in-text-templates"></a>Verwenden von Escapesequenzen in Textvorlagen
Können Sie Escapesequenzen in Textvorlagen generieren Sie Text in Template Tags und (in c# nur Code)-Steuerelement-Escape-Zeichen und Anführungszeichen.

 Um öffnende und schließende Tags für einen standard-Codeblock in die Ausgabedatei drucken, mit Escapezeichen versehen Sie die Tags wie folgt:

```
\<# ... \#>
```

 Sie können auch mit anderen Text-Vorlage Richtlinie und Code-Block Tags vornehmen.

 Enthält ein TextBlock Zeichenfolgen, die Text-in Template Tags als Escapezeichen verwendet, können Sie die folgenden Escapesequenzen verwenden:

- Wenn Sie eine Vorlage Texttag eine gerade Anzahl von Escapezeichen vorangestellt ist (\\) Zeichen von der Vorlage Parser wird die Hälfte der Escape-Zeichen und die Sequenz als Text Template-Tag enthalten. Z. B. wenn vier Escape-Zeichen in der Textvorlage vorhanden sind, stehen zwei "\\" Zeichen in der generierten Datei.

- Wenn eine ungerade Anzahl von Escapezeichen Vorlagentags Text vorangestellt ist (\\) Zeichen der Vorlagenparser umfasst die Hälfte der der "\\"-Zeichen sowie das Tag selbst (\<# oder #>). Das Tag ist nicht als Text Template-Tag werden.

- Wenn ein Escapezeichen (\\) Zeichen wird angezeigt, an anderer Stelle in beliebiger Reihenfolge als die, in dem sie ein Steuerzeichen noch ein öffnendes ohne schließendes Anführungszeichen (nur c#) versieht, wird das Zeichen direkt ausgegeben werden.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Generieren von Vorlagen aus Vorlagen mithilfe von Escapesequenzen](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)