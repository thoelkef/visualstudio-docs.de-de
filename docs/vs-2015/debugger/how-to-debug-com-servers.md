---
title: 'Vorgehensweise: Debuggen von com-Servern | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205416"
---
# <a name="how-to-debug-com-servers"></a>Gewusst wie: Debuggen von COM-Servern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Debuggen von COM-Serveranwendungen wirft einige spezifische Probleme auf, die nicht immer einfach zu lösen sind.  
  
 Wenn Sie keine Debuginformationen besitzen oder diese für Ihre Containeranwendung nicht verwenden möchten, besteht das Debuggen der Serveranwendung aus drei Schritten.  
  
### <a name="to-debug-a-server-application-without-container-information"></a>So debuggen Sie eine Serveranwendung ohne Containerinformationen  
  
1. Debuggen Sie den Server wie eine normale Anwendung.  
  
2. Legen Sie die gewünschten Haltepunkte fest.  
  
3. Starten Sie die Containeranwendung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [COM-und ActiveX-Debugging](../debugger/com-and-activex-debugging.md)   
 [Gewusst wie: Debuggen von com-Clients und-Servern mithilfe von RPC](../debugger/how-to-debug-com-clients-and-servers-using-rpc-debugging.md)   
 [COM-Server-und Container Debugging](../debugger/com-server-and-container-debugging.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)
