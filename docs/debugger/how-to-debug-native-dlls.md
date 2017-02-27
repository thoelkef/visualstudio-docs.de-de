---
title: "Gewusst wie: Debuggen von systemeigenen DLLs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.dll"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen von DLLs"
  - "DLLs, Debuggen"
  - "Ausführbare Dateien, Angeben für Debugsitzungen"
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Gewusst wie: Debuggen von systemeigenen DLLs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Das Debuggen einer DLL kann über die folgenden Projekte gestartet werden:  
  
-   Über das Projekt, das zum Erstellen der ausführbaren Datei verwendet wurde, durch die die DLL aufgerufen wird.  
  
 \- oder \-  
  
-   Über das Projekt, durch das die DLL selbst erstellt wurde.  
  
 Falls das Projekt, mit dem die ausführbare Datei erstellt wurde, verfügbar ist, starten Sie den Debugvorgang über dieses Projekt.  Sie können dann eine Quelldatei für die DLL öffnen und in dieser Datei Haltepunkte festlegen. Dies gilt auch, wenn die Datei nicht dem Projekt angehört, mit dem die ausführbare Datei erstellt wurde.  Weitere Informationen finden Sie unter [Haltepunkte](http://msdn.microsoft.com/de-de/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
 Wenn Sie den Debugvorgang über das Projekt starten, mit dem die DLL erstellt wird, müssen Sie die ausführbare Datei angeben, die beim Debuggen der DLL verwendet werden soll.  
  
### So legen Sie eine ausführbare Datei für die Debugsitzung fest  
  
1.  Wählen Sie das Projekt, mit dem die DLL erstellt wird, im **Projektmappen\-Explorer** aus.  
  
2.  Wählen Sie im Menü **Ansicht** die Option **Eigenschaftenseiten** aus.  
  
3.  Öffnen Sie im Dialogfeld **Eigenschaftenseiten** den Ordner **Konfigurationseigenschaften**, und wählen Sie die Kategorie **Debuggen** aus.  
  
4.  Geben Sie im Feld **Befehl** den Pfadnamen für den Container an.  Beispielsweise **C:\\Programme\\MeineAnwendung\\MEINEANW.EXE**.  
  
5.  Geben Sie im Feld **Befehlsargumente** die erforderlichen Argumente für die ausführbare Datei an.  
  
 Wenn Sie im Dialogfeld *Project*\-**Eigenschaftenseiten** keine ausführbare Datei angeben, wird zu Beginn der Debugsitzung das Dialogfeld [Ausführbare Datei für die Debugsitzung](../debugger/executable-for-debugging-session-dialog-box.md) angezeigt.  
  
## Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)