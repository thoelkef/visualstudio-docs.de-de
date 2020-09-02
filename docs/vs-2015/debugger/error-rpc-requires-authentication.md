---
title: 'Fehler: RPC verlangt Authentifizierung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dbf0c2d13668dbf380f326ee3a49e0389815a8fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62535735"
---
# <a name="error-rpc-requires-authentication"></a>Fehler: RPC verlangt Authentifizierung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Visual Studio-Debugger kann keine Verbindung mit dem Remotecomputer herstellen. Auf dem lokalen Computer ist eine RPC-Richtlinie aktiviert, die das Remotedebugging verhindert.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1. Führen Sie `\`*windir*`\system32\regedt32.exe` aus.  
  
2. Suchen Sie nach `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`, und löschen Sie den Eintrag.  
  
3. Starten Sie den Computer neu, damit die Registrierungsänderung wirksam wird.  
  
4. Wenn das Problem weiterhin besteht, wenden Sie sich an Ihren Domänen Administrator, um >die Gruppenrichtlinien Einstellung **System >administrative Vorlagen >System remote Prozedur Aufruf >Einschränkungen für nicht authentifizierte RPC-Clients zu** erhalten.
