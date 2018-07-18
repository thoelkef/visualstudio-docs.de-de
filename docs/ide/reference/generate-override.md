---
title: Generieren einer Methodenüberschreibung in Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c366ce3d393e639590e5d45fc55ad5523be920b6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31943865"
---
# <a name="generate-an-override-in-visual-studio"></a>Generieren einer Überschreibung in Visual Studio

Diese Codegenerierung gilt für:

- C#

- Visual Basic

**Beschreibung**: Sie können sofort Code für eine Methode generieren, die von einer Basisklasse überschrieben werden kann.

**Hintergrund**: Sie möchten eine Basisklassenmethode überschreiben und die Signatur automatisch generieren.

**Vorteile**: Sie könnten die Methodensignatur selbst schreiben – dieses Feature generiert die Signatur jedoch automatisch.

## <a name="how-to"></a>Vorgehensweise

1. Schreiben Sie `override` in C# oder `Overrides` in Visual Basic, gefolgt von einem Leerzeichen, an der Stelle, an der Sie eine Überschreibungsmethode einfügen möchten.

   - C#:

    ![Überschreiben mit IntelliSense in C#](media/override-intellisense-cs.png)

   - Visual Basic:

    ![Überschreiben mit IntelliSense in Visual Basic](media/override-intellisense-vb.png)

1. Wählen Sie die zu überschreibende Methode aus der Basisklasse.

   > [!TIP]
   > - Verwenden Sie das Eigenschaftssymbol, ![Eigenschaftssymbol](media/override-property-cs.png) um Eigenschaften in der Liste anzuzeigen oder auszublenden.
   > - Verwenden Sie das Methodensymbol, ![Methodensymbol](media/override-method-cs.png) um Methoden in der Liste anzuzeigen oder auszublenden.

   Die ausgewählte Methode oder Eigenschaft wird der Klasse als Überschreibung hinzugefügt und steht für die Implementierung zur Verfügung.

   - C#:

      ![Ergebnis der Überschreibung in C#](media/override-result-cs.png)

   - Visual Basic:

      ![Ergebnis der Überschreibung in Visual Basic](media/override-result-vb.png)

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)