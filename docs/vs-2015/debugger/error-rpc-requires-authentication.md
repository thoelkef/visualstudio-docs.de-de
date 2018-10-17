---
title: 'Fehler: RPC verlangt Authentifizierung | Microsoft-Dokumentation'
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
ms.openlocfilehash: 5643e815386541bb9045eb56cacbd68e7e9b998d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193830"
---
# <a name="error-rpc-requires-authentication"></a>Fehler: RPC verlangt Authentifizierung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Visual Studio-Debugger kann keine Verbindung mit dem Remotecomputer herstellen. Auf dem lokalen Computer ist eine RPC-Richtlinie aktiviert, die das Remotedebugging verhindert.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Führen Sie `\` *Windir*`\system32\regedt32.exe`  
  
2.  Suchen und löschen Sie `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Starten Sie den Computer neu, damit die Registrierungsänderung wirksam wird.  
  
4.  Wenn das Problem weiterhin besteht, wenden Sie sich an den Domänenadministrator bitten, zu der **Computerkonfiguration > Administrative Vorlagen - > System -> Remote Procedure Call-Einschränkungen für nicht authentifizierte RPC-Clients >** Gruppe aktiviert wurde.



