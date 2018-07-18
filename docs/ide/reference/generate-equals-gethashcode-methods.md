---
title: Generieren der Überschreibungsmethoden „Equals“ und „GetHashCode“ in Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: cdbb5273d046be8f11cc2fbc4a03ed6767a31e00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945310"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generieren der Überschreibungsmethoden „Equals“ und „GetHashCode“ in Visual Studio

Diese Codegenerierung gilt für:

- C#

**Beschreibung**: Ermöglicht das Generieren von **Equals**- und **GetHashCode**-Methoden.

**Hintergrund**: Generieren Sie diese Überschreibungsmethoden, wenn Sie einen Typ haben, der durch ein Feld oder mehrere Felder verglichen werden soll, anstelle des Objektspeicherorts im Arbeitsspeicher.

**Vorteile**:

- Wenn Sie einen Werttyp implementieren, sollten Sie erwägen, die **Equals**-Methode zu überschreiben, um eine bessere Leistung als mit der Standardimplementierung der Equals-Methode in ValueType zu erzielen.

- Wenn Sie einen Verweistyp implementieren, sollten Sie erwägen, die **Equals**-Methode zu überschreiben, wenn der Typ wie ein Basistyp aussieht, z.B. Point, String, BigNumber usw.

- Überschreiben Sie die **GetHashCode**-Methode, damit ein Typ in einer Hashtabelle ordnungsgemäß funktioniert. Informieren Sie sich weiter über [Gleichheitsoperatoren](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in Ihre Typdeklaration.

   ![Markierter Code](media/overrides-highlight-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
     - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
     - Führen Sie einen Rechtsklick durch, und klicken Sie auf das Menü **Schnellaktionen und Refactorings**.
     - Klicken Sie auf die Schaltfläche ![Glühbirnensymbol,](media/bulb-cs.png) das am linken Rand angezeigt wird, sofern der Textcursor bereits in der Zeile mit der Typdeklaration platziert ist.

   ![Generieren von Überschreibungen – Vorschau](media/overrides-preview-cs.png)

1. Klicken Sie im Dropdownmenü auf **„Equals(object)“ generieren** oder **„Equals“ und „GetHashCode“ generieren**.

1. Wählen Sie die Mitglieder, für die Sie die Methoden generieren wollen, im Dialogfeld **Member auswählen** aus:

    ![Generieren von Überschreibungen – Dialogfeld](media/overrides-dialog-cs.png)

    > [!TIP]
    > In diesem Dialogfeld können Sie auch die Generierung von Operatoren auswählen, indem Sie die entsprechenden Kontrollkästchen unterhalb der Memberliste verwenden.

   Die Überschreibungsmethoden „Equals“ und „GetHashCode“ werden mit Standardimplementierungen generiert.

   ![Ergebnis der Aktion zum Generieren einer Methode](media/overrides-result-cs.png)

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)