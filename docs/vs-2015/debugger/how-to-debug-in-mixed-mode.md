---
title: 'Vorgehensweise: Debuggen im gemischten Modus | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ee85e5822d4792046c755c85d699dd6a9a5d26
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737159"
---
# <a name="how-to-debug-in-mixed-mode"></a>Gewusst wie: Debuggen im gemischten Modus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In den folgenden Prozeduren wird beschrieben, wie sowohl verwalteter als auch nativer Code debuggt wird. Dieses Verfahren wird auch als Debuggen im gemischten Modus bezeichnet. Je nachdem, ob die DLL oder die Anwendung in systemeigenem Code geschrieben sind, gibt es hierfür zwei Szenarios:  
  
-   Die Anwendung, die die DLL aufruft, ist in nativem Code geschrieben. In diesem Fall handelt es sich um eine verwaltete DLL, und sowohl der verwaltete als auch der native Debugger müssen für das Debuggen aktiviert werden. Sie können dies überprüfen, der  **\<Projekt > Eigenschaftenseiten** Dialogfeld. Wie Sie dabei vorgehen, hängt davon ab, ob Sie den Debugvorgang über das DLL-Projekt oder über das Projekt für die aufrufende Anwendung starten.  
  
-   Die aufrufende Anwendung, die die DLL aufruft, ist in verwaltetem Code, die DLL in systemeigenem Code geschrieben.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>So aktivieren Sie Debuggen im gemischten Modus  
  
1.  In **Projektmappen-Explorer**, wählen Sie das Projekt.  
  
2.  Auf der **Ansicht** Menü klicken Sie auf **Eigenschaftenseiten**.  
  
3.  In der  **\<Projekt > Eigenschaftenseiten** Dialogfeld erweitern Sie die **Konfigurationseigenschaften** Knoten, und wählen Sie dann **Debuggen**.  
  
4.  Legen Sie **Debuggertyp** zu **gemischten** oder **automatisch**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Debuggen über ein DLL-Projekt](../debugger/how-to-debug-from-a-dll-project.md)



