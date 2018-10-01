---
title: 'Vorgehensweise: Verwalten von Editormodi | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 7e679c751f5d4e8aa23bb843f812476f2f9e9f5b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524912"
---
# <a name="how-to-manage-editor-modes"></a>Gewusst wie: Verwalten von Editormodi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Verwalten von Editormodi](https://docs.microsoft.com/visualstudio/ide/how-to-manage-editor-modes).  
  
Sie können den Visual Studio Code-Editor in verschiedenen Anzeigemodi verwenden.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="enabling-full-screen-mode"></a>Aktivieren des Vollbildmodus  
 Wenn Sie möchten, könne Sie alle Toolfenster ausblenden und nur Dokumentfenster anzeigen, indem Sie den **Vollbildmodus** aktivieren.  
  
#### <a name="to-enable-full-screen-mode"></a>So können Sie den Vollbildmodus aktivieren  
  
-   Drücken Sie auf ALT + UMSCHALT + EINGABE, um den **Vollbildmodus** zu starten oder zu beenden.  
  
     – oder –  
  
-   Geben Sie im Feld **Befehl** den Befehl `View.Fullscreen` ein.  
  
## <a name="enabling-virtual-space-mode"></a>Aktivieren des Modus für virtuelle Leerzeichen  
 Im Modus für **virtuelle Leerzeichen** werden Leerzeichen am Ende jeder Codezeile eingefügt. Aktivieren Sie diese Option, um Kommentare immer an derselben Stelle neben dem Markup einzufügen.  
  
#### <a name="to-enable-virtual-space-mode"></a>So aktivieren Sie den Modus für virtuelle Leerzeichen  
  
1.  Wählen Sie im Menü **Extras** den Befehl **Optionen** aus.  
  
2.  Erweitern Sie den Ordner **Text-Editor** und klicken Sie auf **Alle Sprachen**, um diese Option global anzuwenden, oder entscheiden Sie sich für den Ordner einer bestimmten Sprache. (Um z.B. Zeilennummern nur für Visual Basic zu aktivieren, klicken Sie auf die Optionen „Basic“, „Text-Editor“.)  
  
3.  Klicken Sie auf die Option **Allgemein** und dann unter **Einstellungen** auf **Enable Virtual Space** (Virtuelle Leerzeichen aktivieren).  
  
    > [!NOTE]
    >  **Virtuelle Leerzeichen** sind im Modus **Spaltenauswahl** aktiviert. Wenn der Modus für **virtuelle Leerzeichen** nicht aktiviert ist, wird die Einfügemarke vom Ende einer Zeile direkt zum ersten Zeichen der nächsten verschoben.  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen des Editors](../ide/customizing-the-editor.md)   
 [Vorgehensweise: anordnen und Andocken von Windows](../misc/how-to-arrange-and-dock-windows.md)   
 [Schriftarten und Farben, Umgebung, Dialogfeld „Optionen“](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)



