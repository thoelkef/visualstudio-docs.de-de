---
title: Refactoring eines Felds zu einer Eigenschaft in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 78d2c33002e59eab1b6e8605092a74d9995453a8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="encapsulate-a-field-refactoring"></a>Refactoring des Kapselns eines Felds

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung**: Sie können ein Feld in eine Eigenschaft umwandeln und alle Verwendungen dieses Felds auf die neu erstellte Eigenschaft aktualisieren.

**Hintergrund**: Sie möchten ein Feld in eine Eigenschaft verschieben und alle Verweise auf dieses Feld aktualisieren.

**Vorteile**: Sie möchten anderen Klassen Zugriff auf ein Feld gewähren, die Klassen sollen aber nicht direkt zugreifen können.  Indem Sie das Feld mit einer Eigenschaft umschließen, können Sie z.B. Code schreiben, um den Wert zu überprüfen, der zugewiesen wird.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie den Namen des zu kapselnden Felds, oder platzieren Sie den Textcursor in den Namen:

   - C#:

    ![Hervorgehobener Code – C#](media/encapsulate-highlight-cs.png)

   - Visual Basic:

    ![Hervorgehobener Code – Visual Basic](media/encapsulate-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
     - Drücken Sie **STRG+R** und dann **STRG+E**.  (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
     - Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster einen der Einträge für **Feld kapseln** aus.
   - **Maus**
     - Wählen Sie **Bearbeiten > Umgestalten > Feld kapseln** aus.
     - Klicken Sie mit der rechten Maustaste auf den Code, wählen Sie das Menü **Schnellaktionen und Refactorings** aus, und wählen Sie im Popupvorschaufenster einen der Einträge für **Feld kapseln** aus.

   Auswahl | description
   --------- | -----------
   **Feld kapseln (und Eigenschaft verwenden)** | Kapselt das Feld mit einer Eigenschaft und aktualisiert alle Verwendungen des Felds so, dass die generierte Eigenschaft verwendet wird.
   **Feld kapseln (Feld jedoch weiterhin verwenden)** | Kapselt das Feld mit einer Eigenschaft, lässt aber alle Verwendungen des Felds unverändert.

   Die Eigenschaft wird erstellt, und sofern ausgewählt, werden Verweise auf das Feld aktualisiert.

   > [!TIP]
   > Verwenden Sie den Link **Vorschau der Änderungen** im Popupfenster, um [vor einer endgültigen Änderung das Ergebnis zu sehen](../../ide/preview-changes.md).

   - C#:

    ![Ergebnis vom Kapseln der Eigenschaft – C#](media/encapsulate-result-cs.png)

   - Visual Basic:

    ![Ergebnis vom Kapseln der Eigenschaft – Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Refactoring](../refactoring-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)