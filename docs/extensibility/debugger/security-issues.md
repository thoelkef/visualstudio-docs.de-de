---
title: Sicherheitsprobleme | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 753f916d148675afd7313afc8673232f22280b7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="security-issues"></a>Sicherheitsprobleme
Um ein Programm, das mit Visual Studio zu debuggen, sind die einzigen Berechtigungen, die erforderlich sind identisch ein Entwickler benötigt, um das Programm auszuführen. Dies schließt das Remotedebuggen für die meisten Situationen (einige Situationen, die im Zusammenhang mit anderen Diensten, z. B. die Internet-Informationsdienste möglicherweise ein höheres Maß an Berechtigungen).  
  
 Während der Visual Studio ausgeführt wird, wird der Prozess-Manager (PDM) Debug-Prozesse auf dem lokalen Computer überwacht. Remote, wird ein Programm namens msvsmon.exe gestartet, vom Entwickler des Remotedebuggens behandeln und die PDM verfügbar zu machen. (Beachten Sie, die von msvsmon.exe ist kein Dienst und muss manuell gestartet werden, um das Remotedebuggen auf diesem Computer aktivieren.) Wenn Visual Studio (oder msvsmon.exe) nicht ausgeführt wird, werden keine Prozesse zum Debuggen nachverfolgt.  
  
 Dies bedeutet, dass ein Entwickler Programme Debuggen kann, wenn, die er ohne besondere Berechtigungen gestartet. Entwickler kann auch Debuggen, Prozesse, die von einem anderen Benutzer gestartet wird, wenn diese anderen Person Mitglied der gleichen Sicherheitsgruppe ist. Zum Aktivieren von Remotedebuggen erforderlich ist, nur so kopieren Sie die erforderlichen Dateien mit der Remoteinstanz, Computer, und starten msvsmon.exe (finden Sie unter [Remotedebuggen](../../debugger/remote-debugging.md) Weitere Details).  
  
## <a name="see-also"></a>Siehe auch  
 [Debugging-Aufgaben](../../extensibility/debugger/debugging-tasks.md)   
 [Prozess-Debug-Manager](../../extensibility/debugger/process-debug-manager.md)   
 [Remotedebuggen](../../debugger/remote-debugging.md)