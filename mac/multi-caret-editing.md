---
title: Bearbeiten mit mehreren Caretzeichen
description: Fügen Sie beim Bearbeiten von Code in Visual Studio für Mac Text an mehreren Stellen ein.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "75439049"
---
# <a name="multi-caret-editing"></a>Bearbeiten mit mehreren Caretzeichen

Das Bearbeiten mit mehreren Caretzeichen gestattet es Ihnen, _n_ Einfügemarken auf einmal hinzuzufügen. Im Modus für mehrere Caretzeichen können Sie Ihrem Dokument entweder per Mausklick oder per Tastaturbefehl zusätzliche Carets hinzufügen. Das primäre Caret ist durch einen roten Cursor gekennzeichnet, während die sekundären Carets in einer hellblauen Farbe angezeigt werden. Der Bearbeitungsmodus für mehrere Caretzeichen kann über die `ESC`-TASTE deaktiviert werden.

## <a name="enabling-multi-caret-editing"></a>Aktivieren der Bearbeitung mit mehreren Caretzeichen

### <a name="keyboard"></a>Tastatur

Der Modus für mehrere Caretzeichen kann auf verschiedene Weise über die Tastatur aktiviert werden. In der folgenden Tabelle finden Sie die verfügbaren Tastenkombinationen zur Eingabe bestimmter Modi der Bearbeitung mit mehreren Caretzeichen:

| Hotkey  | Action                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Nächstes übereinstimmendes Caretzeichen einfügen    | 
|  ⌥⇧;   | Caretzeichen an allen übereinstimmenden Positionen einfügen | 
|  ⌥⇧,   | Letztes Caretzeichen entfernen             | 
|  ⌥⇧/   | Letztes Caretzeichen nach unten verschieben          | 

Jede dieser Verhaltensweisen wird an der aktuellen Position des Caretzeichens verankert, wenn Sie den Befehl aufrufen. Wenn sich das Caretzeichen z. B. am Anfang des Wortes „Name“ befindet und Sie „Caretzeichen an allen übereinstimmenden Positionen einfügen“ (⌥⇧;) aufrufen, wird bei jeder Instanz des Wortes „Name“ in Ihrem aktuellen Dokument ein Caretzeichen am Anfang des Wortes eingefügt. Ebenso gilt beim Aufrufen des Befehls „Nächstes passendes Caretzeichen einfügen" (⌥⇧.), dass ein Caretzeichen an der nächsten Instanz des Wortes „Name“ platziert wird. Dieser Befehl kann mehrfach aufgerufen werden.

![Tastatur mit mehreren Caretzeichen](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Maus/Touchpad

Mit dem Cursor können Sie die Auswahl bestimmter Einfügemarken für mehrere Caretzeichen freigeben. Während die Tastenkombinationen an übereinstimmende Zeichenfolgen gebunden sind, können Sie mit dem Cursor an beliebiger Stelle im Dokument manuell ein Caretzeichen einfügen. Sobald die Caretzeichen festgelegt sind, wird jedes die Tasteneingaben, die Sie auf Ihrer Tastatur eingeben, wiedergeben.

Um mit der Maus mehrere Caretzeichen einzufügen, müssen Sie ⌘⌥ gedrückt halten und an die Stelle klicken, an der die Caretzeichen eingegeben werden sollen. Solange Sie die Tasten ⌘⌥ gedrückt halten, befinden Sie sich im Einfügemodus. Wenn Sie ein Caretzeichen an einer falschen Stelle einfügen, können Sie das Caretzeichen entfernen, indem Sie weiterhin ⌘⌥ gedrückt halten und erneut in denselben Bereich klicken. Wenn Sie alle Caretzeichen an den gewünschten Stellen platziert haben, dann lassen Sie die Tasten ⌘⌥ los und beginnen Sie mit der Eingabe. Das folgende GIF veranschaulicht sowohl das Auswählen eines Satzes von Einfügemarken als auch das Entfernen von fälschlich gesetzten Einfügemarken.

![Maus mit mehrerer Caretzeichen](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Weitere Informationen

- [Schnellaktionen (Visual Studio unter Windows)](/visualstudio/ide/quick-actions)
- [Umgestalten von Code (Visual Studio unter Windows)](/visualstudio/ide/refactoring-in-visual-studio)
