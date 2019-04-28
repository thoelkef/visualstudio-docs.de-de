---
title: 'Fehler: Fehler bei der Kerberosauthentifizierung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c18053f9-9074-4bc3-a8bf-13e4acbea921
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5e85bc7a5bac87692448aab393056fa1db5edbd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62535634"
---
# <a name="error-kerberos-authentication-failed"></a>Fehler: Fehler bei der Kerberos-Authentifizierung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Versuch, das Remotedebuggen auszuführen, kann die folgende Fehlermeldung ausgegeben werden:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos auythentication failed.  
```  
  
 Dieser Fehler tritt auf, wenn der Visual Studio-Remotedebugmonitor unter dem lokalen Systemkonto oder dem Netzwerkdienstkonto ausgeführt wird. Der Remotedebugger muss unter einem dieser Konten eine Verbindung für die Kerberos-Authentifizierung herstellen, um die Kommunikation mit dem Visual Studio Debugger-Hostcomputer zu ermöglichen.  
  
 Unter den folgenden Bedingungen ist die Kerberos-Authentifizierung nicht verfügbar:  
  
- Entweder der Zielcomputer oder der Debuggerhostcomputer befindet sich in einer Arbeitsgruppe anstatt in einer Domäne  
  
   \- oder –  
  
- Kerberos wurde auf dem Domänencontroller deaktiviert  
  
  Wenn die Kerberos-Authentifizierung nicht verfügbar ist, ändern Sie das zum Ausführen des Visual Studio-Remotedebugmonitors verwendete Konto. Die Prozedur finden Sie unter [Fehler: Der Visual Studio Remote Debugger-Dienst auf dem Zielcomputer kann keine Verbindung hergestellt, rückverbindung mit diesem Computer](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).  
  
  Wenn beide Computer mit derselben Domäne verbunden sind und weiterhin diese Meldung ausgegeben wird, stellen Sie sicher, dass der Name des Debuggerhostcomputers vom DNS auf dem Zielcomputer ordnungsgemäß aufgelöst wird. Siehe folgendes Verfahren.  
  
### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>So überprüfen Sie, ob der Name des Debuggerhostcomputers vom DNS auf dem Zielcomputer ordnungsgemäß aufgelöst wird  
  
1. Klicken Sie auf dem Zielcomputer auf das Menü **Start**, zeigen Sie auf **Zubehör**, und klicken Sie dann auf **Eingabeaufforderung**.  
  
2. Geben Sie im Fenster **Eingabeaufforderung** Folgendes ein:  
  
    ```  
    ping <debugger_host_computer_name>  
    ```  
  
3. Die erste Zeile der `ping`-Antwort enthält den vollständigen Computernamen und die vollständige IP-Adresse, die vom DNS für den angegebenen Computer zurückgegeben wurden.  
  
4. Öffnen Sie auf dem Debuggerhostcomputer das Fenster **Eingabeaufforderung**, und führen Sie `ipconfig` aus.  
  
5. Vergleichen Sie die IP-Adresswerte.  
  
## <a name="see-also"></a>Siehe auch  
 [Remote Debugging Errors and Troubleshooting (Remotedebuggen – Fehler und Problembehandlung)](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
