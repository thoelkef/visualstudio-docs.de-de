---
title: 'Fehler: Stellen Sie sicher, dass DNS auf dem Ziel Computer ordnungsgemäß konfiguriert ist. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6815e21d0fe7af3a24f2fc36a4f448ec420c89de
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299749"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Fehler: Stellen Sie sicher, dass DNS auf dem Zielcomputer ordnungsgemäß konfiguriert ist
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie versuchen, Remotedebuggen auszuführen, wird möglicherweise folgende Fehlermeldung angezeigt:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Dieser Fehler tritt auf, wenn der Name des Hostcomputers für den Visual Studio-Debugger vom Zielcomputer nicht aufgelöst werden kann. Überprüfen Sie die DNS-Einstellungen auf dem Zielcomputer.  
  
- Gehen Sie wie folgt vor, um Informationen zum Anzeigen der DNS-Einstellung in Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 oder Windows Server 2008 R2 einzublenden: Wählen Sie im Menü **Start** die Option **Hilfe und Support** aus, und suchen Sie anschließend nach **Ändern der TCP/IP-Einstellungen**.  
  
- Um weitere Informationen zu erhalten, rufen Sie die [Microsoft Windows-Website](https://go.microsoft.com/fwlink/?LinkId=252720) auf, und suchen Sie nach **Ändern der TCP/IP-Einstellungen**.  
  
  Wenn das DNS-Problem nicht behoben werden kann, können Sie versuchen, den Remotedebugger unter einem anderen Konto auszuführen. Dieser Fehler tritt nur auf, wenn der Remotedebugger unter dem lokalen Systemkonto oder dem Netzwerkdienstkonto ausgeführt wird. Wenn Sie den Remotedebugger unter einem anderen Konto ausführen, kann die NTLM-Authentifizierung verwendet werden, für die DNS nicht erforderlich ist. . Informationen zu diesem Verfahren finden [Sie unter Error: der Visual Studio Remote Debugger-Dienst auf dem Zielcomputer kann keine Verbindung mit diesem Computer herstellen](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
