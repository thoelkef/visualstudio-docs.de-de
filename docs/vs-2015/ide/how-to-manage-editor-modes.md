---
title: 'Vorgehensweise: Verwalten von Editormodi | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a188e90d3feeb903eb8b4efceb91eb53cac3bdce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651848"
---
# <a name="how-to-manage-editor-modes"></a>Gewusst wie: Verwalten von Editormodi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können den Visual Studio Code-Editor in verschiedenen Anzeigemodi verwenden.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="enabling-full-screen-mode"></a>Aktivieren des Vollbildmodus
 Sie können auswählen, dass Sie alle Tool Fenster ausblenden und nur Dokument Fenster anzeigen, indem Sie den **voll Bild** Modus aktivieren.

#### <a name="to-enable-full-screen-mode"></a>So aktivieren Sie den Vollbildmodus

- Drücken Sie ALT + UMSCHALT + Eingabe, um den **voll Bild** Modus zu beenden oder zu beenden.

     – oder –

- Geben Sie im Feld **Befehl** den Befehl `View.Fullscreen` ein.

## <a name="enabling-virtual-space-mode"></a>Aktivieren des Modus für virtuelle Leerzeichen
 Im Modus für **virtuelle Leerzeichen** werden Leerzeichen am Ende jeder Codezeile eingefügt. Aktivieren Sie diese Option, um Kommentare immer an derselben Stelle neben dem Markup einzufügen.

#### <a name="to-enable-virtual-space-mode"></a>So aktivieren Sie den Modus des virtuellen Bereichs

1. Wählen Sie im Menü **Extras** den Befehl **Optionen** aus.

2. Erweitern Sie den Ordner **Text-Editor** und klicken Sie auf **Alle Sprachen**, um diese Option global anzuwenden, oder entscheiden Sie sich für den Ordner einer bestimmten Sprache. (Um z.B. Zeilennummern nur für Visual Basic zu aktivieren, klicken Sie auf die Optionen „Basic“, „Text-Editor“.)

3. Klicken Sie auf die Option **Allgemein** und dann unter **Einstellungen** auf **Enable Virtual Space** (Virtuelle Leerzeichen aktivieren).

    > [!NOTE]
    > **Virtuelle Leerzeichen** sind im Modus **Spaltenauswahl** aktiviert. Wenn der Modus für **virtuelle Leerzeichen** nicht aktiviert ist, wird die Einfügemarke vom Ende einer Zeile direkt zum ersten Zeichen der nächsten verschoben.

## <a name="see-also"></a>Weitere Informationen
 [Anpassen des Editors](../ide/customizing-the-editor.md) Gewusst [wie: anordnen und Andocken von Windows](../misc/how-to-arrange-and-dock-windows.md) [-Schriftarten und Farben, Umgebung, Dialog Feld "Optionen](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) "
