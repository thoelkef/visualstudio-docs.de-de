---
title: 'Fehler: Stellen Sie sicher, dass DNS auf dem Zielcomputer ordnungsgemäß konfiguriert ist. | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19184f0925c8c1ed4d2815a59c93281d7c04d0fc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818055"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Fehler: Stellen Sie sicher, dass DNS auf dem Zielcomputer ordnungsgemäß konfiguriert ist
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie versuchen, Remotedebuggen auszuführen, wird möglicherweise folgende Fehlermeldung angezeigt:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Dieser Fehler tritt auf, wenn der Name des Hostcomputers für den Visual Studio-Debugger vom Zielcomputer nicht aufgelöst werden kann. Überprüfen Sie die DNS-Einstellungen auf dem Zielcomputer.  
  
- Weitere Informationen zum Anzeigen der DNS-Einstellung in Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 oder Windows Server 2008 R2, dazu: auf der **starten** Menü wählen **Hilfe und Support** , und suchen Sie nach **Änderung TCP/IP-Einstellungen**.  
  
- Weitere Informationen finden Sie unter [Microsoft Windows-Website](http://go.microsoft.com/fwlink/?LinkId=252720) und suchen Sie nach **Änderung TCP/IP-Einstellungen**.  
  
  Wenn das DNS-Problem nicht behoben werden kann, können Sie versuchen, den Remotedebugger unter einem anderen Konto auszuführen. Dieser Fehler tritt nur auf, wenn der Remotedebugger unter dem lokalen Systemkonto oder dem Netzwerkdienstkonto ausgeführt wird. Wenn Sie den Remotedebugger unter einem anderen Konto ausführen, kann die NTLM-Authentifizierung verwendet werden, für die DNS nicht erforderlich ist. sein. Die Prozedur finden Sie unter [Fehler: die Visual Studio Remote Debugger-Dienst auf dem Zielcomputer kann keine Verbindung hergestellt, rückverbindung mit diesem Computer](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).



