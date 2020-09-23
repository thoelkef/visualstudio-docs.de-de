---
title: RPC verlangt Authentifizierung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
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
ms.openlocfilehash: 9bb172455226ab290a74da07e97fc40deb30b6ba
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852549"
---
# <a name="error-rpc-requires-authentication"></a>Fehler: RPC verlangt Authentifizierung
Der Visual Studio-Debugger kann keine Verbindung mit dem Remotecomputer herstellen. Auf dem lokalen Computer ist eine RPC-Richtlinie aktiviert, die das Remotedebugging verhindert.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Führen Sie `\`*windir*`\system32\regedt32.exe` aus.

2. Suchen Sie nach `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`, und löschen Sie den Eintrag.

3. Starten Sie den Computer neu, damit die Registrierungsänderung wirksam wird.

4. Wenn das Problem weiterhin besteht, bitten Sie Ihren Domänenadministrator, die Gruppenrichtlinieneinstellung **Computerkonfiguration > Administrative Vorlagen > System > Remoteprozeduraufruf > Einschränkungen für nicht authentifizierte RPC-Clients** zu überprüfen.