---
title: "Umgestalten einer Umbenennung in Visual Studio für C# | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.rename
dev_langs: CSharp
ms.workload: dotnet
ms.openlocfilehash: e1325de81e16b0e381f07af4d8073d0a3fa4330c
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="rename-a-code-symbol-in-c"></a>Umbenennen eines Codesymbols in C# #

**Beschreibung**: Hiermit können Sie Bezeichner für Codesymbole (z.B. Felder, lokale Variablen, Methoden, Namespaces, Eigenschaften und Typen) umbenennen.

**Hintergrund**: Sie möchten ein Element sicher umbenennen, ohne alle Instanzen suchen und den neuen Namen kopieren und einfügen zu müssen.

**Vorteile**: Das Kopieren und Einfügen des neuen Namens in ein ganzes Projekt würde aller Wahrscheinlichkeit nach zu Fehlern führen.  Dieses Refactoringtool führt die Umbenennungsaktion ordnungsgemäß durch.

**Vorgehensweise**:

1. Markieren Sie den Namen des umzubenennenden Elements, oder platzieren Sie den Textcursor in das Element:

   ![Markierter Code](media/rename-highlight-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+R** und dann **STRG+R**. (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
   * **Maus**
     * Wählen Sie **Bearbeiten > Umgestalten > Umbenennen** aus.
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie **Umbenennen** aus.

1. Benennen Sie das Element einfach um, indem Sie den neuen Namen eingeben.

   ![Animierte Darstellung des Umbenennungsvorgangs](media/rename-animated-cs.gif)

   > [!TIP]
   > Sie können Kommentare und andere Zeichenfolgen vor dem Speichern mit diesem neuen Namen aktualisieren sowie eine [Vorschau der Änderungen](../../ide/preview-changes.md) anzeigen, indem Sie oben rechts in der IDE die jeweiligen Kontrollkästchen im Feld **Umbenennen** aktivieren.

1. Wenn Sie mit der Änderung zufrieden sind, klicken Sie auf die Schaltfläche **Übernehmen**, oder drücken Sie die **EINGABETASTE**. Die Änderungen werden angewendet.

> [!NOTE]
> Wenn Sie einen bereits vorhandenen Namen verwenden, der zu einem Konflikt führen würde, werden Sie durch das Feld **Umbenennen** in Ihrer IDE darüber informiert.
>
> ![Umbenennungskonflikt](media/rename-conflict-cs.png)

## <a name="see-also"></a>Siehe auch

[Refactoring](../refactoring-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)
