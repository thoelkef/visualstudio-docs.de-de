---
title: 'Vorgehensweise: Debuggen im gemischten Modus | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: bb1bcaf6eac3d8ad671a8b610c9b45821a93e7b4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438447"
---
# <a name="how-to-debug-in-mixed-mode"></a>Vorgehensweise: Debuggen im gemischten Modus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In den folgenden Prozeduren wird beschrieben, wie sowohl verwalteter als auch systemeigener Code debuggt wird. Dieses Verfahren wird auch als Debuggen im gemischten Modus bezeichnet. Je nachdem, ob die DLL oder die Anwendung in systemeigenem Code geschrieben sind, gibt es hierfür zwei Szenarios:  
  
- Die Anwendung, die die DLL aufruft, ist in systemeigenem Code geschrieben. In diesem Fall handelt es sich um eine verwaltete DLL, und sowohl der verwaltete als auch der systemeigene Debugger müssen für das Debuggen aktiviert werden. Sie können dies überprüfen, der  **\<Projekt > Eigenschaftenseiten** Dialogfeld. Wie Sie dabei vorgehen, hängt davon ab, ob Sie den Debugvorgang über das DLL-Projekt oder über das Projekt für die aufrufende Anwendung starten.  
  
- Die aufrufende Anwendung, die die DLL aufruft, ist in verwaltetem Code, die DLL in nativem Code geschrieben.  
  
> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>So aktivieren Sie Debuggen im gemischten Modus  
  
1. In **Projektmappen-Explorer**, wählen Sie das Projekt.  
  
2. Klicken Sie im Menü **Ansicht** auf die Option **Eigenschaftenseiten**.  
  
3. In der  **\<Projekt > Eigenschaftenseiten** Dialogfeld erweitern Sie die **Konfigurationseigenschaften** Knoten, und wählen Sie dann **Debuggen**.  
  
4. Legen Sie **Debuggertyp** auf **Gemischt** oder **Automatisch** fest.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Debuggen über ein DLL-Projekt](../debugger/how-to-debug-from-a-dll-project.md)
