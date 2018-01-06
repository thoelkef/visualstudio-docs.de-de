---
title: 'Fehler: RPC verlangt Authentifizierung | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 73cd474d415a49b6dd9075559d8618289b1b0d21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="error-rpc-requires-authentication"></a>Fehler: RPC verlangt Authentifizierung
Der Visual Studio-Debugger kann keine Verbindung mit dem Remotecomputer herstellen. Auf dem lokalen Computer ist eine RPC-Richtlinie aktiviert, die das Remotedebugging verhindert.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Führen Sie `\` *Windir*`\system32\regedt32.exe`  
  
2.  Suchen und löschen Sie `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Starten Sie den Computer neu, damit die Registrierungsänderung wirksam wird.  
  
4.  Wenn das Problem weiterhin besteht, wenden Sie sich an Ihren Domänenadministrator, über die **Computerkonfiguration > Administrative Vorlagen > System > Remoteprozeduraufruf > Einschränkungen für nicht authentifizierte RPC-Clients** Gruppenrichtlinie festlegen.