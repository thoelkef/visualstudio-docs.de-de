---
title: Debuggen im gemischten Modus | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c67953db7daa9575fe30108f8772de550ed5b19d
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="debugging-mixed-mode-applications"></a>Debuggen von Anwendungen im gemischten Modus
Eine Anwendung im gemischten Modus ist eine Anwendung, in der nativer Code (C++) mit verwaltetem Code (z. B. Visual Basic-Code, Visual C#-Code oder verwaltetes C++, das mit der Common Language Runtime ausgeführt wird) kombiniert wird. Das Debuggen von Anwendungen im gemischten Modus erfolgt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] weitestgehend transparent. Es unterscheidet sich nicht maßgeblich vom Debuggen einer Anwendung im einfachen Modus. Beachten Sie jedoch einige besondere Aspekte.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Aktivieren von "Bearbeiten und Fortfahren" in C++ beim Debuggen im gemischten Modus  

Zum Aktivieren von "Bearbeiten und Fortfahren" für C++ finden Sie unter [aktivieren und Deaktivieren von bearbeiten und Fortfahren](../debugger/how-to-enable-and-disable-edit-and-continue.md).

> [!NOTE]
> Um "Bearbeiten und Fortfahren" für C++ in Visual Studio 2013 zu verwenden, müssen Sie die Legacyversion des Debugmoduls wiederherstellen. Finden Sie unter [Wechsel zu verwalteter Kompatibilitätsmodus in Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) im Microsoft Application Lifecycle Management Blog.  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>Auswertung von Eigenschaften in Anwendungen im gemischten Modus  
 In einer Anwendung im gemischten Modus erfordert die Auswertung von Eigenschaften durch den Debugger sehr viel Rechenleistung. Folglich werden Debugoperationen, z. B. das schrittweise Ausführen, scheinbar langsam ausgeführt. Weitere Informationen finden Sie unter [Stepping](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9). Falls Sie beim Debuggen im gemischten Modus einen Leistungsabfall beobachten, empfiehlt es sich u. U., die Eigenschaftenauswertung in den Debuggerfenstern zu deaktivieren.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
#### <a name="to-turn-off-property-evaluation"></a>So deaktivieren Sie die Eigenschaftenauswertung  
  
1.  Wählen Sie im Menü **Extras** den Befehl **Optionen**.  
  
2.  In der **Optionen** öffnen Sie im Dialogfeld die **Debuggen** Ordner, und wählen die **allgemeine** Kategorie.  
  
3.  Deaktivieren der **eigenschaftenauswertung und andere implizite Funktionsaufrufe** Kontrollkästchen.  
  
 Da systemeigene Aufruflisten sich von verwalteten Aufruflisten unterscheiden, kann der Debugger nicht immer die vollständige Aufrufliste für den gemischten Code bereitstellen. Wenn nativer Code verwalteten Code aufruft, stellen Sie u. U. einige Diskrepanzen fest. Weitere Informationen finden Sie unter [Gemischter Code und fehlende Daten in das Fenster "Aufrufliste"](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)