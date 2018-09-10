---
title: Debuggen im gemischten Modus-Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 795b1bf9f2c3d2014e1fa2c4ccd25254a07a70a8
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283313"
---
# <a name="debugging-mixed-mode-applications"></a>Debuggen von Anwendungen im gemischten Modus
Eine Anwendung im gemischten Modus ist eine Anwendung, in der nativer Code (C++) mit verwaltetem Code (z. B. Visual Basic-Code, Visual C#-Code oder verwaltetes C++, das mit der Common Language Runtime ausgeführt wird) kombiniert wird. Das Debuggen von Anwendungen im gemischten Modus erfolgt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] weitestgehend transparent. Es unterscheidet sich nicht maßgeblich vom Debuggen einer Anwendung im einfachen Modus. Beachten Sie jedoch einige besondere Aspekte.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Aktivieren von "Bearbeiten und Fortfahren" in C++ beim Debuggen im gemischten Modus  

Zum Aktivieren von "Bearbeiten und Fortfahren" für C++ finden Sie unter [aktivieren und Deaktivieren von bearbeiten und Fortfahren](../debugger/how-to-enable-and-disable-edit-and-continue.md).

> [!NOTE]
> Um "Bearbeiten und Fortfahren" für C++ in Visual Studio 2013 zu verwenden, müssen Sie die Legacyversion der Debug-Engine wiederherstellen. Finden Sie unter [Switching to Managed Compatibility Mode in Visual Studio 2013](https://blogs.msdn.microsoft.com/devops/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013/) Blog des Microsoft Application Lifecycle Management.  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>Auswertung von Eigenschaften in Anwendungen im gemischten Modus  
 In einer Anwendung im gemischten Modus erfordert die Auswertung von Eigenschaften durch den Debugger sehr viel Rechenleistung. Folglich werden Debugoperationen, z. B. das schrittweise Ausführen, scheinbar langsam ausgeführt. Weitere Informationen finden Sie unter [ausführen in Einzelschritten](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)). Falls Sie beim Debuggen im gemischten Modus einen Leistungsabfall beobachten, empfiehlt es sich u. U., die Eigenschaftenauswertung in den Debuggerfenstern zu deaktivieren.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
#### <a name="to-turn-off-property-evaluation"></a>So deaktivieren Sie die Eigenschaftenauswertung  
  
1.  Wählen Sie im Menü **Extras** den Befehl **Optionen**.  
  
2.  In der **Optionen** öffnen Sie im Dialogfeld die **Debuggen** Ordner, und wählen die **allgemeine** Kategorie.  
  
3.  Deaktivieren der **eigenschaftenauswertung und andere implizite Funktionsaufrufe** Kontrollkästchen.  
  
 Da systemeigene Aufruflisten sich von verwalteten Aufruflisten unterscheiden, kann der Debugger nicht immer die vollständige Aufrufliste für den gemischten Code bereitstellen. Wenn nativer Code verwalteten Code aufruft, stellen Sie u. U. einige Diskrepanzen fest. Weitere Informationen finden Sie unter [Gemischter Code und fehlende Daten in das Fenster "Aufrufliste"](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)