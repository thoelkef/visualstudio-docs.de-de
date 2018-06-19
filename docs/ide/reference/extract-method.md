---
title: Extrahieren einer Methode in Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: b4b5a818a75399fc4ce29fb7f2bec6332dac0585
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945791"
---
# <a name="extract-a-method-refactoring"></a>Refactoring des Extrahierens einer Methode

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung**: Hiermit können Sie ein Codefragment in eine eigene Methode umwandeln.

**Hintergrund**: Sie verwenden ein Fragment von vorhandenem Code in einer Methode, die von einer anderen Methode aufgerufen werden muss.

**Vorteile**: Sie könnten diesen Code kopieren und einfügen, dies würde jedoch zu einer Duplizierung führen. Eine bessere Lösung wäre es, dieses Fragment in eine eigene Methode umzugestalten, die von anderen Methoden beliebig aufgerufen werden kann.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie den zu extrahierenden Code:

   - C#:

    ![Hervorgehobener Code – C#](media/extractmethod-highlight-cs.png)

   - Visual Basic:

    ![Hervorgehobener Code – Visual Basic](media/extractmethod-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
     - Drücken Sie **STRG+R** und dann **STRG+M**. (Beachten Sie, dass Ihre Tastenkombination je nach dem gewählten Profil möglicherweise abweicht.)
     - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Methode extrahieren** aus.
   - **Maus**
     - Wählen Sie **Bearbeiten > Umgestalten > Methode extrahieren** aus.
     - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie **Umgestalten > Extrahieren > Methode extrahieren**.
     - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Methode extrahieren** aus.

   Die Methode wird sofort erstellt. In dieser Ansicht können Sie nun die Methode umbenennen, indem Sie einfach den neuen Namen eingeben.

   > [!TIP]
   > Sie können Kommentare und andere Zeichenfolgen vor dem Speichern mit diesem neuen Namen aktualisieren sowie eine [Vorschau der Änderungen](../../ide/preview-changes.md) anzeigen, indem Sie oben rechts in der IDE die jeweiligen Kontrollkästchen im Feld **Umbenennen** aktivieren.

   - C#:

    ![Umbenennen einer Methode – C#](media/extractmethod-rename-cs.png)

   - Visual Basic:

    ![Umbenennen einer Methode – Visual Basic](media/extractmethod-rename-vb.png)

1. Wenn Sie mit der Änderung zufrieden sind, klicken Sie auf die Schaltfläche **Übernehmen**, oder drücken Sie die **EINGABETASTE**. Die Änderungen werden angewendet.

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)