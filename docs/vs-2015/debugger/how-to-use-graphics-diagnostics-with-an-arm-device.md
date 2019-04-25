---
title: 'Vorgehensweise: Verwenden der Grafikdiagnose mit einem ARM-Gerät | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ae934de4a9f0dbcf4076d7402abd138eac20268
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104875"
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Vorgehensweise: Verwenden der Grafikdiagnose mit einem ARM-Gerät
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Grafikdiagnose unterstützt Remotedebugging von Direct3D-Apps auf ARM-basierten Geräten, auf denen Windows RT 8.1 oder Windows Phone 8.1. läuft. Sie können Grafikinformationen von Ihrer Direct3D-App erfassen, während diese auf dem Gerät läuft, oder das Gerät als Wiedergabecomputer für zuvor erfasste Grafikinformationen verwenden.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Verwendung der Grafikdiagnose mit einem ARM-basierten Gerät  
 Da Visual Studio nicht auf ARM-basierten Geräten läuft, müssen Sie den Remotedebugger verwenden, um Apps zu analysieren, die darauf laufen. Der Remotedebugger unterstützt Grafikerfassung und -wiedergabe, sodass Sie Rendering-Fehler diagnostizieren und die Grafikleistung auf diesen Geräten bewerten können. Dies ist so einfach wie das Debuggen Ihrer App.  
  
 Wenn Sie Grafikdiagnosefunktionen verwenden möchten, aktivieren Sie zunächst Remotedebugging auf Ihrem Gerät.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>So aktivieren Sie Remotedebugging auf Ihrem ARM-basierten Gerät  
  
1. Installieren Sie die [ARM Kits Policy](http://msdn.microsoft.com/windows/desktop/dn469188) auf Ihrem ARM-basierten Gerät.  
  
2. Installieren Sie die [Remotedebugging-Tools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) auf Ihrem ARM-basierten Gerät.  
  
> [!IMPORTANT]
>  Im Falle von Windows Phone 8.1-Geräten müssen Sie Ihr Gerät eventuell für die Entwicklung registrieren. Dafür müssen Sie ein registrierter Entwickler sein. Weitere Informationen finden Sie unter [wie bereitstellen und Ausführen einer app für Windows Phone 8](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Wenn Sie Remotedebugging auf Ihrem Gerät aktiviert haben, machen Sie dieses zu Ihrem Debugging-Ziel, und starten Sie die Grafikdiagnose.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>So konfigurieren und starten Sie die Grafikdiagnose auf Ihrem Gerät  
  
1. Auf der **Projektmappenplattformen** Dropdown-Liste **ARM** , damit Ihr ARM-basiertes Gerät als Remotedebugging-Ziel zur Verfügung stehen.  
  
2. Auf der **Debugziel** Dropdown-Liste, wählen Sie Ihr ARM-Gerät.  
  
3. Wählen Sie im Menü **Debuggen**, **Grafiken**, **Diagnose starten**. (Tastatur: ALT + F5)  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Windows Store-apps auf einem Remotecomputer](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Vorgehensweise: Ändern des Grafikdiagnose-Wiedergabecomputers](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)
