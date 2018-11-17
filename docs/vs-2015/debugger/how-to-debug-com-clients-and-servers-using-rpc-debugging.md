---
title: 'Vorgehensweise: Debuggen von COM-Clients und Servern, die RPC-Debuggen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78a4c85d24ea382e5946000ac2225588c5deceed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786797"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Gewusst wie: RPC-Debuggen von COM-Clients und -Servern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können RPC-Debuggen (Remote Procedure Call, Remoteprozeduraufruf) verwenden, um COM-Client-/Server-Anwendungen zu debuggen. Vor der Verwendung muss RPC-Debuggen allerdings aktiviert werden. Bei aktiviertem RPC-Debuggen wird der Debugger an den Server angefügt, wenn Sie vom Client in den Serveraufruf springen. Der Code kann nun debuggt werden. Wenn der Debugger angefügt wurde, können alle Debuggerfeatures sowohl für Client- als auch für Serverprozesse verwendet werden.  
  
### <a name="to-enable-rpc-debugging"></a>So aktivieren Sie RPC-Debuggen  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  In der **Optionen** Dialogfeld klicken Sie auf die **Debuggen** Ordner.  
  
3.  Klicken Sie auf die **Native** Seite.  
  
4.  Wählen Sie die **RPC-Debuggen** Kontrollkästchen.  
  
    > [!NOTE]
    >  Sie müssen Administrator- oder Hauptbenutzerrechte besitzen, um Remoteprozeduraufrufe debuggen zu können.  
  
    > [!NOTE]
    >  RPC-Stepping auf einem Remoteserver, auf dem Microsoft Windows Vista ausgeführt wird, funktioniert nur, wenn ein systemeigener Debugger an den Remoteserver angehängt wird. Andernfalls schlägt der RPC-Aufruf ohne eine Fehlermeldung fehl. Sonst wird der RPC-Aufruf abgeschlossen, aber der Einzelschritt beim RPC-Aufruf funktioniert nicht.  
  
## <a name="see-also"></a>Siehe auch  
 [COM-Servern und-Containern](../debugger/com-server-and-container-debugging.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)



