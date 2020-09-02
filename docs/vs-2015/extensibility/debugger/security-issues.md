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
ms.openlocfilehash: fb6209882a7a71a68728299064edcc13afabff35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704422"
---
# <a name="security-issues"></a>Sicherheitsprobleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn Sie ein Programm mit Visual Studio debuggen möchten, benötigen Sie nur die gleichen Berechtigungen wie ein Entwickler, um das Programm auszuführen. Dies umfasst in den meisten Fällen das Remote Debuggen (einige Situationen mit anderen Diensten, z. b. der Internet Informationsdienste, benötigen möglicherweise ein höheres Berechtigungs Niveau).  
  
 Während Visual Studio ausgeführt wird, verfolgt der Process Debug Manager (PDM) Debugprozesse auf dem lokalen Computer. Ein Programm mit dem Namen msvsmon.exe wird vom Entwickler gestartet, um das Remote Debuggen zu verarbeiten und das PDM verfügbar zu machen. (Beachten Sie, dass msvsmon.exe kein Dienst ist und manuell gestartet werden muss, um das Remote Debuggen auf diesem Computer zu aktivieren.) Wenn Visual Studio (oder msvsmon.exe) nicht ausgeführt wird, werden keine Prozesse zum Debuggen nachverfolgt.  
  
 Dies bedeutet, dass ein Entwickler die Programme, die er gestartet hat, ohne spezielle Berechtigungen Debuggen kann. Der Entwickler kann sogar Prozesse Debuggen, die von einem anderen Benutzer gestartet wurden, wenn die andere Person Mitglied derselben Sicherheitsgruppe ist. Zum Aktivieren des Remote Debuggens muss lediglich die erforderlichen Dateien auf den Remote Computer kopiert und msvsmon.exe gestartet werden (Weitere Informationen finden Sie unter [Einrichten der Remotetools auf dem Gerät](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) ).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugtasks](../../extensibility/debugger/debugging-tasks.md)   
 [Process Debug Manager](../../extensibility/debugger/process-debug-manager.md)   
 [Einrichten der Remotetools auf dem Gerät](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
