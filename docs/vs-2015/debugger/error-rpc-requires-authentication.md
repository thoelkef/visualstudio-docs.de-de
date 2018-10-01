---
title: 'Fehler: RPC verlangt Authentifizierung | Microsoft-Dokumentation'
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
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e606c0e730b279723248a3fdbdd5b3e2bca1c4a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511958"
---
# <a name="error-rpc-requires-authentication"></a>Fehler: RPC verlangt Authentifizierung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Fehler: RPC-Requires Authentication](https://docs.microsoft.com/visualstudio/debugger/error-rpc-requires-authentication).  
  
Der Visual Studio-Debugger kann keine Verbindung mit dem Remotecomputer herstellen. Auf dem lokalen Computer ist eine RPC-Richtlinie aktiviert, die das Remotedebugging verhindert.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Führen Sie `\` *Windir*`\system32\regedt32.exe`  
  
2.  Suchen und löschen Sie `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Starten Sie den Computer neu, damit die Registrierungsänderung wirksam wird.  
  
4.  Wenn das Problem weiterhin besteht, wenden Sie sich an den Domänenadministrator bitten, zu der **Computerkonfiguration > Administrative Vorlagen - > System -> Remote Procedure Call-Einschränkungen für nicht authentifizierte RPC-Clients >** Gruppe aktiviert wurde.



