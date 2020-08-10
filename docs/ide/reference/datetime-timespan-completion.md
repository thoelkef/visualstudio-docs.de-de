---
title: Vervollständigung von DateTime und TimeSpan über das IntelliSense-Menü
ms.date: 07/31/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 36b6d5440e532653845638f87f7f1d7066af6ba3
ms.sourcegitcommit: 43df639b2cd99200f725a8ebb941477481a6f0ff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2020
ms.locfileid: "87471552"
---
# <a name="datetime-and-timespan-completion-through-intellisense-menu"></a>Vervollständigung von DateTime und TimeSpan über das IntelliSense-Menü

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Vervollständigung der Zeichenfolgenliterale und Formatzeichenfolgen für DateTime und TimeSpan über das IntelliSense-Menü.

**Hintergrund:** Sie möchten die Zeichenfolgenliterale und Formatzeichenfolgen für DateTime und TimeSpan schreiben. IntelliSense bietet Ihnen eine einfache Vervollständigung und Erklärung, was die einzelnen Zeichen bedeuten. 

**Vorteile**: Sich an DateTime-Formate zu erinnern ist schwierig, weshalb IntelliSense Ihnen beim Schreiben helfen kann.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in der Formatzeichenfolge für DateTime oder TimeSpan.
2. Drücken Sie **STRG**+**LEERTASTE**, um das Menü **IntelliSense** zu öffnen.
3. Wählen Sie das Zeichen, das Sie hinzufügen möchten.

   ![Vervollständigung von DateTime durch IntelliSense](media/datetime-completion.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
