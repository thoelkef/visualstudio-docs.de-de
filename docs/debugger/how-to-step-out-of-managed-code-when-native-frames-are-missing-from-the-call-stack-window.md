---
title: 'Vorgehensweise: Ausführen bis Rücksprung verwaltetem Code, wenn systemeigene Rahmen im Aufruflistenfenster fehlen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e21d45cd65fc6bc6a66f2f7c698952f0cdd788b9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Gewusst wie: Ausführen von verwaltetem Code bis zum Rücksprung, wenn systemeigene Rahmen im Aufruflistenfenster fehlen
Wenn der Code systemeigene Rahmen enthält, die in nicht sichtbar sind die **Aufrufliste** Fenster, die beim Ausführen von verwalteten Codes kann zu unerwarteten Ergebnissen führen. Dieses Problem zu umgehen, können Sie einen Haltepunkt anstelle von **Ausführen bis Rücksprung**.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>So führen Sie verwalteten Code bis zum Rücksprung aus, wenn systemeigene Rahmen in der Aufrufliste fehlen  
  
1.  Legen Sie im nativen Code nach dem Aufruf an den verwalteten Code einen Positionshaltepunkt fest.  
  
2.  Auf der **Debuggen** Menü wählen **Fortfahren**.  
  
     Sobald der verwaltete Aufruf fertig gestellt wurde, wird die Ausführung am Haltepunkt im nativen Code beendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Verwenden des Fensters „Aufrufliste“](../debugger/how-to-use-the-call-stack-window.md)