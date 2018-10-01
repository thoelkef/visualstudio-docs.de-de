---
title: 'Fehler: Remotecomputer wird in einem Dialogfeld "Remoteverbindungen" nicht angezeigt | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 552be1e38cdb7401af36b287b23091d754c35980
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523377"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Fehler: Remotecomputer wird im Dialogfeld „Remoteverbindungen“ nicht angezeigt.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Fehler: Remotecomputer wird nicht angezeigt, in einem Dialogfeld "Remoteverbindungen"](https://docs.microsoft.com/visualstudio/debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog).  
  
Wenn der Remotecomputer im Dialogfeld „Remoteverbindungen“ nicht angezeigt wird, überprüfen Sie die folgenden häufigen Ursachen.  
  
 Wenn Sie verwalteten Kompatibilitätsmodus verwenden, finden Sie in der Visual Studio 2010-Dokumentation: [Problembehandlung beim Remotedebuggen – Visual Studio 2010](https://msdn.microsoft.com/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Häufige Ursachen dieses Fehlers  
  
-   Der Remotecomputer wird auf einem Computer ausgeführt, der sich in einem anderen Subnetz befindet. Zum Beheben dieses Problems geben Sie im Dialogfeld „Qualifizierer“ manuell den Computernamen oder die IP-Adresse ein.  
  
-   Der Remotedebugger wird auf dem Remotecomputer nicht ausgeführt. Um dieses Problem zu beheben, starten Sie den Remotedebugger.  
  
-   Kommunikation zwischen Visual Studio und dem Remotecomputer wird durch die Firewall blockiert. Um dieses Problem zu beheben, konfigurieren Sie Ihre Firewall so, dass Visual Studio und der Remotedebugger (msvsmon) kommunizieren können.  
  
-   Die Kommunikation zwischen Visual Studio und dem Remotecomputer wird durch Antivirensoftware blockiert. Um dieses Problem zu beheben, konfigurieren Sie die Antivirensoftware so, dass Visual Studio und der Remotedebugger (msvsmon) kommunizieren können.  
  
## <a name="see-also"></a>Siehe auch  
 [Einrichten der Remotetools auf dem Gerät](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)



