---
title: 'Vorgehensweise: Debuggen von COM-Servern | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- COM, debugging
- debugging [C++], COM servers
- single document interface (SDI), debugging
- COM servers, debugging
- debugging [C++], ADI applications
- container information
ms.assetid: 9f013c2b-0306-4b34-ba7f-d4445a874da1
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3552ff1ffb5d6b3e3789aebd3a8903bf82a66b16
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205416"
---
# <a name="how-to-debug-com-servers"></a>Vorgehensweise: Debuggen von COM-Servern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Debuggen von COM-Serveranwendungen wirft einige spezifische Probleme auf, die nicht immer einfach zu lösen sind.  
  
 Wenn Sie keine Debuginformationen besitzen oder diese für Ihre Containeranwendung nicht verwenden möchten, besteht das Debuggen der Serveranwendung aus drei Schritten.  
  
### <a name="to-debug-a-server-application-without-container-information"></a>So debuggen Sie eine Serveranwendung ohne Containerinformationen  
  
1. Debuggen Sie den Server wie eine normale Anwendung.  
  
2. Legen Sie die gewünschten Haltepunkte fest.  
  
3. Starten Sie die Containeranwendung.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von COM und ActiveX](../debugger/com-and-activex-debugging.md)   
 [Vorgehensweise: RPC-Debuggen von COM-Clients und -Servern](../debugger/how-to-debug-com-clients-and-servers-using-rpc-debugging.md)   
 [Debuggen von COM-Servern und -Containern](../debugger/com-server-and-container-debugging.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)
