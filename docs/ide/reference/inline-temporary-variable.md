---
title: Ersetzen einer temporären Variable durch ihren Wert
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: aa329dd3fe7d01046c35be9829aed4ca4519c3e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909033"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Inlinesetzen eines temporären Variablenrefactorings

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung:** Hiermit können Sie eine temporäre Variable entfernen und diese stattdessen durch ihren Wert ersetzen.

**Hintergrund:** Durch die Verwendung der temporären Variable ist der Code schwieriger zu verstehen.

**Vorteile**: Durch das Entfernen einer temporären Variablen kann die Lesbarkeit des Codes verbessert werden.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie die inline zu setzende temporäre Variable, oder platzieren Sie den Textcursor in die Variable:

   - C#:

       ![Hervorgehobener Code – C#](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Hervorgehobener Code – Visual Basic](media/inline-highlight-vb.png)

2. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
      - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** aus.

3. Wählen Sie im Popupvorschaufenster **Inline temporär variabel** aus.

   Die Variable wird entfernt und sofort durch ihren Wert ersetzt.

   - C#:

      ![Ergebnis des Inlinevorgangs in C#](media/inline-result-cs.png)

   - Visual Basic:

      ![Ergebnis des Inlinevorgangs in Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)