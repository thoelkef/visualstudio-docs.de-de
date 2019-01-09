---
title: Vollbildmodus und Modus für virtuelle Leerzeichen
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f2bf05eaaa5a61f7614b5d35ac6f8467ad6089a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820438"
---
# <a name="how-to-manage-editor-modes"></a>Vorgehensweise: Verwalten von Bearbeitungsmodi

Sie können den Visual Studio-Code-Editor in verschiedenen Anzeigemodi verwenden.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in diesem Artikel beschriebenen. Klicken Sie auf **Extras** > **Einstellungen importieren/exportieren** und dann auf **Alle Einstellungen zurücksetzen**, um Ihre Einstellungen z.B. in **Allgemein** oder **Visual C++** zu ändern.

## <a name="enable-full-screen-mode"></a>Aktivieren des Vollbildmodus

Wenn Sie möchten, könne Sie alle Toolfenster ausblenden und nur Dokumentfenster anzeigen, indem Sie den **Vollbildmodus** aktivieren.

-   Drücken Sie auf **ALT**+**UMSCHALT**+**EINGABE**, um den **Vollbildmodus** zu starten oder zu beenden.

     – oder –

-   Geben Sie im Feld **Befehl** den Befehl `View.Fullscreen` ein.

## <a name="enable-virtual-space-mode"></a>So aktivieren Sie den Modus für virtuelle Leerzeichen

Im Modus für **virtuelle Leerzeichen** werden Leerzeichen am Ende jeder Codezeile eingefügt. Aktivieren Sie diese Option, um Kommentare immer an derselben Stelle neben dem Markup einzufügen.

1.  Wählen Sie im Menü **Extras** den Befehl **Optionen** aus.

2.  Erweitern Sie den Ordner **Text-Editor** und klicken Sie auf **Alle Sprachen**, um diese Option global anzuwenden, oder entscheiden Sie sich für den Ordner einer bestimmten Sprache. Klicken Sie auf den Knoten **Basic** > **Text-Editor**, um beispielsweise nur für Visual Basic Zeilennummern zu aktivieren.

3.  Klicken Sie auf die Option **Allgemein** und dann unter **Einstellungen** auf **Enable Virtual Space** (Virtuelle Leerzeichen aktivieren).

    > [!NOTE]
    > **Virtuelle Leerzeichen** sind im Modus **Spaltenauswahl** aktiviert. Wenn der Modus für **virtuelle Leerzeichen** nicht aktiviert ist, wird die Einfügemarke vom Ende einer Zeile direkt zum ersten Zeichen der nächsten verschoben.

## <a name="see-also"></a>Siehe auch

- [Anpassen des Editors](../ide/customizing-the-editor.md)
- [Anpassen von Fensterlayouts in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)
- [Schriftarten und Farben, Umgebung, Dialogfeld „Optionen“](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)