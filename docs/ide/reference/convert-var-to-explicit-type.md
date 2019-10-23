---
title: Refactoring von Code zum Ersetzen von var durch einen expliziten Typ
ms.date: 05/15/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 566d064ac0ac1b9c48ee8e75697cef39b2ec4ee1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661686"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refactoring zum Ersetzen von var durch einen expliziten Typ

Mithilfe dieses Refactorings können Sie [var](/dotnet/csharp/language-reference/keywords/var) in einer lokalen Variablendeklaration mit einem expliziten Typ ersetzen.

Dieses Refactoring gilt für:

- C#

## <a name="why-to-use-an-explicit-type"></a>Gründe für die Verwendung eines expliziten Typs

Hier finden Sie einige Gründe für das Deklarieren einer Variable mit einem expliziten Typ:

- Bessere Lesbarkeit des Codes

- Wenn die Variable nicht in der Deklaration initialisiert werden soll

[var](/dotnet/csharp/language-reference/keywords/var) muss jedoch verwendet werden, wenn eine Variable mit einem anonymen Typ initialisiert wird und wenn Sie zu einem späteren Zeitpunkt auf die Eigenschaften des Objekts zugreifen möchten. Weitere Informationen finden Sie unter [Implizit typisierte lokale Variablen (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Verwendungsweise

1. Fügen Sie die Einfügemarke in das `var`-Schlüsselwort ein.

1. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , oder klicken Sie auf den Schraubendreher ![Schraubendrehersymbol](../media/screwdriver-icon.png) im Randbereich der Codedatei.

   ![Verwenden des Menüs für schnelle Aktionen für den expliziten Typ](media/use-explicit-type.png)

1. Wählen Sie **Expliziten Typ verwenden** aus. Wählen Sie alternativ **Vorschau der Änderungen anzeigen** aus, um das Dialogfeld [Vorschau der Änderungen](../../ide/preview-changes.md) anzuzeigen. Klicken Sie dann auf **Anwenden**.

## <a name="see-also"></a>Siehe auch

- [Implizit typisierte Variablen (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)