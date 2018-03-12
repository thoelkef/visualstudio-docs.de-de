---
title: 'Vorgehensweise: Debuggen von COM-Server | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- COM, debugging
- debugging [C++], COM servers
- single document interface (SDI), debugging
- COM servers, debugging
- debugging [C++], ADI applications
- container information
ms.assetid: 9f013c2b-0306-4b34-ba7f-d4445a874da1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a0aedd0f60464ed56bfeb8f6f2e3147680641ea6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-com-servers"></a>Gewusst wie: Debuggen von COM-Servern
Das Debuggen von COM-Serveranwendungen wirft einige spezifische Probleme auf, die nicht immer einfach zu lösen sind.  
  
 Wenn Sie keine Debuginformationen besitzen oder diese für Ihre Containeranwendung nicht verwenden möchten, besteht das Debuggen der Serveranwendung aus drei Schritten.  
  
### <a name="to-debug-a-server-application-without-container-information"></a>So debuggen Sie eine Serveranwendung ohne Containerinformationen  
  
1.  Debuggen Sie den Server wie eine normale Anwendung.  
  
2.  Legen Sie die gewünschten Haltepunkte fest.  
  
3.  Starten Sie die Containeranwendung.  
  
## <a name="see-also"></a>Siehe auch  
 [COM und ActiveX-Debugging](../debugger/com-and-activex-debugging.md)   
 [Vorgehensweise: Debuggen von COM-Clients und Servern mithilfe von RPC-Debuggen](../debugger/how-to-debug-com-clients-and-servers-using-rpc-debugging.md)   
 [COM-Servern und-Containern](../debugger/com-server-and-container-debugging.md)   
 [Debuggen in Visual Studio](../debugger/index.md)  
 [Debugger – Featuretour](../debugger/debugger-feature-tour.md)