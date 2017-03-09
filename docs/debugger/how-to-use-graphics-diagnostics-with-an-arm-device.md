---
title: "Gewusst wie: Verwenden der Grafikdiagnose mit einem ARM-Ger&#228;t | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Verwenden der Grafikdiagnose mit einem ARM-Ger&#228;t
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Grafikdiagnose unterstützt Remotedebugging von Direct3D\-Apps auf ARM\-basierten Geräten, auf denen Windows RT 8.1 oder Windows Phone 8.1. läuft.  Sie können Grafikinformationen von Ihrer Direct3D\-App erfassen, während diese auf dem Gerät läuft, oder das Gerät als Wiedergabecomputer für zuvor erfasste Grafikinformationen verwenden.  
  
## Verwendung der Grafikdiagnose mit einem ARM\-basierten Gerät  
 Da Visual Studio nicht auf ARM\-basierten Geräten läuft, müssen Sie den Remotedebugger verwenden, um Apps zu analysieren, die darauf laufen.  Der Remotedebugger unterstützt Grafikerfassung und \-wiedergabe, sodass Sie Rendering\-Fehler diagnostizieren und die Grafikleistung auf diesen Geräten bewerten können. Dies ist so einfach wie das Debuggen Ihrer App.  
  
 Wenn Sie Grafikdiagnosefunktionen verwenden möchten, aktivieren Sie zunächst Remotedebugging auf Ihrem Gerät.  
  
#### So aktivieren Sie Remotedebugging auf Ihrem ARM\-basierten Gerät  
  
1.  Installieren Sie die [ARM Kits Policy](http://msdn.microsoft.com/windows/desktop/dn469188) auf Ihrem ARM\-basierten Gerät.  
  
2.  Installieren Sie die [Remotedebugging\-Tools](http://go.microsoft.com/fwlink/?LinkId=393086) auf Ihrem ARM\-basierten Gerät.  
  
> [!IMPORTANT]
>  Im Falle von Windows Phone 8.1\-Geräten müssen Sie Ihr Gerät eventuell für die Entwicklung registrieren.  Dafür müssen Sie ein registrierter Entwickler sein.  Weitere Informationen finden Sie unter [How to deploy and run an app for Windows Phone 8 \(Bereitstellen und Ausführen einer App für Windows Phone 8, in englischer Sprache\)](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Wenn Sie Remotedebugging auf Ihrem Gerät aktiviert haben, machen Sie dieses zu Ihrem Debugging\-Ziel, und starten Sie die Grafikdiagnose.  
  
#### So konfigurieren und starten Sie die Grafikdiagnose auf Ihrem Gerät  
  
1.  Wählen Sie in der Dropdown\-Liste **Projektmappenplattformen** die Option **ARM**, sodass Ihr ARM\-basiertes Gerät als Remotedebugging\-Ziel verfügbar ist.  
  
2.  Wählen Sie in der Dropdown\-Liste **Debugziel** Ihr ARM\-Gerät.  
  
3.  Klicken Sie in der Menüleiste auf **Debuggen**, dann auf **Grafik** und **Diagnose starten**.  \(Tastatur: Alt\+F5\)  
  
## Siehe auch  
 [Ausführen von Windows Store\-Apps auf einem Remotecomputer](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Gewusst wie: Ändern des Grafikdiagnose\-Wiedergabecomputers](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)