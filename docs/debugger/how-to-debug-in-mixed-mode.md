---
title: 'Vorgehensweise: Debuggen im gemischten Modus | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/19/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 834288c063a4bc0d830f121dcb8589b509c61bcf
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256161"
---
# <a name="how-to-debug-in-mixed-mode"></a>Gewusst wie: Debuggen im gemischten Modus
In den folgenden Prozeduren wird beschrieben, wie sowohl verwalteter als auch nativer Code debuggt wird. Dieses Verfahren wird auch als Debuggen im gemischten Modus bezeichnet. Je nachdem, ob die DLL oder die Anwendung in systemeigenem Code geschrieben sind, gibt es hierfür zwei Szenarios:  
  
-   Die Anwendung, die die DLL aufruft, ist in nativem Code geschrieben. In diesem Fall handelt es sich um eine verwaltete DLL, und sowohl der verwaltete als auch der native Debugger müssen für das Debuggen aktiviert werden. Sie können dies überprüfen, der  **\<Projekt > Eigenschaftenseiten** Dialogfeld. Wie Sie dabei vorgehen, hängt davon ab, ob Sie den Debugvorgang über das DLL-Projekt oder über das Projekt für die aufrufende Anwendung starten.  
  
-   Die aufrufende Anwendung, die die DLL aufruft, ist in verwaltetem Code, die DLL in nativem Code geschrieben. Ein Lernprogramm, das Sie durch diese Schritte führt, finden Sie unter [verwalteten und systemeigenen Code Debuggen](../debugger/how-to-debug-managed-and-native-code.md).
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

Wenn Sie den Zugriff auf das Projekt für die aufrufende Anwendung besitzen, können Sie eine DLL aus dem DLL-Projekt debuggen. Weitere Informationen finden Sie unter [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md). Sie müssen nicht verwenden, kombiniert, um nur das DLL-Projekt zu debuggen.
  
### <a name="to-enable-mixed-mode-debugging-c-calling-app"></a>So aktivieren Sie das Debuggen im gemischten Modus (C++-aufrufende app)  
  
1.  In **Projektmappen-Explorer**, wählen Sie das systemeigene Projekt.
  
2.  Auf der **Ansicht** Menü klicken Sie auf **Eigenschaftenseiten**.
  
3.  In der  **\<Projekt > Eigenschaftenseiten** Dialogfeld erweitern Sie die **Konfigurationseigenschaften** Knoten, und wählen Sie dann **Debuggen**.  
  
4.  Legen Sie **Debuggertyp** zu **gemischten** oder **automatisch**.

    ![Aktivieren Sie das Debuggen im gemischten Modus](../debugger/media/dbg-mixed-mode-from-native.png "Debuggen im gemischten Modus aktivieren")

### <a name="to-enable-mixed-mode-debugging-c-or-vb-calling-app"></a>So aktivieren Sie das Debuggen im gemischten Modus (C#- oder VB aufrufende app)  
  
1.  In **Projektmappen-Explorer**, wählen Sie das verwaltete Projekt.  
  
2.  Auf der **Ansicht** Menü klicken Sie auf **Eigenschaftenseiten**.  
  
3.  In der  **\<Projekt > Eigenschaftenseiten** wählen Sie im Dialogfeld die **Debuggen** Registerkarte, und wählen Sie dann **Debuggen von nativem Code aktivieren**

    ![Debuggen von nativem Code aktivieren](../debugger/media/dbg-mixed-mode-from-csharp.png "Debuggen von nativem Code aktivieren")
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Debuggen über ein DLL-Projekt](../debugger/how-to-debug-from-a-dll-project.md)