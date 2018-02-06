---
title: Extrahieren einer Methode in Visual Basic | Microsoft-Dokumentation
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
f1_keywords: vs.csharp.refactoring.extractmethod
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: f9e55a41f9a61626e8fce18cb11da6edc8a8bced
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="extract-a-method-in-visual-basic"></a>Extrahieren einer Methode in Visual Basic

**Beschreibung**: Hiermit können Sie ein Codefragment in eine eigene Methode umwandeln.

**Hintergrund**: Sie verwenden ein Fragment von vorhandenem Code in einer Methode, die von einer anderen Methode aufgerufen werden muss.  

**Vorteile**: Sie könnten diesen Code kopieren und einfügen, dies würde jedoch zu einer Duplizierung führen.  Eine bessere Lösung wäre es, dieses Fragment in eine eigene Methode umzugestalten, die von anderen Methoden beliebig aufgerufen werden kann.

**Vorgehensweise**:

1. Markieren Sie den zu extrahierenden Code:

   ![Markierter Code](media/extractmethod-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+R** und dann **STRG+M**.  (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Methode extrahieren** aus.
   * **Maus**
     * Wählen Sie **Bearbeiten > Umgestalten > Methode extrahieren** aus.
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie **Umgestalten > Extrahieren > Methode extrahieren**.
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Methode extrahieren** aus.

   Die Methode wird sofort erstellt.  In dieser Ansicht können Sie nun die Methode umbenennen, indem Sie einfach den neuen Namen eingeben.

   > [!TIP]
   > Sie können Kommentare und andere Zeichenfolgen vor dem Speichern mit diesem neuen Namen aktualisieren sowie eine [Vorschau der Änderungen](../../ide/preview-changes.md) anzeigen, indem Sie oben rechts in der IDE die jeweiligen Kontrollkästchen im Feld **Umbenennen** aktivieren.

   ![Umbenennen einer Methode](media/extractmethod-rename-vb.png)

1. Wenn Sie mit der Änderung zufrieden sind, klicken Sie auf die Schaltfläche **Übernehmen**, oder drücken Sie die **EINGABETASTE**. Die Änderungen werden angewendet.

## <a name="see-also"></a>Siehe auch

[Refactoring](../refactoring-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)