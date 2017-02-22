---
title: "Gewusst wie: Herausfinden des ASP.NET-Prozessnamens | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
helpviewer_keywords: 
  - "ASP.NET-Debuggen, ASP.NET-Prozess"
  - "ASP.NET-Prozess"
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Herausfinden des ASP.NET-Prozessnamens
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Für das Anhängen an eine ausgeführte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Anwendung müssen Sie den Namen des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Prozesses kennen.  
  
-   Wenn Sie IIS 6.0 oder IIS 7.0 ausführen, lautet der Name "w3wp.exe".  
  
-   Wenn Sie eine frühere Version von IIS ausführen, lautet der Name aspnet\_wp.exe.  
  
 Bei Anwendungen, die mit [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] oder höheren Versionen erstellt wurden, kann sich der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Code im Dateisystem befinden und unter dem Testserver WebDev.WebServer.exe ausgeführt werden.  In diesem Fall müssen Sie den Debugger an WebDev.WebServer.exe und nicht an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Prozess anhängen.  Dieses Szenario gilt nur für lokales Debuggen.  
  
 Ältere ASP\-Anwendungen werden innerhalb des IIS\-Prozesses inetinfo.exe ausgeführt, sobald sie prozessintern laufen.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### So stellen Sie fest, ob sich Projektcode im Dateisystem oder auf IIS befindet  
  
1.  Öffnen Sie in Visual Studio den **Projektmappen\-Explorer**, sofern er noch nicht geöffnet ist.  
  
2.  Wählen Sie den obersten Knoten aus, der den Namen der Anwendung enthält.  
  
3.  Wenn der Titel des **Eigenschaftenfensters** einen Pfad zu einer Datei enthält, befindet sich der Anwendungscode im Dateisystem.  
  
     Andernfalls enthält der Titel des **Eigenschaftenfensters** den Namen der Website.  
  
### So stellen Sie die IIS\-Version fest, unter der die Anwendung ausgeführt wird  
  
1.  Öffnen Sie **Verwaltung**.  Je nach Ihrem Betriebssystem ist dies entweder ein Symbol in der **Systemsteuerung** oder ein Menüeintrag, der beim Klicken auf die Schaltfläche **Start** angezeigt wird.  
  
     In Windows XP kann die **Systemsteuerung** in der Kategorieansicht oder in der klassischen Ansicht angezeigt werden.  Klicken Sie in der Kategorieansicht auf **Zur klassischen Ansicht wechseln** oder **Leistung und Wartung**, um das Symbol **Verwaltung** anzuzeigen.  
  
2.  Führen Sie aus **Verwaltung** die Internetinformationsdienste aus.  Ein MMC\-Dialogfeld wird geöffnet.  
  
3.  Wenn im linken Bereich mehr als ein Computer aufgeführt wird, wählen Sie den Computer aus, auf dem sich der Anwendungscode befindet.  
  
4.  Die IIS\-Version können Sie der Spalte **Version** im rechten Bereich entnehmen.  
  
## Siehe auch  
 [Voraussetzungen für das Remotedebuggen von Webanwendungen](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md)   
 [Vorbereitungen zum Debuggen von ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Debuggen von Webanwendungen und Skripts](../debugger/debugging-web-applications-and-script.md)