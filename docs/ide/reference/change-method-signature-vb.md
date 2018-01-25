---
title: Umgestalten einer Methodensignatur in Visual Basic | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: daee27902bd602dfe1d67533ce45f42f44a3aba4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="change-a-method-signature-in-visual-basic"></a>Ändern einer Methodensignatur in Visual Basic

**Beschreibung**: Hiermit können Sie Parameter einer Methode entfernen oder deren Reihenfolge ändern.

**Hintergrund**: Sie möchten einen Methodenparameter verschieben oder entfernen, der gegenwärtig an vielen Stellen verwendet wird.  

**Vorteile**: Sie könnten die Parameter manuell entfernen und neu anordnen und anschließend alle Aufrufe dieser Methode suchen und nacheinander ändern, was jedoch Fehler verursachen könnte.  Bei diesem Refactoringtool wird der Task automatisch ausgeführt.

**Vorgehensweise**:

1. Markieren Sie den Namen der zu ändernden Methode oder eines ihrer Vorkommen, oder platzieren Sie den Textcursor in den Namen:

   ![Markierter Code](media/changesignature-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+R** und dann **STRG+V**.  (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Signatur ändern** aus.
   * **Maus**
     * Wählen Sie **Bearbeiten > Umgestalten > Parameter entfernen** aus.
     * Wählen Sie **Bearbeiten > Umgestalten > Parameter neu anordnen** aus.
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Signatur ändern** aus.

1. Mit den Schaltflächen auf der rechten Seite im angezeigten Dialogfeld **Signatur ändern** können Sie die Methodensignatur ändern:

   ![Dialogfeld „Signatur ändern“](media/changesignature-dialog-vb.png)

   | Schaltfläche | description
   | ------ | ---
   | **Nach oben/unten** | Den ausgewählten Parameter in der Liste nach oben oder nach unten verschieben
   | **Entfernen**  | Den ausgewählten Parameter aus der Liste entfernen
   | **Wiederherstellen** | Den ausgewählten, durchgestrichenen Parameter in der Liste wiederherstellen

   > [!TIP]
   > Aktivieren Sie das Kontrollkästchen [**Vorschau der Verweisänderungen**](../../ide/preview-changes.md), um vor einer endgültigen Änderung das Ergebnis zu sehen.

1. Wenn Sie fertig sind, klicken Sie auf die Schaltfläche **OK**, um die Änderungen zu übernehmen.

   ![Ergebnis der Aktion zum Ändern einer Signatur](media/changesignature-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Refactoring](../refactoring-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)