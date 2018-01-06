---
title: Rename - Umgestaltung (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abf1565b-c7b7-4d45-b3d3-a438a836c70e
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.rename
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: da85803adf3de8afa0912a1f47e2b474952df51d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="rename-a-code-symbol-in-visual-basic"></a>Umbenennen eines Symbols Code in Visual Basic
**Was:** können Sie die Bezeichner für die Code-Symbolen, z. B. Felder, lokale Variablen, Methoden, Namespaces, Eigenschaften und Typen umbenennen.

**Wann:** Sie etwas problemlos ohne Suchen nach allen Instanzen und den neuen Namen kopieren/einfügen umbenennen möchten.  

**Grund:** kopieren und Einfügen von den neuen Namen für ein Gesamtprojekt würde wahrscheinlich zu Fehlern führen.  Dieses refactoring Tool führt genau umbenennen.

**Vorgehensweise:**

1. Markieren Sie, oder platzieren Sie den Textcursor innerhalb des Elements an, der umbenannt werden:

   ![Hervorgehobene code](media/rename_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG + R**, klicken Sie dann **STRG + R**.  (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
   * **Maus**
     * Wählen Sie **Bearbeiten > Umgestalten > Umbenennen**.
     * Mit der rechten Maustaste in des Codes, und wählen Sie **umbenennen**.

1. Benennen Sie das Element, indem Sie einfach den neuen Namen eingeben.

   ![Umbenennen von Animationen](media/rename_rename.png)

   > [!TIP]
   > Sie können auch aktualisieren, Kommentare und andere Zeichenfolgen mit diesen neuen Namen sowie [Vorschau der Änderungen](../../ide/preview-changes.md) vor dem Speichern, verwenden die Kontrollkästchen in der **umbenennen** Feld der oben angezeigt wird rechts von der IDE.

1. Wenn Sie mit der Änderung zufrieden sind, klicken Sie auf die **übernehmen** Schaltfläche oder drücken Sie die **EINGABETASTE** und die Änderungen werden ein Commit ausgeführt werden.

> [!NOTE]
> Wenn Sie einen Namen, der bereits verwenden, die zu einem Konflikt führt die **umbenennen** Feld in der IDE werden Sie gewarnt werden können.
>
> ![Konflikt umbenennen](media/rename_conflict.png)

## <a name="see-also"></a>Siehe auch  
[Refactoring (Visual Basic)](../refactoring-vb.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)