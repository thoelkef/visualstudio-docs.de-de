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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 193afeddd553dfda54de568c92b4697e3f1a2a93
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095541"
---
# <a name="how-to-manage-editor-modes"></a>Vorgehensweise: Verwalten von Editormodi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können den Visual Studio Code-Editor in verschiedenen Anzeigemodi verwenden.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="enabling-full-screen-mode"></a>Aktivieren des Vollbildmodus  
 Wenn Sie möchten, könne Sie alle Toolfenster ausblenden und nur Dokumentfenster anzeigen, indem Sie den **Vollbildmodus** aktivieren.  
  
#### <a name="to-enable-full-screen-mode"></a>So können Sie den Vollbildmodus aktivieren  
  
- Drücken Sie auf ALT + UMSCHALT + EINGABE, um den **Vollbildmodus** zu starten oder zu beenden.  
  
     – oder –  
  
- Geben Sie im Feld **Befehl** den Befehl `View.Fullscreen` ein.  
  
## <a name="enabling-virtual-space-mode"></a>Aktivieren des Modus für virtuelle Leerzeichen  
 Im Modus für **virtuelle Leerzeichen** werden Leerzeichen am Ende jeder Codezeile eingefügt. Aktivieren Sie diese Option, um Kommentare immer an derselben Stelle neben dem Markup einzufügen.  
  
#### <a name="to-enable-virtual-space-mode"></a>So aktivieren Sie den Modus für virtuelle Leerzeichen  
  
1. Wählen Sie im Menü **Extras** den Befehl **Optionen** aus.  
  
2. Erweitern Sie den Ordner **Text-Editor** und klicken Sie auf **Alle Sprachen**, um diese Option global anzuwenden, oder entscheiden Sie sich für den Ordner einer bestimmten Sprache. (Um z.B. Zeilennummern nur für Visual Basic zu aktivieren, klicken Sie auf die Optionen „Basic“, „Text-Editor“.)  
  
3. Klicken Sie auf die Option **Allgemein** und dann unter **Einstellungen** auf **Enable Virtual Space** (Virtuelle Leerzeichen aktivieren).  
  
    > [!NOTE]
    >  **Virtuelle Leerzeichen** sind im Modus **Spaltenauswahl** aktiviert. Wenn der Modus für **virtuelle Leerzeichen** nicht aktiviert ist, wird die Einfügemarke vom Ende einer Zeile direkt zum ersten Zeichen der nächsten verschoben.  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen des Editors](../ide/customizing-the-editor.md)   
 [Vorgehensweise: Anordnen und Andocken von Windows](../misc/how-to-arrange-and-dock-windows.md)   
 [Schriftarten und Farben, Umgebung, Dialogfeld „Optionen“](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)
