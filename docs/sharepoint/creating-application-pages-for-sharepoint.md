---
title: "Erstellen von Anwendungsseiten für SharePoint | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
ms.assetid: a6e97149-15dd-4bdb-8d75-3b53f886f76c
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 858df05759f1c3b4205d4cbcd0bbad2cdfb6e034
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="creating-application-pages-for-sharepoint"></a>Erstellen von Anwendungsseiten für SharePoint
  Ein *Seite "Anwendung"* ist eine ASP.NET-Webseite, die für die Verwendung in einer SharePoint-Website entwickelt wurde. Anwendungsseiten sind ein spezialisierter Typ von ASP.NET-Seite. Der Hauptunterschied zwischen einer Anwendungsseite und einer standardmäßigen ASP.NET-Seite ist, dass eine Anwendungsseite Inhalt enthält, die mit einer SharePoint-Masterseite zusammengeführt wird. Eine Masterseite ermöglicht dienstanwendungsseiten, um das gleiche Erscheinungsbild und Verhalten wie andere Seiten auf einer Website freigeben.  
  
 Visual Studio ermöglicht Ihnen Anwendungsseiten, die mit einem Designer entworfen. Der Designer zeigt einen Inhaltsbereich für jeden Inhaltsplatzhalter, die auf einer Masterseite definiert ist. Sie können die Seite "Anwendung" durch Ziehen von Steuerelementen in diese Inhaltsbereiche entwerfen.  
  
## <a name="application-pages"></a>Anwendungsseiten  
 Anwendungsseiten sind in allen Standorten auf dem Server freigegeben, während eine Websiteseite mit einem Standort spezifisch ist. Weitere Informationen [SharePoint Seitentypen](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
 Standardmäßig sind die meisten der Seiten, die beim Erstellen einer SharePoint-Websites angezeigt Seiten der Website. Eine Websiteseite kann in einer SharePoint-Seite-Bibliothek hinzugefügt werden. Benutzer können eine Websiteseite mit Tools wie SharePoint Designer anpassen. Eine Websiteseite kann auch Funktionen wie dynamische Webparts und Web Teil Zonen hosten.  
  
 Anwendungsseiten können nicht die folgenden Schritte ausführen. Eine Anwendungsseite ist jedoch die beste Typ zu erstellen, wenn Sie die Seite benutzerdefinierten Code enthalten soll. Obwohl Sie eine Websiteseite benutzerdefinierten Code hinzufügen können, wird der Code ausgeführt, wenn der Benutzer die Seite passt, mithilfe von Tools wie z. B. SharePoint Designer beendet.  
  
> [!NOTE]  
>  Visual Studio bietet keine Vorlagen, mit denen Sie Seiten der Website für eine SharePoint-Website zu erstellen. Weitere Informationen finden Sie unter [SharePoint Seitentypen](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
## <a name="creating-an-application-page"></a>Erstellen einer Anwendungsseite  
 Fügen Sie zum Erstellen einer Anwendungsseite einer **Anwendungsseite** einem SharePoint-Projekt. Wenn Sie eine Anwendungsseite erstellen, fügt Visual Studio die folgenden Ordner zu Ihrem Projekt hinzu:  
  
|Ordner|Beschreibung|  
|------------|-----------------|  
|Layouts|Zuordnungen zum virtuellen Verzeichnis _layouts des SharePoint-Dateisystems.|  
|Unterordner Layouts|Enthält die Dateien, aus denen die Seite "Anwendung" besteht. Standardmäßig ist dieser Ordner den gleichen Namen wie das Projekt. Sie können diesen Ordner jedoch jederzeit umbenennen. Wenn Sie das Projekt ausführen, stellt Visual Studio diesen Ordner zum virtuellen Verzeichnis des Dateisystems SharePoint _layouts bereit.|  
  
 Visual Studio fügt die folgenden Dateien zum Projekt hinzu:  
  
|Datei|Beschreibung|  
|----------|-----------------|  
|Datei der ASP.NET-Seite (.aspx)|Enthält XML-Markup, das die Seite definiert.|  
|Die Codedatei Anwendungsseite|Enthält die CodeBehind-Seite "Anwendung". Fügen Sie Code, der Ereignisse in dieser Datei behandelt.|  
|Application-Designer-Codedatei|Enthält Code, der vom Designer generiert wird. Bearbeiten Sie diese Datei nicht direkt.|  
  
## <a name="designing-and-debugging-an-application-page"></a>Entwerfen und Debuggen einer Anwendungsseite  
 Entwerfen Sie den Inhalt einer Anwendungsseite mithilfe der Designeransicht in Visual Studio. Dieser Designer wird angezeigt, wenn Sie die Seite "Anwendung" in Ihrem Projekt öffnen (indem Sie darauf doppelklicken oder indem Sie das Kontextmenü öffnen und auswählen, **öffnen**) und wählen Sie dann die **Entwurf** Schaltfläche am unteren Rand der Editor.  
  
> [!NOTE]  
>  Sie können die Seite entwerfen nur in der **Quelle** Ansicht des Designers. Die **Entwurf** Ansicht des Designers für Anwendungsseiten deaktiviert ist.  
  
 Sie können eine Anwendungsseite Debuggen, ebenso wie andere SharePoint-Projektelemente in Visual Studio debuggen. Wenn Sie den Visual Studio-Debugger starten, wird von Visual Studio die SharePoint-Website geöffnet.  
  
 Um die Seite "Anwendung" anzuzeigen, müssen Sie manuell auf den Speicherort der Seite "Anwendung" navigieren (zum Beispiel: http://*Server_Name*/_layouts /*Project_Name*  /ApplicationPage1.aspx).  
  
 Weitere Informationen zum Debuggen von SharePoint-Projekten finden Sie unter [SharePoint-Lösungen zur Problembehandlung](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="choosing-a-master-page"></a>Auswählen einer Masterseite  
 Wird standardmäßig ein **Anwendungsseite** Element verweist auf die Gestaltungsvorlage der Site, die Sie verwenden, um das Debuggen des Projekts. Seite heißt v4.master und können dort aufgeführt, die der **Master Page Gallery** der SharePoint-Website.  
  
 Sie können explizit ändern, welche Masterseite von der Seite "Anwendung" verwendet wird, durch Festlegen der `MasterPageFile` Attribut der Anwendung `Page` Element. (Zum Beispiel: `MasterPageFile="~/_layouts/applicationv4.master"`). Tatsächlich müssen Sie dieses Attribut festlegen, wenn dynamische Masterseiten nicht auf dem SharePoint-Server aktiviert sind. Weitere Informationen zu master Seiten in SharePoint finden Sie unter [Masterseiten](http://go.microsoft.com/fwlink/?LinkID=169281).  
  
## <a name="see-also"></a>Siehe auch  
 [SharePoint Foundation-Entwicklung im Detail](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [Übersicht über ASP.NET](/aspnet/overview)   
 [ASP.NET-Webseiten 2](/aspnet/web-pages/index)   
  
  