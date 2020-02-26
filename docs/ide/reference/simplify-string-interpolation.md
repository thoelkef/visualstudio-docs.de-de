---
title: Vereinfachen der Zeichenfolgeninterpolation
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 15f034b0ecf46e19681f3b74e4137a2de9e9d950
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77283436"
---
# <a name="simplify-string-interpolation-refactoring"></a>Refactoring zur Vereinfachung von Zeichenfolgeninterpolationen

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Ermöglicht Ihnen das Vereinfachen einer [Zeichenfolgeninterpolation](https://docs.microsoft.com/dotnet/csharp/tutorials/string-interpolation)

**Hintergrund:** Sie verfügen über eine Zeichenfolgeninterpolation, die vereinfacht werden kann.

**Vorteile**: Das Vereinfachen einer Zeichenfolgeninterpolation kann zu einer übersichtlicheren und präziseren Syntax führen. Dieses Refactoringtool führt die Aufgaben automatisch aus, anstatt dass Sie sie manuell ausführen müssen.

## <a name="how-to"></a>Vorgehensweise

1. Zeigen Sie mit dem Cursor auf die Zeichenfolgeninterpolation:

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

3. Klicken Sie auf **Interpolation vereinfachen**.

    ![Vereinfachen der Zeichenfolgeninterpolation](media/simplify-string-interpolation.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)