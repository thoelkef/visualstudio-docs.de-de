---
title: "Fehler: RPC verlangt Authentifizierung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.rpc_requires_authentication"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Fehler: RPC verlangt Authentifizierung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Visual Studio\-Debugger kann keine Verbindung mit dem Remotecomputer herstellen.  Auf dem lokalen Computer ist eine RPC\-Richtlinie aktiviert, die das Remotedebugging verhindert.  
  
### So beheben Sie diesen Fehler  
  
1.  Führen Sie `\`*windir*`\system32\regedt32.exe` aus.  
  
2.  Suchen Sie den Eintrag `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`, und löschen Sie ihn.  
  
3.  Starten Sie den Computer neu, damit die Registrierungsänderung wirksam wird.  
  
4.  Wenn das Problem weiterhin auftritt, fragen Sie Ihren Domänenadministrator nach der Gruppenrichtlinieneinstellung Computerkonfiguration\-\>Administrative Vorlagen\-\>System\-\>Remoteprozeduraufruf\-\>Einschränkungen für nicht authentifizierte RPC\-Clients.