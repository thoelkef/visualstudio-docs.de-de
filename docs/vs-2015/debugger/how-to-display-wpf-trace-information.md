---
title: 'Vorgehensweise: Anzeigen von WPF-Ablaufverfolgungsinformationen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07cdebcc636f768c7caf2437af55f20283db7b6c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515640"
---
# <a name="how-to-display-wpf-trace-information"></a>Gewusst wie: Anzeigen von WPF-Ablaufverfolgungsinformationen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Anzeigen von WPF-Ablaufverfolgungsinformationen](https://docs.microsoft.com/visualstudio/debugger/how-to-display-wpf-trace-information).  
  
[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] debugablaufverfolgungs-Informationen von WPF-Anwendungen empfangen und Anzeigen dieser Informationen können die **Ausgabe** Fenster. Zum Anzeigen von debugablaufverfolgungs-Informationen muss die WPF-Ablaufverfolgung aktiviert werden.  
  
 Sie können WPF-Ablaufverfolgung in der Datei "App.Config" oder programmgesteuert mit der <xref:System.Diagnostics.PresentationTraceSources>-Klasse aktivieren. Eine einfachere Möglichkeit zum Aktivieren der WPF-Ablaufverfolgung ist die Verwendung der **Optionen** Fenster. Die WPF-Ablaufverfolgung für Webanwendungen wird nicht unterstützt.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>So aktivieren Sie WPF-Ablaufverfolgungsinformationen oder passen diese an  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  In der **Optionen** öffnen Sie im Dialogfeld im Feld auf der linken Seite die **Debuggen** Knoten.  
  
3.  Klicken Sie unter **Debuggen**, klicken Sie auf **Fenster "Ausgabe"**.  
  
4.  Klicken Sie unter **allgemeine Ausgabeeinstellungen**Option **gesamte Debugausgabe**.  
  
5.  Suchen Sie im Feld auf der rechten Seite **WPF-Ablaufverfolgungseinstellungen**.  
  
6.  Öffnen der **WPF-Ablaufverfolgungseinstellungen** Knoten.  
  
7.  Klicken Sie unter **WPF-Ablaufverfolgungseinstellungen**, klicken Sie auf die Kategorie der Einstellungen, die Sie aktivieren möchten (z. B. **Datenbindung**).  
  
     Ein Dropdown-Listenfeld-Steuerelement wird in der Spalte "Einstellungen" neben **Datenbindung** oder der Kategorie, die Sie geklickt haben.  
  
8.  Klicken Sie auf die Dropdown-Liste, und wählen Sie den Typ der Ablaufverfolgungsinformationen, die Sie anzeigen möchten: **alle**, **kritisch**, **Fehler**, **Warnung**,  **Informationen**, **ausführliche**, oder **ActivityTracing**.  
  
     **Kritische** ermöglicht die Verfolgung von kritischen Ereignissen nur.  
  
     **Fehler** ermöglicht die Verfolgung von kritischen und fehlerbezogenen Ereignissen.  
  
     **Warnung** ermöglicht die Verfolgung von kritischen, Fehler- und Warnungsereignisse.  
  
     **Informationen** ermöglicht die Verfolgung von kritischen, Fehler-, Warnungs- und Ereignisse.  
  
     **Ausführliche** ermöglicht die Verfolgung von kritischen, Fehler-, Warn-, Informationen und ausführlich Ereignisse.  
  
     **ActivityTracing** ermöglicht die Verfolgung von beenden, starten, anhalten, Übertragung und Resume-Ereignisse.  
  
     Weitere Informationen zur Bedeutung der Ablaufverfolgungs-Informationsebenen finden Sie unter <xref:System.Diagnostics.SourceLevels>.  
  
9. Klicken Sie auf **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>So deaktivieren Sie WPF-Ablaufverfolgungsinformationen  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  In der **Optionen** öffnen Sie im Dialogfeld im Feld auf der linken Seite die **Debuggen** Knoten.  
  
3.  Klicken Sie unter **Debuggen**, klicken Sie auf **Fenster "Ausgabe"**.  
  
4.  Suchen Sie im Feld auf der rechten Seite **WPF-Ablaufverfolgungseinstellungen**.  
  
5.  Öffnen der **WPF-Ablaufverfolgungseinstellungen** Knoten.  
  
6.  Klicken Sie unter **WPF-Ablaufverfolgungseinstellungen**, klicken Sie auf die Kategorie der Einstellungen, die Sie aktivieren möchten (z. B. **Datenbindung**).  
  
     Ein Dropdown-Listenfeld-Steuerelement wird in der Spalte "Einstellungen" neben **Datenbindung** oder der Kategorie, die Sie geklickt haben.  
  
7.  Klicken Sie auf die Dropdown-Liste, und wählen Sie **aus**.  
  
8.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von WPF](../debugger/debugging-wpf.md)



