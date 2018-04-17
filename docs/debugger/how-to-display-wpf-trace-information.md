---
title: 'Vorgehensweise: Anzeigen von WPF-Ablaufverfolgungsinformationen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3584ae0d1dcd0e33bfa08954a2ad376485b6b71e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-display-wpf-trace-information"></a>Gewusst wie: Anzeigen von WPF-Ablaufverfolgungsinformationen
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] kann debugablaufverfolgungs-Informationen von WPF-Anwendungen empfangen und diese Informationen im Anzeigen der **Ausgabe** Fenster. Zum Anzeigen von debugablaufverfolgungs-Informationen muss die WPF-Ablaufverfolgung aktiviert werden.  
  
 Sie können WPF-Ablaufverfolgung in der Datei "App.Config" oder programmgesteuert mit der <xref:System.Diagnostics.PresentationTraceSources>-Klasse aktivieren. Eine einfachere Möglichkeit zum Aktivieren der WPF-Ablaufverfolgung wird mithilfe der **Optionen** Fenster. Die WPF-Ablaufverfolgung für Webanwendungen wird nicht unterstützt.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>So aktivieren Sie WPF-Ablaufverfolgungsinformationen oder passen diese an  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  In der **Optionen** öffnen (Dialogfeld), in das Feld auf der linken Seite der **Debuggen** Knoten.  
  
3.  Klicken Sie unter **Debuggen**, klicken Sie auf **Fenster "Ausgabe"**.  
  
4.  Klicken Sie unter **allgemeine Ausgabeeinstellungen**Option **gesamte Debugausgabe**.  
  
5.  Suchen Sie im Feld auf der rechten Seite **WPF-Ablaufverfolgungseinstellungen**.  
  
6.  Öffnen der **WPF-Ablaufverfolgungseinstellungen** Knoten.  
  
7.  Klicken Sie unter **WPF-Ablaufverfolgungseinstellungen**, klicken Sie auf die Kategorie der Einstellungen, die Sie aktivieren möchten (z. B. **Datenbindung**).  
  
     Ein Dropdownlisten-Steuerelement wird in der Spalte neben **Datenbindung** oder der Kategorie, die Sie geklickt haben.  
  
8.  Klicken Sie auf die Dropdownliste, und wählen Sie den Typ der Ablaufverfolgungsinformationen aus, die Sie anzeigen möchten: **alle**, **kritisch**, **Fehler**, **Warnung**,  **Informationen**, **ausführliche**, oder **ActivityTracing**.  
  
     **Kritische** ermöglicht die Verfolgung von kritischen Ereignissen nur.  
  
     **Fehler** ermöglicht die Verfolgung von kritischen und fehlerbezogenen Ereignissen.  
  
     **Warnung** ermöglicht die Verfolgung von kritischen, Fehler- und warnungsbezogenen Ereignissen.  
  
     **Informationen** ermöglicht die Verfolgung von kritischen, Fehler-, Warn- und Informationen Ereignisse.  
  
     **Ausführliche** ermöglicht die Verfolgung von kritischen, Fehler-, Warn-, Informationen und Verbose-Ereignisse.  
  
     **ActivityTracing** ermöglicht die Verfolgung von beenden, starten, anhalten, übertragen und Resume-Ereignisse.  
  
     Weitere Informationen zur Bedeutung der Ablaufverfolgungs-Informationsebenen finden Sie unter <xref:System.Diagnostics.SourceLevels>.  
  
9. Klicken Sie auf **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>So deaktivieren Sie WPF-Ablaufverfolgungsinformationen  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  In der **Optionen** öffnen (Dialogfeld), in das Feld auf der linken Seite der **Debuggen** Knoten.  
  
3.  Klicken Sie unter **Debuggen**, klicken Sie auf **Fenster "Ausgabe"**.  
  
4.  Suchen Sie im Feld auf der rechten Seite **WPF-Ablaufverfolgungseinstellungen**.  
  
5.  Öffnen der **WPF-Ablaufverfolgungseinstellungen** Knoten.  
  
6.  Klicken Sie unter **WPF-Ablaufverfolgungseinstellungen**, klicken Sie auf die Kategorie der Einstellungen, die Sie aktivieren möchten (z. B. **Datenbindung**).  
  
     Ein Dropdownlisten-Steuerelement wird in der Spalte neben **Datenbindung** oder der Kategorie, die Sie geklickt haben.  
  
7.  Klicken Sie auf die Dropdownliste, und wählen Sie **deaktiviert**.  
  
8.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von WPF](../debugger/debugging-wpf.md)