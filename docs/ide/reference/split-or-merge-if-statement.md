---
title: Teilen oder Zusammenführen von if-Anweisungen
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 405ccd4bc0197ce06aa14982a16dc02f6d13a537
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160736"
---
# <a name="split-or-merge-if-statements"></a>Teilen oder Zusammenführen von if-Anweisungen

Dieses Refactoring gilt für:

- C#

**Beschreibung:** **Beschreibung:** Teilen oder Zusammenführen von [if](/dotnet/csharp/language-reference/keywords/if-else)-Anweisungen

**Hintergrund:** Sie möchten eine `if`-Anweisung, die die Operatoren `&&` oder `||` verwendet, in eine geschachtelte `if`-Anweisung teilen oder eine `if`-Anweisung mit einer äußeren `if`-Anweisung zusammenführen.

**Vorteile**: Dies ist eine Frage des bevorzugten Stils.  

## <a name="how-to"></a>Vorgehensweise

Wenn Sie die `if`-Anweisung teilen möchten:

1. Platzieren Sie Ihren Cursor in der `if`-Anweisung des Operators `&&` oder `||`.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

    ![Teilen von if-Anweisungen](../media/split-if-statement.png)

3. Wählen Sie **In geschachtelte if-Anweisungen teilen** aus.

    ![Teilen von if-Anweisungen abgeschlossen](../media/split-if-statement-complete.png)

Wenn Sie die innere `if`-Anweisung mit der äußeren `if`-Anweisung zusammenführen möchten: 

1. Platzieren Sie Ihren Cursor im inneren Schlüsselwort `if`.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

    ![Zusammenführen von if-Anweisungen](../media/merge-if-statement.png)

3. Wählen Sie **Mit äußerer if-Anweisung zusammenführen**.

    ![Zusammenführen von if-Anweisungen abgeschlossen](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)