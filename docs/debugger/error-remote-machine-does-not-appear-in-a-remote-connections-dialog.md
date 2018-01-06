---
title: 'Fehler: Remotecomputer erscheint nicht in einem Dialogfeld "Remoteverbindungen" | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 72a891219b24f1cb80ec9e65988f57ebfb04fcd6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Fehler: Remotecomputer wird im Dialogfeld „Remoteverbindungen“ nicht angezeigt.
Wenn der Remotecomputer im Dialogfeld „Remoteverbindungen“ nicht angezeigt wird, überprüfen Sie die folgenden häufigen Ursachen.  
  
 Bei Verwendung des verwalteten Kompatibilitätsmodus, ziehen Sie die Visual Studio 2010-Dokumentation zurate: [Problembehandlung beim Remotedebuggen – Visual Studio 2010](https://msdn.microsoft.com/en-us/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Häufige Ursachen dieses Fehlers  
  
-   Der Remotecomputer wird auf einem Computer ausgeführt, der sich in einem anderen Subnetz befindet. Zum Beheben dieses Problems geben Sie im Dialogfeld „Qualifizierer“ manuell den Computernamen oder die IP-Adresse ein.  
  
-   Der Remotedebugger wird auf dem Remotecomputer nicht ausgeführt. Um dieses Problem zu beheben, starten Sie den Remotedebugger.  
  
-   Kommunikation zwischen Visual Studio und dem Remotecomputer wird durch die Firewall blockiert. Um dieses Problem zu beheben, konfigurieren Sie Ihre Firewall so, dass Visual Studio und der Remotedebugger (msvsmon) kommunizieren können.  
  
-   Die Kommunikation zwischen Visual Studio und dem Remotecomputer wird durch Antivirensoftware blockiert. Um dieses Problem zu beheben, konfigurieren Sie die Antivirensoftware so, dass Visual Studio und der Remotedebugger (msvsmon) kommunizieren können.  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen](../debugger/remote-debugging.md)