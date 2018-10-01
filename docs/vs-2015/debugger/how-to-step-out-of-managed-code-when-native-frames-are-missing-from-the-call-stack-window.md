---
title: 'Gewusst wie: Prozedurschritt aus verwaltetem Code, wenn systemeigene Rahmen im Aufruflistenfenster fehlen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 682d4f9c8973f8deee65efa0cd8c0d78061ee00a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510394"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Gewusst wie: Ausführen von verwaltetem Code bis zum Rücksprung, wenn systemeigene Rahmen im Aufruflistenfenster fehlen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Prozedurschritt aus verwaltetem Code, wenn systemeigene Rahmen im Aufruflistenfenster fehlen](https://docs.microsoft.com/visualstudio/debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window).  
  
Wenn Ihr Code systemeigene Rahmen enthält, die in werden die **Aufrufliste** Fenster, die beim Ausführen von verwaltetem Code kann zu unerwarteten Ergebnissen führen. Dieses Problem zu umgehen, können Sie einen Haltepunkt anstelle von **Ausführen bis Rücksprung**.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>So führen Sie verwalteten Code bis zum Rücksprung aus, wenn systemeigene Rahmen in der Aufrufliste fehlen  
  
1.  Legen Sie im nativen Code nach dem Aufruf an den verwalteten Code einen Positionshaltepunkt fest.  
  
2.  Auf der **Debuggen** Menü wählen **Weiter**.  
  
     Sobald der verwaltete Aufruf fertig gestellt wurde, wird die Ausführung am Haltepunkt im nativen Code beendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Verwenden des Fensters „Aufrufliste“](../debugger/how-to-use-the-call-stack-window.md)





