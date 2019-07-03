---
title: switch-Anweisung in switch-Ausdruck konvertieren
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: ecb7750301101a2607c17e68b5e919623a03caba
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67329073"
---
# <a name="convert-switch-statement-to-switch-expression"></a>switch-Anweisung in switch-Ausdruck konvertieren

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Hiermit wird eine [switch-Anweisung](/dotnet/csharp/language-reference/keywords/switch) in einen [switch-Ausdruck](/dotnet/csharp/whats-new/csharp-8#switch-expressions) von C# 8.0 konvertiert.

**Hintergrund:** Sie möchten eine `switch`-Anweisung in einen `switch`-Ausdruck und umgekehrt konvertieren. 

**Vorteile**: Wenn Sie nur Ausdrücke verwenden, ermöglicht dieses Refactoring einen einfachen Wechsel von herkömmlichen `switch`-Anweisungen.

## <a name="how-to"></a>Vorgehensweise

1. Legen Sie in der Projektdatei die [Sprachversion auf „Vorschau“ fest](/dotnet/csharp/language-reference/configure-language-version#set-the-language-version-in-visual-studio), da `switch`-Ausdrücke ein neues C# 8.0-Feature sind.
2. Platzieren Sie den Cursor im Schlüsselwort `switch`, und drücken Sie **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
3. Wählen Sie **switch-Anweisung in switch-Ausdruck konvertieren** aus.

   ![switch-Anweisung in switch-Ausdruck konvertieren](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
