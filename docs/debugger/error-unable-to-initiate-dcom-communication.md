---
title: 'Fehler: Initiiert die DCOM-Kommunikation | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_server_failed
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
ms.openlocfilehash: 89dc5ba98d706153b919063563f1d4beecacdde5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932063"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Fehler: Die DCOM-Kommunikation kann nicht initiiert werden
Bei einem Versuch des lokalen Computers, mit dem Remotecomputer zu kommunizieren, ist ein DCOM-Fehler aufgetreten. Dies wird durch eine Firewall auf dem Remoteserver oder durch eine nicht funktionierende Windows-Authentifizierung auf dem Remotecomputer verursacht.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Wenn auf dem Remotecomputer Windows-Firewall aktiviert ist, finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md) Anleitungen zum Konfigurieren der Firewall für das lokale Debuggen.  
  
-   Versuchen Sie zum Wiederherstellen der Windows-Authentifizierung, beide Computer neu zu starten. Überprüfen Sie die Ereignisprotokolle auf dem lokalen Computer und dem Remotecomputer auf Kerberos-Fehler, und klären Sie mit den Domänenadministratoren ab, ob bekannte Probleme vorliegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Remote Debugging](../debugger/remote-debugging.md)