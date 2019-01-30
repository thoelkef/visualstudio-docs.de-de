---
title: Schnelle Aktionen, Glühbirnen und Schraubendreher
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d1d129e1a7448e814f01c5a60f282fec028ee4a2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982220"
---
# <a name="quick-actions"></a>Schnelle Aktionen

Mit schnellen Aktionen können Sie ganz leicht Code mit einer einzelnen Aktion umgestalten, generieren oder anderweitig ändern. Schnelle Aktionen sind für C#-, [C++](/cpp/ide/writing-and-refactoring-code-cpp)- und Visual Basic-Codedateien verfügbar. Einige der Aktionen sind für eine Sprache spezifisch, während andere für alle Sprachen gelten.

Schnelle Aktionen können für Folgendes verwendet werden:

- Anwenden einer Codefehlerbehebung für eine Verletzung einer Regel des [Codeanalysetools](../code-quality/roslyn-analyzers-overview.md)
- [Unterdrücken](../code-quality/use-roslyn-analyzers.md) einer Verletzung einer Regel des Codeanalysetools
- Anwenden eines Refactorings (z.B. [Inlinesetzen einer temporären Variable](../ide/reference/inline-temporary-variable.md))
- Generieren von Code (z.B. [Einführen einer lokalen Variable](../ide/reference/introduce-local-variable.md))

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden sie unter [Refactoring (Visual Studio für Mac)](/visualstudio/mac/refactoring).

Schnelle Aktionen können mithilfe der Glühbirne ![Glühbirnensymbol](media/light-bulb-icon.png), des Schraubendrehers ![Schraubendrehersymbol](media/screwdriver-icon.png) oder durch Drücken der Tasten **STRG**+**.** angewendet werden, wenn Ihr Cursor sich auf einer Codezeile befindet, für die eine Aktion verfügbar ist. Es wird eine Glühbirne mit einem roten Warnzeichen ![Glühbirnensymbol](media/error-light-bulb-icon.png) angezeigt, was auf einen Fehler hindeutet, und in Visual Studio ist für diesen Fehler eine Problemlösung verfügbar.

Für jede Sprache können Drittanbieter benutzerdefinierte Diagnosen und Empfehlungen bereitstellen, beispielsweise als Bestandteil eines SDKs. Anhand dieser Regeln leuchten die Visual Studio-Glühbirnen dann auf.

## <a name="icons"></a>Symbole

Das Symbol, das angezeigt wird, wenn eine schnelle Aktion verfügbar ist, erläutert den Typ der verfügbaren Fehlerkorrektur oder des Refactorings. Der *Schraubendreher* ![Schraubendrehersymbol](media/screwdriver-icon.png) gibt nur an, dass Aktionen für die Änderung des Codes verfügbar sind, Sie diese jedoch nicht unbedingt verwenden müssen. Die *gelbe Glühbirne* ![Symbol für gelbe Glühbirne](media/light-bulb-icon.png) zeigt, dass Aktionen verfügbar sind, die Sie *durchführen sollten*, um Ihren Code zu verbessern. Die *Glühbirne mit Warnzeichen* ![Symbol für Glühbirne mit Warnzeichen](media/error-light-bulb-icon.png) zeigt, dass eine Aktion verfügbar ist, die einen Fehler in Ihrem Code beheben kann.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>So zeigen Sie eine Glühbirne oder einen Schraubendreher an

- Wenn eine Fehlerkorrektur verfügbar ist, erscheinen Glühbirnen spontan, wenn Sie mit der Maus auf die Position eines Fehlers zeigen.

   ![Glühbirne mit Mauszeigerbewegung](../ide/media/vs2015_lightbulb_hover.png)

- Glühbirnen und Schraubendreher werden im linken Rand des Editors angezeigt, wenn Sie das Caretzeichen in eine Codezeile verschieben, für die eine schnelle Aktion verfügbar ist.

- Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um eine Liste verfügbarer schneller Aktionen und Refactorings anzuzeigen.

## <a name="to-see-potential-fixes"></a>So zeigen Sie potenzielle Fehlerbehebungen an

Klicken Sie entweder neben der Glühbirne auf den Pfeil nach unten oder auf den Link **Mögliche Korrekturen anzeigen**, um eine Liste der verfügbaren schnellen Aktionen anzuzeigen.

![Erweiterte Glühbirne](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Siehe auch

- [Codegenerierung in Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Häufige schnelle Aktionen](../ide/common-quick-actions.md)
- [Codeformate und Schnellaktionen](../ide/code-styles-and-quick-actions.md)
- [Schreiben und Refactoring von Code (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refactoring (Visual Studio für Mac)](/visualstudio/mac/refactoring)