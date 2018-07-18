---
title: 'Vorgehensweise: Debuggen von COM-Server | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 87d5bedd98aed5ab7bddc7027eaac9e7678d533c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481683"
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