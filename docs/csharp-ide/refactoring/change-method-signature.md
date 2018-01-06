---
title: "Ändern der Methodensignatur - Umgestaltung (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: b4f45f9d-9c8f-46ae-99f7-7705c6d90b6e
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 6344a30b5772ffa23c09baa4f38a4478d907cc9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="change-a-method-signature-in-c"></a>Ändern der Signatur einer Methode in c# #
**Was:** ermöglicht Ihnen das Entfernen oder Ändern der Reihenfolge der Parameter einer Methode.

**Wann:** verschieben oder entfernen die Parameter der Methode, die zurzeit in einer Vielzahl von Standorten verwendet werden sollen.  

**Grund:** Sie konnte manuell entfernen und die Parameter neu anordnen und dann aller Aufrufe dieser Methode finden und ändern Sie sie einzeln- jedoch, die zu Fehlern führen.  Dieses refactoring-Tool wird automatisch den Task ausgeführt werden.

**Vorgehensweise:**

1. Markieren Sie, oder platzieren Sie den Textcursor innerhalb der Name der die Methode zum Ändern oder eines seiner Verwendungen:

   ![Hervorgehobene code](media/changesignature_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG + R**, klicken Sie dann **STRG + V**.  (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **Signatur ändern** im Popupmenü Fenster Vorschau.
   * **Maus**
     * Wählen Sie **Bearbeiten > Umgestalten > Entfernen Sie die Parameter**.
     * Wählen Sie **Bearbeiten > Umgestalten > Parameter neu anordnen**.
     * Mit der rechten Maustaste in des Codes, wählen Sie die **Schnellaktionen und Refactorings** Menü **Signatur ändern** im Popupmenü Fenster Vorschau.

1. In der **ändern Signatur** oben angezeigten Dialogfeld können Sie die Schaltflächen auf der rechten Seite so ändern Sie die Signatur der Methode:

   ![Ändern der Signatur-Dialogfeld](media/changesignature_dialog.png)

   | Schaltfläche | Beschreibung
   | ------ | ---
   | **Nach oben/unten** | Verschiebt den ausgewählten Parameter nach oben oder unten der Liste
   | **Entfernen**  | Entfernt den ausgewählten Parameter aus der Liste
   | **Stellen Sie wieder her** | Die Liste der ausgewählten, durchgestrichene Wiederherstellungsparameter

   > [!TIP]
   > Verwenden der [ **Vorschau der Änderungen Verweis** ](../../ide/preview-changes.md) Kontrollkästchen, um zu sehen, was das Ergebnis sein wird, bevor Sie endgültig.

1. Wenn Sie fertig sind, drücken Sie die **OK** Schaltfläche, um die Änderungen vornehmen.

   ![Ergebnis der Signatur](media/changesignature_result.png)

## <a name="see-also"></a>Siehe auch  
[Refactoring (C#)](../refactoring-csharp.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)