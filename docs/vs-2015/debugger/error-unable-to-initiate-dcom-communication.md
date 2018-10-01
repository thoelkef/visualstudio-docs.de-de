---
title: 'Fehler: Die DCOM-Kommunikation initiiert | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c8ee1e5a9a9f799a4e9d5d8a4cc3b6f5e03b504
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513955"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Fehler: Die DCOM-Kommunikation kann nicht initiiert werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Fehler: die DCOM-Kommunikation initiiert](https://docs.microsoft.com/visualstudio/debugger/error-unable-to-initiate-dcom-communication).  
  
Bei einem Versuch des lokalen Computers, mit dem Remotecomputer zu kommunizieren, ist ein DCOM-Fehler aufgetreten. Dies wird durch eine Firewall auf dem Remoteserver oder durch eine nicht funktionierende Windows-Authentifizierung auf dem Remotecomputer verursacht.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Wenn auf dem Remotecomputer Windows-Firewall aktiviert ist, finden Sie unter [festgelegt Einrichten der Remotetools auf dem Gerät](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) Anleitungen zum Konfigurieren der Firewall für das lokale Debuggen.  
  
-   Versuchen Sie zum Wiederherstellen der Windows-Authentifizierung, beide Computer neu zu starten. Überprüfen Sie die Ereignisprotokolle auf dem lokalen Computer und dem Remotecomputer auf Kerberos-Fehler, und klären Sie mit den Domänenadministratoren ab, ob bekannte Probleme vorliegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen](../debugger/remote-debugging.md)



