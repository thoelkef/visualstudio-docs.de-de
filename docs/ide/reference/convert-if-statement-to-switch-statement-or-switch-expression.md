---
title: Konvertieren der if-Anweisung in eine switch-Anweisung
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 93ad96809c77d5644b13e6221a41f0b182fb448f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094134"
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
3. Wählen Sie eine der folgenden beiden Optionen aus: 

    Klicken Sie auf **In switch-Anweisung konvertieren**.

   ![Konvertieren von if-Anweisung in switch-Anweisung](media/convert-if-to-switch-statement.png) 

    Klicken Sie auf **In switch-Ausdruck konvertieren**. 

    ![Konvertieren von if-Anweisung in switch-Ausdruck](media/convert-if-to-switch-expression.png) 

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
