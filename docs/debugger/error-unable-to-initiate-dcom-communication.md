---
title: 'Fehler: Die DCOM-Kommunikation initiiert | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c80f2455b53cba46f0f2f753c55ff1b7e9dad8d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Fehler: Die DCOM-Kommunikation kann nicht initiiert werden
Bei einem Versuch des lokalen Computers, mit dem Remotecomputer zu kommunizieren, ist ein DCOM-Fehler aufgetreten. Dies wird durch eine Firewall auf dem Remoteserver oder durch eine nicht funktionierende Windows-Authentifizierung auf dem Remotecomputer verursacht.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Wenn auf dem Remotecomputer Windows-Firewall aktiviert ist, finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md) für Anweisungen zum Konfigurieren der Firewall für lokales Debuggen.  
  
-   Versuchen Sie zum Wiederherstellen der Windows-Authentifizierung, beide Computer neu zu starten. Überprüfen Sie die Ereignisprotokolle auf dem lokalen Computer und dem Remotecomputer auf Kerberos-Fehler, und klären Sie mit den Domänenadministratoren ab, ob bekannte Probleme vorliegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen](../debugger/remote-debugging.md)