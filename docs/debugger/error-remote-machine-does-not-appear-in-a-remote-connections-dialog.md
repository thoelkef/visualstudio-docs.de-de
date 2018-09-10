---
title: 'Fehler: Remotecomputer wird in einem Dialogfeld "Remoteverbindungen" nicht angezeigt | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f91358597ce19f9dac1341831364dafb1fcabae
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284158"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Fehler: Remotecomputer wird im Dialogfeld „Remoteverbindungen“ nicht angezeigt.
Wenn der Remotecomputer im Dialogfeld „Remoteverbindungen“ nicht angezeigt wird, überprüfen Sie die folgenden häufigen Ursachen.  
  
 Wenn Sie verwalteten Kompatibilitätsmodus verwenden, finden Sie in der Visual Studio 2010-Dokumentation: [Problembehandlung beim Remotedebuggen – Visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).  
  
### <a name="common-causes-for-this-error"></a>Häufige Ursachen dieses Fehlers  
  
-   Der Remotecomputer wird auf einem Computer ausgeführt, der sich in einem anderen Subnetz befindet. Zum Beheben dieses Problems geben Sie im Dialogfeld „Qualifizierer“ manuell den Computernamen oder die IP-Adresse ein.  
  
-   Der Remotedebugger wird auf dem Remotecomputer nicht ausgeführt. Um dieses Problem zu beheben, starten Sie den Remotedebugger.  
  
-   Kommunikation zwischen Visual Studio und dem Remotecomputer wird durch die Firewall blockiert. Um dieses Problem zu beheben, konfigurieren Sie Ihre Firewall so, dass Visual Studio und der Remotedebugger (msvsmon) kommunizieren können.  
  
-   Die Kommunikation zwischen Visual Studio und dem Remotecomputer wird durch Antivirensoftware blockiert. Um dieses Problem zu beheben, konfigurieren Sie die Antivirensoftware so, dass Visual Studio und der Remotedebugger (msvsmon) kommunizieren können.  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen](../debugger/remote-debugging.md)