---
title: 'Vorgehensweise: Debuggen von COM-Servern | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6343366478e360631b5a50c8c6d36ca4b31c27cf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853930"
---
# <a name="how-to-debug-com-servers"></a>Vorgehensweise: Debuggen von COM-Servern
Das Debuggen von COM-Serveranwendungen wirft einige spezifische Probleme auf, die nicht immer einfach zu lösen sind.  
  
 Wenn Sie keine Debuginformationen besitzen oder diese für Ihre Containeranwendung nicht verwenden möchten, besteht das Debuggen der Serveranwendung aus drei Schritten.  
  
### <a name="to-debug-a-server-application-without-container-information"></a>So debuggen Sie eine Serveranwendung ohne Containerinformationen  
  
1.  Debuggen Sie den Server wie eine normale Anwendung.  
  
2.  Legen Sie die gewünschten Haltepunkte fest.  
  
3.  Starten Sie die Containeranwendung.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von COM und ActiveX](../debugger/com-and-activex-debugging.md)   
 [Vorgehensweise: RPC-Debuggen von COM-Clients und -Servern](../debugger/how-to-debug-com-clients-and-servers-using-rpc-debugging.md)   
 [Debuggen von COM-Servern und -Containern](../debugger/com-server-and-container-debugging.md)   
 [Debuggen in Visual Studio](../debugger/index.md)  
 [Debugger – Featuretour](../debugger/debugger-feature-tour.md)