---
title: 'Vorgehensweise: Verwenden der Grafikdiagnose mit einem ARM-Gerät | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24067412f875001185a0709c41f930ce3cdc8f3c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516334"
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Gewusst wie: Verwenden der Grafikdiagnose mit einem ARM-Gerät
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Verwenden der Grafikdiagnose mit einem ARM-Gerät](https://docs.microsoft.com/visualstudio/debugger/graphics/how-to-use-graphics-diagnostics-with-an-arm-device).  
  
Die Grafikdiagnose unterstützt Remotedebugging von Direct3D-Apps auf ARM-basierten Geräten, auf denen Windows RT 8.1 oder Windows Phone 8.1. läuft. Sie können Grafikinformationen von Ihrer Direct3D-App erfassen, während diese auf dem Gerät läuft, oder das Gerät als Wiedergabecomputer für zuvor erfasste Grafikinformationen verwenden.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Verwendung der Grafikdiagnose mit einem ARM-basierten Gerät  
 Da Visual Studio nicht auf ARM-basierten Geräten läuft, müssen Sie den Remotedebugger verwenden, um Apps zu analysieren, die darauf laufen. Der Remotedebugger unterstützt Grafikerfassung und -wiedergabe, sodass Sie Rendering-Fehler diagnostizieren und die Grafikleistung auf diesen Geräten bewerten können. Dies ist so einfach wie das Debuggen Ihrer App.  
  
 Wenn Sie Grafikdiagnosefunktionen verwenden möchten, aktivieren Sie zunächst Remotedebugging auf Ihrem Gerät.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>So aktivieren Sie Remotedebugging auf Ihrem ARM-basierten Gerät  
  
1.  Installieren Sie die [ARM Kits Policy](http://msdn.microsoft.com/windows/desktop/dn469188) auf Ihrem ARM-basierten Gerät.  
  
2.  Installieren Sie die [Remotedebugging-Tools](http://go.microsoft.com/fwlink/?LinkId=393086) auf Ihrem ARM-basierten Gerät.  
  
> [!IMPORTANT]
>  Im Falle von Windows Phone 8.1-Geräten müssen Sie Ihr Gerät eventuell für die Entwicklung registrieren. Dafür müssen Sie ein registrierter Entwickler sein. Weitere Informationen finden Sie unter [wie bereitstellen und Ausführen einer app für Windows Phone 8](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Wenn Sie Remotedebugging auf Ihrem Gerät aktiviert haben, machen Sie dieses zu Ihrem Debugziel, und starten Sie die Grafikdiagnose.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>So konfigurieren und starten Sie die Grafikdiagnose auf Ihrem Gerät  
  
1.  Auf der **Projektmappenplattformen** Dropdown-Liste **ARM** , damit Ihr ARM-basiertes Gerät als Remotedebugging-Ziel zur Verfügung stehen.  
  
2.  Auf der **Debugziel** Dropdown-Liste, wählen Sie Ihr ARM-Gerät.  
  
3.  Wählen Sie im Menü **Debuggen**, **Grafiken**, **Diagnose starten**. (Tastatur: Alt+F5)  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Windows Store-apps auf einem Remotecomputer](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Gewusst wie: Ändern des Grafikdiagnose-Wiedergabecomputers](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)



