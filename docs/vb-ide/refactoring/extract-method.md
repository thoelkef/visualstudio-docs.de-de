---
title: Extrahieren Sie die Methode - Umgestaltung (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 8ad16c15-432b-4b8c-86fd-5f31ad652d24
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractmethod
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 6ec25b8c0e2a583364ff3c6418515507cdc04d40
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="extract-a-method-in-visual-basic"></a>Extrahieren Sie eine Methode in Visual Basic
**Was:** können Sie ein Fragment des Codes in einem eigenen umzuwandeln.

**Wann:** haben Sie ein Fragment von vorhandenem Code, in einer Methode, die von einer anderen Methode aufgerufen werden muss.  

**Grund:** Sie konnte Kopieren/Einfügen dieses Codes jedoch, die zu Duplizierung führen würde.  Eine bessere Lösung ist dieses Fragment in einem eigenen umgestaltet werden, die kostenlos durch keine andere Methode aufgerufen werden kann.

**Vorgehensweise:**

1. Markieren Sie den Code, die extrahiert werden:

   ![Hervorgehobene code](media/extractmethod_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG + R**, klicken Sie dann **STRG + M**.  (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **Methode extrahieren** im Popupmenü Fenster Vorschau.
   * **Maus**
     * Wählen Sie **Bearbeiten > Umgestalten > Methode extrahieren**.
     * Mit der rechten Maustaste in des Codes, und wählen Sie **Umgestalten > extrahieren > Methode extrahieren**.
     * Mit der rechten Maustaste in des Codes, wählen Sie die **Schnellaktionen und Refactorings** Menü **Methode extrahieren** im Popupmenü Fenster Vorschau.

   Die Methode wird sofort erstellt werden.  Von hier aus können Sie nun die Methode umbenennen, einfach durch den neuen Namen eingeben.

   > [!TIP]
   > Sie können auch aktualisieren, Kommentare und andere Zeichenfolgen mit diesen neuen Namen sowie [Vorschau der Änderungen](../../ide/preview-changes.md) vor dem Speichern, verwenden die Kontrollkästchen in der **umbenennen** Feld der oben angezeigt wird rechts von der IDE.

   ![Benennen Sie die Methode](media/extractmethod_rename.png)

1. Wenn Sie mit der Änderung zufrieden sind, klicken Sie auf die **übernehmen** Schaltfläche oder drücken Sie die **EINGABETASTE** und die Änderungen werden ein Commit ausgeführt werden.

## <a name="see-also"></a>Siehe auch  
[Refactoring (Visual Basic)](../refactoring-vb.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)