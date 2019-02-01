---
title: 'Fehler: Stellen Sie sicher, dass DNS auf dem Zielcomputer ordnungsgemäß konfiguriert ist. | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb5d5091f38835134c8803f58962a250790b24c9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996492"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Fehler: Stellen Sie sicher, dass DNS auf dem Zielcomputer ordnungsgemäß konfiguriert ist
Wenn Sie versuchen, Remotedebuggen auszuführen, wird möglicherweise folgende Fehlermeldung angezeigt:  
  
```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Dieser Fehler tritt auf, wenn der Name des Hostcomputers für den Visual Studio-Debugger vom Zielcomputer nicht aufgelöst werden kann. Überprüfen Sie die DNS-Einstellungen auf dem Zielcomputer.  
  
- Gehen Sie wie folgt vor, um Informationen zum Anzeigen der DNS-Einstellung in Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 oder Windows Server 2008 R2 einzublenden: Wählen Sie im Menü **Start** die Option **Hilfe und Support** aus, und suchen Sie anschließend nach **Ändern der TCP/IP-Einstellungen**.  
  
- Um weitere Informationen zu erhalten, rufen Sie die [Microsoft Windows-Website](http://go.microsoft.com/fwlink/?LinkId=252720) auf, und suchen Sie nach **Ändern der TCP/IP-Einstellungen**.  
  
  Wenn das DNS-Problem nicht behoben werden kann, können Sie versuchen, den Remotedebugger unter einem anderen Konto auszuführen. Dieser Fehler tritt nur auf, wenn der Remotedebugger unter dem lokalen Systemkonto oder dem Netzwerkdienstkonto ausgeführt wird. Wenn Sie den Remotedebugger unter einem anderen Konto ausführen, kann die NTLM-Authentifizierung verwendet werden, für die DNS nicht erforderlich ist. sein. Die Prozedur finden Sie unter [Fehler: Der Visual Studio Remote Debugger-Dienst auf dem Zielcomputer kann die Verbindung mit diesem Computer nicht wiederherstellen](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)
