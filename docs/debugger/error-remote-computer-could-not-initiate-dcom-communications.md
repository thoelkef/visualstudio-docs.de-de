---
title: 'Fehler: Remotecomputer konnte DCOM-Kommunikation nicht initiieren | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 377211f0ca7e4095da58b169f113689db9c7b41e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Fehler: Der Remotecomputer konnte die DCOM-Kommunikation nicht initiieren
Bei einem Versuch des Remotecomputers, mit dem lokalen Computer zu kommunizieren, ist ein DCOM-Fehler aufgetreten. Der lokale Computer ist der Computer, auf dem  
  
 Visual Studio ausgeführt wird. Dieser Fehler kann mehrere Ursachen haben:  
  
-   Auf dem lokalen Computer ist eine Firewall aktiviert.  
  
-   Die Windows-Authentifizierung vom Remotecomputer zum lokalen Computer funktioniert nicht.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Wenn auf dem lokalen Computer die Windows-Firewall aktiviert ist, finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md) für Anweisungen zum Konfigurieren der Firewall für lokales Debuggen.  
  
2.  Testen Sie die Windows-Authentifizierung, indem Sie versuchen, vom Remoteserver auf dem lokalen Computer eine Dateifreigabe zu öffnen.  
  
3.  Versuchen Sie zum Wiederherstellen der Windows-Authentifizierung, beide Computer neu zu starten. Überprüfen Sie die Ereignisprotokolle auf dem lokalen Computer und dem Remotecomputer auf Kerberos-Fehler, und klären Sie mit den Domänenadministratoren ab, ob bekannte Probleme vorliegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen](../debugger/remote-debugging.md)