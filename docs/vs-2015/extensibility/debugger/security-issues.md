---
title: Sicherheitsprobleme | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 874231333c87020c126eac4c066d53512ba0bbc9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946170"
---
# <a name="security-issues"></a>Sicherheitsprobleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um ein Programm mit Visual Studio zu debuggen, werden nur die erforderlichen Berechtigungen identisch ein Entwickler benötigt, um das Programm auszuführen. Dies schließt die Remotedebugging-Funktionen für die meisten Situationen (einige Situationen, die im Zusammenhang mit anderen Diensten, z. B. das Internet Information Service, möglicherweise eine höhere Berechtigungen erforderlich).  
  
 Während Visual Studio ausgeführt wird, verfolgt der Prozess-Manager (PDM) Debuggen auf dem lokalen Computer. Remote wird ein Programm namens msvsmon.exe gestartet, durch den Entwickler zu behandeln, Remotedebuggen und das PDM verfügbar zu machen. (Beachten Sie, dass msvsmon.exe ist kein Dienst und muss manuell gestartet werden, um das Remotedebuggen auf diesem Computer zu aktivieren.) Wenn Visual Studio (oder msvsmon.exe) nicht ausgeführt wird, werden keine Prozesse für das Debuggen nachverfolgt.  
  
 Dies bedeutet, dass ein Entwickler Programme Debuggen kann, er, mit denen keine besonderen Berechtigungen, die gestartet. Entwickler kann auch Debuggen, Prozesse, die von einem anderen Benutzer gestartet werden, wenn diese andere Person die gleiche Sicherheitsgruppe angehört. Um das Remotedebuggen zu aktivieren, es ist notwendig nur kopieren Sie die erforderlichen Dateien mit dem Computer, und msvsmon.exe starten (finden Sie unter [festgelegt Einrichten der Remotetools auf dem Gerät](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) Weitere Details).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)   
 [Prozessbasierter Debug-Manager](../../extensibility/debugger/process-debug-manager.md)   
 [Einrichten der Remotetools auf dem Gerät](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
