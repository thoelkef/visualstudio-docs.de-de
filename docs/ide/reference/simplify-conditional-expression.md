---
title: Vereinfachen bedingter Ausdrücke
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d0571c01217441d4a39fbfe6fb58ccfe95fd0c5a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290864"
---
# <a name="simplify-conditional-expression-refactoring"></a>Refactoring: Vereinfachen bedingter Ausdrücke

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Ermöglicht das Vereinfachen eines [bedingten Ausdrucks](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).

**Hintergrund:** Sie möchten unnötigen Code entfernen, um mehr Klarheit zu schaffen.

**Vorteile**: Das Vereinfachen eines bedingten Ausdrucks kann zu einer übersichtlicheren und präziseren Syntax führen. Dieses Refactoringtool führt die Aufgaben automatisch aus, anstatt dass Sie sie manuell ausführen müssen.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihren Cursor auf dem bedingten Ausdruck:

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

3. Wählen Sie **Bedingten Ausdruck vereinfachen aus**.

    ![Vereinfachen bedingter Ausdrücke](media/simplify-conditional-expression.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)