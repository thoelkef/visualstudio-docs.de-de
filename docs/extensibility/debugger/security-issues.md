---
title: Sicherheitsprobleme | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 98a4c85118fc836e1f8922a24700036c9d4837cb
ms.openlocfilehash: fcc65d94f8348674110db6cc0a87e0e3020a4683
ms.lasthandoff: 02/22/2017

---
# <a name="security-issues"></a>Sicherheitsprobleme
Um ein Programm mithilfe von Visual Studio debuggen, sind die einzigen Berechtigungen, die erforderlich sind identisch mit ein Entwickler benötigt, um das Programm auszuführen. Dies umfasst das Remotedebuggen für die meisten Situationen (einige Situationen, die im Zusammenhang mit anderen Diensten, wie z. B. Internet Information Service, möglicherweise eine höhere Berechtigungsstufe erfordern).  
  
 Während Visual Studio ausgeführt wird, wird der Prozess-Manager (PDM) Debug-Prozesse auf dem lokalen Computer überwacht. Remote wird ein Programm namens msvsmon.exe gestartet, indem der Entwickler das Remotedebuggen zu behandeln und die PDM verfügbar machen. (Beachten Sie, die von msvsmon.exe ist kein Dienst und muss manuell gestartet werden, um Remotedebuggen auf diesem Computer zu aktivieren.) Wenn Visual Studio (oder msvsmon.exe) nicht ausgeführt wird, werden keine Prozesse zum Debuggen nachverfolgt.  
  
 Dies bedeutet, dass ein Entwickler Programme Debuggen kann, wenn, die er ohne besondere Berechtigungen gestartet. Entwickler kann auch Debuggen, Prozesse, die von einem anderen Benutzer gestartet wird, wenn diese andere Person Mitglied der Sicherheitsgruppe der gleiche ist. Und zum Aktivieren von Remotedebuggen, es muss nur kopiert die erforderlichen Dateien auf dem Remote Computer und msvsmon.exe starten (finden Sie unter [Remotedebuggen](../../debugger/remote-debugging.md) Weitere Einzelheiten).  
  
## <a name="see-also"></a>Siehe auch  
 [Debugging-Aufgaben](../../extensibility/debugger/debugging-tasks.md)   
 [Prozess-Debug-Manager](../../extensibility/debugger/process-debug-manager.md)   
 [Remotedebuggen](../../debugger/remote-debugging.md)
