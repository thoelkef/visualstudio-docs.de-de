---
title: "Debuggen von Anwendungen im gemischten Modus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Aufruflistenfenster"
  - "Aufruflistenfenster, Debuggen im gemischten Modus"
  - "Debuggen [Visual Studio], Gemischter Modus"
  - "Debuggen von verwaltetem Code, Gemischter Code"
  - "Debuggen im gemischten Modus"
  - "Debuggen im gemischten Modus, Aufrufliste"
  - "Debuggen im gemischten Modus, Eigenschaftenauswertung"
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Debuggen von Anwendungen im gemischten Modus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine Anwendung im gemischten Modus ist eine Anwendung, in der systemeigener Code \(C\+\+\) mit verwaltetem Code \(z. B. Visual Basic\-Code, Visual C\#\-Code oder verwaltetes C\+\+, das mit der Common Language Runtime ausgeführt wird\) kombiniert wird.  Das Debuggen von Anwendungen im gemischten Modus erfolgt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] weitestgehend transparent. Es unterscheidet sich nicht maßgeblich vom Debuggen einer Anwendung im einfachen Modus.  Beachten Sie jedoch einige besondere Aspekte.  
  
## Aktivieren von "Bearbeiten und Fortfahren" in C\+\+ beim Debuggen im gemischten Modus  
  
-   Um "Bearbeiten und Fortfahren" für C\+\+ in Visual Studio 2013 zu verwenden, müssen Sie die Legacyversion des Debugmoduls wiederherstellen.  Siehe [Switching to Managed Compatibility Mode in Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) im Blog "Microsoft Application Lifecycle Management".  
  
## Auswertung von Eigenschaften in Anwendungen im gemischten Modus  
 In einer Anwendung im gemischten Modus erfordert die Auswertung von Eigenschaften durch den Debugger sehr viel Rechenleistung.  Folglich werden Debugoperationen, z. B. das schrittweise Ausführen, scheinbar langsam ausgeführt.  Weitere Informationen finden Sie unter [Ausführen in Einzelschritten](http://msdn.microsoft.com/de-de/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  Falls Sie beim Debuggen im gemischten Modus einen Leistungsabfall beobachten, empfiehlt es sich u. U., die Eigenschaftenauswertung in den Debuggerfenstern zu deaktivieren.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
#### So deaktivieren Sie die Eigenschaftenauswertung  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Öffnen Sie im Dialogfeld **Optionen** den Ordner **Debuggen**, und wählen Sie die Kategorie **Allgemein** aus.  
  
3.  Deaktivieren Sie das Kontrollkästchen **Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen**.  
  
 Da systemeigene Aufruflisten sich von verwalteten Aufruflisten unterscheiden, kann der Debugger nicht immer die vollständige Aufrufliste für den gemischten Code bereitstellen.  Wenn systemeigener Code verwalteten Code aufruft, stellen Sie u. U. einige Diskrepanzen fest.  Weitere Informationen finden Sie unter [Gemischter Code und fehlende Daten im Fenster "Aufrufliste"](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)