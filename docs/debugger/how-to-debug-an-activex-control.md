---
title: "Gewusst wie: Debuggen von ActiveX-Steuerelementen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen eines Containers für ActiveX-Steuerelemente [Visual Studio]"
  - "ActiveX-Steuerelemente, Debuggen"
  - "Container, Angeben für Debugsitzungen"
  - "Datengebundene Steuerelemente, ActiveX"
  - "Debuggen von ActiveX-Steuerelementen"
  - "Testcontainer"
  - "Testen [Visual Studio], ActiveX-Steuerelemente"
  - "Testen [Visual Studio], Testcontainer"
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Debuggen von ActiveX-Steuerelementen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Um das ActiveX\-Steuerelement zu debuggen, müssen Sie einen Container \(ausführbare Datei\) angeben, in dem das Steuerelement ausgeführt werden kann.  
  
### So legen Sie einen Container für die Debugsitzung fest  
  
1.  Wählen Sie im Projektmappen\-Explorer das Projekt aus.  
  
2.  Wählen Sie im Menü **Ansicht** die Option **Eigenschaftenseiten** aus.  
  
3.  Öffnen Sie im Dialogfeld **Projekt\-Eigenschaftenseiten** den Ordner **Konfigurationseigenschaften**, und wählen Sie **Debuggen** aus.  
  
4.  Suchen Sie in der Kategorie **Debuggen** die Eigenschaft **Befehl**.  
  
5.  Geben Sie den Pfadnamen für den Container an.  Beispielsweise **C:\\Programme\\Internet Explorer\\IEXPLORE.EXE**.  
  
6.  Wenn Sie Internet Explorer als Container angeben und Active Desktop verwenden, geben Sie `/new`  in das Feld **Befehlsargumente** ein.  
  
7.  Klicken Sie auf **OK**.  
  
     Wenn Sie im Dialogfeld **Projekt\-Eigenschaftenseiten** keinen Container festlegen, können Sie dies zu Beginn der Debugsitzung nachholen.  Falls Sie zum Starten des Debugvorgangs einen Ausführungsbefehl wählen, wird das Dialogfeld [Ausführbare Datei für die Debugsitzung](../debugger/executable-for-debugging-session-dialog-box.md) angezeigt.  Geben Sie den Pfadnamen des Containers im Dialogfeld an.  
  
## Siehe auch  
 [ActiveX\-Steuerelemente](/visual-cpp/mfc/activex-controls)   
 [Testen der Eigenschaften und Ereignisse mit Test Container](/visual-cpp/mfc/testing-properties-and-events-with-test-container)   
 [Debuggen von COM und ActiveX](../debugger/com-and-activex-debugging.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)