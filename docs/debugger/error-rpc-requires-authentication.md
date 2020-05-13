---
title: 'Fehler: RPC verlangt Authentifizierung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: c473916a6b689984f234736eb8b763056fc002d9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850458"
---
# <a name="error-rpc-requires-authentication"></a>Fehler: RPC verlangt Authentifizierung
Der Visual Studio-Debugger kann keine Verbindung mit dem Remotecomputer herstellen. Auf dem lokalen Computer ist eine RPC-Richtlinie aktiviert, die das Remotedebugging verhindert.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Führen Sie `\`*windir*`\system32\regedt32.exe` aus.

2. Suchen Sie nach `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`, und löschen Sie den Eintrag.

3. Starten Sie den Computer neu, damit die Registrierungsänderung wirksam wird.

4. Wenn das Problem weiterhin besteht, bitten Sie Ihren Domänenadministrator, die Gruppenrichtlinieneinstellung **Computerkonfiguration > Administrative Vorlagen > System > Remoteprozeduraufruf > Einschränkungen für nicht authentifizierte RPC-Clients** zu überprüfen.