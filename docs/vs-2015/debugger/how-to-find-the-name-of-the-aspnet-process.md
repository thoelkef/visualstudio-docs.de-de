---
title: 'Vorgehensweise: Suchen des Namens des ASP.NET-Prozesses | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 53072013c1665687262d30f4a0c2720641c920be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685964"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Gewusst wie: Herausfinden des ASP.NET-Prozessnamens
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Für das Anhängen an eine ausgeführte [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Anwendung müssen Sie den Namen des [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Prozesses kennen.  
  
- Wenn Sie IIS 6.0 oder IIS 7.0 ausführen, lautet der Name "w3wp.exe".  
  
- Wenn Sie eine frühere Version von IIS ausführen, lautet der Name aspnet_wp.exe.  
  
  Bei Anwendungen [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] , die mit oder höheren Versionen erstellt wurden, kann sich der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Code im Dateisystem befinden und unter dem Testserver WebDev.WebServer.exe ausgeführt werden. In diesem Fall müssen Sie den Debugger an WebDev.WebServer.exe und nicht an den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Prozess anhängen. Dieses Szenario gilt nur für lokales Debuggen.  
  
  Ältere ASP-Anwendungen werden innerhalb des IIS-Prozesses inetinfo.exe ausgeführt, sobald sie prozessintern laufen.  
  
> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>So stellen Sie fest, ob sich Projektcode im Dateisystem oder auf IIS befindet  
  
1. Öffnen Sie in Visual Studio **Projektmappen-Explorer** , wenn es nicht bereits geöffnet ist.  
  
2. Wählen Sie den obersten Knoten aus, der den Namen der Anwendung enthält.  
  
3. Wenn der Titel des **Eigenschaften** Fensters einen Dateipfad enthält, befindet sich der Anwendungscode im Dateisystem.  
  
     Andernfalls enthält der Titel des **Eigenschaften** Fensters den Namen der Website.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>So stellen Sie die IIS-Version fest, unter der die Anwendung ausgeführt wird  
  
1. Suchen Sie die **Verwaltungs Tools** , und führen Sie Sie aus. Je nach Betriebssystem ist dies möglicherweise ein Symbol in der **Systemsteuerung**oder ein Menüeintrag, der angezeigt wird, wenn Sie auf **Start**klicken.  
  
     In Windows XP kann die **Systemsteuerung** in der Kategorieansicht oder in der klassischen Ansicht angezeigt werden. Klicken Sie in der Kategorieansicht auf **zur klassischen Ansicht wechseln** oder auf **Leistung und Wartung** , um das Symbol **Verwaltungs Tools** anzuzeigen.  
  
2. Führen Sie Internetinformationsdienste aus der **Verwaltungs Tools**aus. Ein MMC-Dialogfeld wird geöffnet.  
  
3. Wenn im linken Bereich mehr als ein Computer aufgeführt wird, wählen Sie den Computer aus, auf dem sich der Anwendungscode befindet.  
  
4. Die IIS-Version befindet sich in der Spalte **Version** des rechten Bereichs.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Voraussetzungen für das Remote Debuggen von Webanwendungen](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md)   
 [Debuggen von ASP.net wird vorbereitet](../debugger/preparing-to-debug-aspnet.md)   
 [Debuggen von Webanwendungen und Skripts](../debugger/debugging-web-applications-and-script.md)
