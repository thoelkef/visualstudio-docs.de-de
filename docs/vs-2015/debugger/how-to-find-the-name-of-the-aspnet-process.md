---
title: 'Vorgehensweise: herausfinden des ASP.NET-Prozessnamens | Microsoft-Dokumentation'
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
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6b036fdd9f75afc0c9976591ae0df23194b196d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268904"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Gewusst wie: Herausfinden des ASP.NET-Prozessnamens
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Für das Anhängen an eine ausgeführte [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Anwendung müssen Sie den Namen des [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Prozesses kennen.  
  
-   Wenn Sie IIS 6.0 oder IIS 7.0 ausführen, lautet der Name "w3wp.exe".  
  
-   Wenn Sie eine frühere Version von IIS ausführen, lautet der Name aspnet_wp.exe.  
  
 Für Anwendungen, die mithilfe von [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] oder höheren Versionen der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Code befinden sich auf das Dateisystem und unter dem Testserver WebDev.WebServer.exe ausgeführt werden kann. In diesem Fall müssen Sie den Debugger an WebDev.WebServer.exe und nicht an den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Prozess anhängen. Dieses Szenario gilt nur für lokales Debuggen.  
  
 Ältere ASP-Anwendungen werden innerhalb des IIS-Prozesses inetinfo.exe ausgeführt, sobald sie prozessintern laufen.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>So stellen Sie fest, ob sich Projektcode im Dateisystem oder auf IIS befindet  
  
1.  Öffnen Sie in Visual Studio **Projektmappen-Explorer** , wenn es nicht bereits geöffnet ist.  
  
2.  Wählen Sie den obersten Knoten aus, der den Namen der Anwendung enthält.  
  
3.  Wenn die **Eigenschaften** Fenstertitel einen Dateipfad enthält, die der Anwendungscode befindet sich im Dateisystem.  
  
     Andernfalls die **Eigenschaften** Fenstertitel enthält den Namen der Website.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>So stellen Sie die IIS-Version fest, unter der die Anwendung ausgeführt wird  
  
1.  Suchen **Verwaltung** und führen Sie sie. Je nach Betriebssystem, dies ist möglicherweise ein Symbol in **Systemsteuerung**, oder ein Menüeintrag, der angezeigt wird, wenn Sie auf **starten**.  
  
     In Windows XP **Systemsteuerung** in Kategorieansicht oder in der Standardansicht werden können. In der Kategorieansicht auf klicken, werden Ihnen **zur klassischen Ansicht wechseln** oder **Leistung und Wartung** , finden Sie unter den **Verwaltung** Symbol.  
  
2.  Von **Verwaltung**, führen Sie Internet Information Services. Ein MMC-Dialogfeld wird geöffnet.  
  
3.  Wenn im linken Bereich mehr als ein Computer aufgeführt wird, wählen Sie den Computer aus, auf dem sich der Anwendungscode befindet.  
  
4.  Die IIS-Version befindet sich in der **Version** Spalte im rechten Bereich.  
  
## <a name="see-also"></a>Siehe auch  
 [Voraussetzungen für das Remotedebuggen von Webanwendungen](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md)   
 [Vorbereitung zum Debuggen von ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Debuggen von Webanwendungen und Skripts](../debugger/debugging-web-applications-and-script.md)



