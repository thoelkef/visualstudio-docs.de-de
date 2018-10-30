---
title: 'Fehler: Stellen Sie sicher, dass DNS auf dem Zielcomputer ordnungsgemäß konfiguriert ist. | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c204e127db15403379c317430c220c886c028e90
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911836"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Fehler: Stellen Sie sicher, dass DNS auf dem Zielcomputer ordnungsgemäß konfiguriert ist
Wenn Sie versuchen, Remotedebuggen auszuführen, wird möglicherweise folgende Fehlermeldung angezeigt:  
  
```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Dieser Fehler tritt auf, wenn der Name des Hostcomputers für den Visual Studio-Debugger vom Zielcomputer nicht aufgelöst werden kann. Überprüfen Sie die DNS-Einstellungen auf dem Zielcomputer.  
  
- Weitere Informationen zum Anzeigen der DNS-Einstellung in Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 oder Windows Server 2008 R2, dazu: auf der **starten** Menü wählen **Hilfe und Support** , und suchen Sie nach **Änderung TCP/IP-Einstellungen**.  
  
- Weitere Informationen finden Sie unter [Microsoft Windows-Website](http://go.microsoft.com/fwlink/?LinkId=252720) und suchen Sie nach **Änderung TCP/IP-Einstellungen**.  
  
  Wenn das DNS-Problem nicht behoben werden kann, können Sie versuchen, den Remotedebugger unter einem anderen Konto auszuführen. Dieser Fehler tritt nur auf, wenn der Remotedebugger unter dem lokalen Systemkonto oder dem Netzwerkdienstkonto ausgeführt wird. Wenn Sie den Remotedebugger unter einem anderen Konto ausführen, kann die NTLM-Authentifizierung verwendet werden, für die DNS nicht erforderlich ist. sein. Die Prozedur finden Sie unter [Fehler: die Visual Studio Remote Debugger-Dienst auf dem Zielcomputer kann keine Verbindung hergestellt, rückverbindung mit diesem Computer](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
