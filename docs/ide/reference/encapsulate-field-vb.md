---
title: Umgestalten eines Felds zu einer Eigenschaft in Visual Basic | Microsoft-Dokumentation
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 010a297745ed6028f7ee127fffc210097d6d26f5
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2018
---
# <a name="encapsulate-a-field-in-visual-basic"></a>Kapseln eines Felds in Visual Basic

**Beschreibung**: Sie können ein Feld in eine Eigenschaft umwandeln und alle Verwendungen dieses Felds auf die neu erstellte Eigenschaft aktualisieren.

**Hintergrund**: Sie möchten ein Feld in eine Eigenschaft verschieben und alle Verweise auf dieses Feld aktualisieren.  

**Vorteile**: Sie möchten anderen Klassen Zugriff auf ein Feld gewähren, die Klassen sollen aber nicht direkt zugreifen können.  Indem Sie das Feld mit einer Eigenschaft umschließen, können Sie z.B. Code schreiben, um den Wert zu überprüfen, der zugewiesen wird.

**Vorgehensweise**:

1. Markieren Sie den Namen des zu kapselnden Felds, oder platzieren Sie den Textcursor in den Namen:

   ![Markierter Code](media/encapsulate-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+R** und dann **STRG+E**.  (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster einen der Einträge für **Feld kapseln** aus.
   * **Maus**
     * Wählen Sie **Bearbeiten > Umgestalten > Feld kapseln** aus.
     * Klicken Sie mit der rechten Maustaste auf den Code, wählen Sie das Menü **Schnellaktionen und Refactorings** aus, und wählen Sie im Popupvorschaufenster einen der Einträge für **Feld kapseln** aus.

   Auswahl | description
   --------- | -----------
   **Feld kapseln (und Eigenschaft verwenden)** | Kapselt das Feld mit einer Eigenschaft und aktualisiert alle Verwendungen des Felds so, dass die generierte Eigenschaft verwendet wird.
   **Feld kapseln (Feld jedoch weiterhin verwenden)** | Kapselt das Feld mit einer Eigenschaft, lässt aber alle Verwendungen des Felds unverändert.

   Die Eigenschaft wird sofort erstellt, und Verweise auf das Feld werden aktualisiert (sofern ausgewählt).

   > [!TIP]
   > Verwenden Sie den Link [**Vorschau der Änderungen**](../../ide/preview-changes.md) im Popupfenster, um vor einer endgültigen Änderung das Ergebnis zu sehen.

   ![Kapseln der Eigenschaft – Ergebnis](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Refactoring](../refactoring-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)