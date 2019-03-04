---
title: 'Fehler: Remotecomputer wird in einem Dialogfeld "Remoteverbindungen" nicht angezeigt | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: a081eceb137c7958a489fb0968f190d0d01b32fa
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698364"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Fehler: Remotecomputer wird im Dialogfeld „Remoteverbindungen“ nicht angezeigt.
Wenn der Remotecomputer im Dialogfeld „Remoteverbindungen“ nicht angezeigt wird, überprüfen Sie die folgenden häufigen Ursachen.

 Bei Verwendung des verwalteten Kompatibilitätsmodus, ziehen Sie die Visual Studio 2010-Dokumentation zurate: [Troubleshooting Remote Debugging - Visual Studio 2010 (Problembehandlung beim Remotedebuggen: Visual Studio 2010)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Häufige Ursachen dieses Fehlers

-   Der Remotecomputer wird auf einem Computer ausgeführt, der sich in einem anderen Subnetz befindet. Zum Beheben dieses Problems geben Sie im Dialogfeld „Qualifizierer“ manuell den Computernamen oder die IP-Adresse ein.

-   Der Remotedebugger wird auf dem Remotecomputer nicht ausgeführt. Um dieses Problem zu beheben, starten Sie den Remotedebugger.

-   Kommunikation zwischen Visual Studio und dem Remotecomputer wird durch die Firewall blockiert. Um dieses Problem zu beheben, konfigurieren Sie Ihre Firewall so, dass Visual Studio und der Remotedebugger (msvsmon) kommunizieren können.

-   Die Kommunikation zwischen Visual Studio und dem Remotecomputer wird durch Antivirensoftware blockiert. Um dieses Problem zu beheben, konfigurieren Sie die Antivirensoftware so, dass Visual Studio und der Remotedebugger (msvsmon) kommunizieren können.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)