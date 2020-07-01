---
title: Vervollständigung von DateTime und TimeSpan über das IntelliSense-Menü
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: eaa8a344e46c031b37b52106ba9aef25dac59b0c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290838"
---
# <a name="datetime-and-timespan-completion-through-intellisense-menu"></a>Vervollständigung von DateTime und TimeSpan über das IntelliSense-Menü

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Vervollständigung der Zeichenfolgenliterale DateTime und TimeSpan über das IntelliSense-Menü.

**Hintergrund:** Sie möchten die Zeichenfolgenliterale DateTime und TimeSpan schreiben. IntelliSense bietet Ihnen eine einfache Vervollständigung und Erklärung, was die einzelnen Zeichen bedeuten. 

**Vorteile**: Sich an DateTime-Formate zu erinnern ist schwierig, weshalb IntelliSense Ihnen beim Schreiben helfen kann.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor innerhalb des Zeichenfolgenliterals DateTime oder TimeSpan.
2. Drücken Sie **STRG**+**LEERTASTE**, um das Menü **IntelliSense** zu öffnen.
3. Wählen Sie das Zeichen, das Sie hinzufügen möchten.

   ![Vervollständigung von DateTime durch IntelliSense](media/datetime-completion.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
