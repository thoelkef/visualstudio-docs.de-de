---
title: Konvertieren der if-Anweisung in eine switch-Anweisung
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cb0c06fe0493f973ea9cf0a566ffda45a49eeeff
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77283460"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Konvertieren der if-Anweisung in eine switch-Anweisung

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Konvertieren einer if-Anweisung in eine [switch-Anweisung](/dotnet/csharp/language-reference/keywords/switch) oder in einen C#-8.0-[switch-Ausdruck](/dotnet/csharp/whats-new/csharp-8#switch-expressions)

**Hintergrund:** Sie möchten eine `if`-Anweisung in einen `switch`-Ausdruck oder einen `switch`-Ausdruck und umgekehrt konvertieren. 

**Vorteile**: Wenn Sie nur `if`-Ausdrücke verwenden, ermöglicht dieses Refactoring einen einfachen Übergang zu `switch`-Anweisungen oder `switch`-Ausdrücken.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihren Cursor im Schlüsselwort `if`.
2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Klicken Sie auf **In switch-Anweisung konvertieren**.

   ![Konvertieren der if-Anweisung in eine switch-Anweisung](media/convert-if-statement-to-switch-statement-or-switch-expression.png) 

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
