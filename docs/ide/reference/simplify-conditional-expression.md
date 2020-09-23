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
ms.openlocfilehash: 0242c8c89848e3e76673ddfbca8a27c20605048d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810349"
---
# <a name="simplify-conditional-expression-refactoring"></a>Refactoring: Vereinfachen bedingter Ausdrücke

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Ermöglicht das Vereinfachen eines [bedingten Ausdrucks](/dotnet/csharp/language-reference/operators/conditional-operator).

**Hintergrund:** Sie möchten unnötigen Code entfernen, um mehr Klarheit zu schaffen.

**Vorteile**: Das Vereinfachen eines bedingten Ausdrucks kann zu einer übersichtlicheren und präziseren Syntax führen. Dieses Refactoringtool führt die Aufgaben automatisch aus, anstatt dass Sie sie manuell ausführen müssen.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie Ihren Cursor auf dem bedingten Ausdruck:

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

3. Wählen Sie **Bedingten Ausdruck vereinfachen aus**.

    ![Vereinfachen bedingter Ausdrücke](media/simplify-conditional-expression.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)