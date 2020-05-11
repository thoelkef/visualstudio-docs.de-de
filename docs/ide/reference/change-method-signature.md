---
title: Ändern der Methodensignatur
description: Entfernen von Parametern einer Methode oder Ändern deren Reihenfolge Klicken Sie mit der rechten Maustaste auf eine Methode, wählen Sie „Schnelle Aktionen“ und anschließend „Refactorings“ aus, und klicken Sie auf „Signatur ändern“.
ms.date: 01/26/2018
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 97c03c798732b5d722b2dc49f3ec7ffa490b4f06
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "68711264"
---
# <a name="change-a-method-signature-refactoring"></a>Ändern einer Methodensignatur durch Refactoring

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung**: Hiermit können Sie Parameter einer Methode entfernen oder deren Reihenfolge ändern.

**Hintergrund**: Sie möchten einen Methodenparameter verschieben oder entfernen, der gegenwärtig an vielen Stellen verwendet wird.

**Vorteile**: Sie könnten die Parameter manuell entfernen und neu anordnen und anschließend alle Aufrufe dieser Methode suchen und nacheinander ändern, was jedoch Fehler verursachen könnte.  Bei diesem Refactoringtool wird der Task automatisch ausgeführt.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie den Namen der zu ändernden Methode oder eines ihrer Vorkommen, oder platzieren Sie den Textcursor in den Namen:

   - C#:

       ![Hervorgehobener Code – C#](media/changesignature-highlight-cs.png)

   - VB:

       ![Hervorgehobener Code in Visual Basic](media/changesignature-highlight-vb.png)

2. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie **STRG+R** und dann **STRG+V**.  (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Signatur ändern** aus.
   - **Maus**
      - Wählen Sie **Bearbeiten > Umgestalten > Parameter entfernen** aus.
      - Wählen Sie **Bearbeiten > Umgestalten > Parameter neu anordnen** aus.
      - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Signatur ändern** aus.

3. Mit den Schaltflächen auf der rechten Seite im angezeigten Dialogfeld **Signatur ändern** können Sie die Methodensignatur ändern:

   ![Dialogfeld „Signatur ändern“](media/changesignature-dialog-cs.png)

   | Schaltfläche | Beschreibung
   | ------ | ---
   | **Nach oben/unten** | Den ausgewählten Parameter in der Liste nach oben oder nach unten verschieben
   | **Entfernen** | Den ausgewählten Parameter aus der Liste entfernen
   | **Wiederherstellen** | Den ausgewählten, durchgestrichenen Parameter in der Liste wiederherstellen

   > [!TIP]
   > Aktivieren Sie das Kontrollkästchen **Vorschau der Verweisänderungen**, um vor einer endgültigen Änderung das [Ergebnis zu sehen](../../ide/preview-changes.md).

4. Wenn Sie fertig sind, klicken Sie auf die Schaltfläche **OK**, um die Änderungen zu übernehmen.

   - C#:

      ![Ergebnis der Signaturänderung in C#](media/changesignature-result-cs.png)

   - Visual Basic:

      ![Ergebnis der Signaturänderung in Visual Basic](media/changesignature-result-vb.png)

## <a name="see-also"></a>Weitere Informationen

- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)