---
title: "Erstellen von Seiten für SharePoint | Microsoft Docs"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4b65c601d36dd04d95466fc8f8dff7a95b70c44a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="creating-pages-for-sharepoint"></a>Erstellen von Seiten für SharePoint
  Sie können die Anwendungsseiten, Websiteseiten, Gestaltungsvorlagen und Seitenlayouts für eine SharePoint-Website erstellen.  
  
 Sie können Anwendungsseiten mithilfe einer Vorlage in Visual Studio erstellen. Erstellen Sie mithilfe von SharePoint Designer Websiteseiten, Gestaltungsvorlagen und Seitenlayouts. Anschließend können Sie diese Seiten in Visual Studio Ihre Verwendung in einem SharePoint-Projekt importieren.  
  
 Sie können auch das Aussehen und Verhalten der Seiten, die mithilfe von cascading Stylesheets, ECMAScript und Designs ändern.  
  
## <a name="types-of-sharepoint-pages"></a>Typen von SharePoint-Seiten  
 Die folgende Tabelle beschreibt die vier Haupttypen der Seiten, die eine SharePoint-Website enthält.  
  
|Seitentyp|Beschreibung|  
|---------------|-----------------|  
|Anwendungsseiten|Erstellen Sie eine Anwendungsseite, wenn Sie die Seite, um benutzerdefinierten Code enthalten oder die Seite für mehrere Standorte freigegeben werden soll. Andernfalls möglicherweise eine Websiteseite die beste Wahl.|  
|Seiten der Website|Erstellen Sie eine Websiteseite, wenn Sie eine der folgenden Aufgaben ausführen möchten:<br /><br /> -Die Seite in einer SharePoint-Bibliothek hinzufügen.<br />-Aktivieren Sie die Seite "auf Host-Funktionen wie dynamische Webparts und Web Teil Zonen.<br />-Benutzer auf der Seite anpassen, indem Sie mit SharePoint Designer zu aktivieren.<br /><br /> Eine Websiteseite kann nicht erstellt werden, wenn Sie die Seite benutzerdefinierten Code enthalten soll. Obwohl Sie eine Websiteseite benutzerdefinierten Code hinzufügen können, wird der Code ausgeführt, wenn der Benutzer die Seite passt, indem Sie mit SharePoint Designer beendet.|  
|Masterseiten|Erstellen einer Masterseite, wenn Sie eine gemeinsame Struktur für die Seiten der Website definieren möchten und Anwendungsseiten.|  
|Seitenlayouts|Seitenlayouts sind spezifisch für [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] und ermöglichen es Ihnen, eine gemeinsame Struktur für Websiteseiten und Anwendungsseiten genauer zu definieren.|  
  
 Einen Überblick über jeden Typ von Seite finden Sie unter [Baustein: Seiten und die Benutzeroberfläche](http://go.microsoft.com/fwlink/?LinkID=182095), und [Seitenlayouts und Masterseiten](http://go.microsoft.com/fwlink/?LinkID=182096).  
  
## <a name="creating-application-pages"></a>Erstellen von Anwendungsseiten  
 Sie können Anwendungsseiten in Visual Studio erstellen, durch Hinzufügen von ein **Seite "Anwendung"** einem SharePoint-Projekt. Sie können Steuerelemente auf der Seite hinzufügen und Behandeln von Steuerelementereignissen dann durch Hinzufügen von Code.  
  
 Festlegen von Haltepunkten in der Codedatei der Seite, starten Sie den Debugger und die Seite auf einer lokalen SharePoint-Website testen, ohne alle zusätzlichen Konfigurationsschritte ausführen. Weitere Informationen finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
## <a name="creating-site-pages-master-pages-and-page-layouts"></a>Erstellen von Websiteseiten, Gestaltungsvorlagen und Seitenlayouts  
 Sie können Websiteseiten, Gestaltungsvorlagen und Seitenlayouts mithilfe von SharePoint Designer erstellen. Anschließend können Sie diese Seiten in Visual Studio importieren. Importieren Sie Ihre Seiten gegebenenfalls nutzen Sie die Bereitstellung oder die Funktionen der quellcodeverwaltung, die in Visual Studio verfügbar sind. Weitere Informationen finden Sie unter [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
 Da es schwierig ist, diese Seiten zu ändern, nachdem Sie diese importieren, sollten Sie diese Seiten entwerfen, bevor Sie sie importieren.  
  
## <a name="creating-cascading-style-sheets-ecmascript-and-themes"></a>Erstellen von Cascading Stylesheets, ECMAScript und Designs  
 Visual Studio stellt keine Vorlagen für Entwicklung Cascading Style Sheets (CSS), ECMAScript (JavaScript, JScript) oder Designdateien für SharePoint-Websites bereit. Sie können diese Dateien anhand der Anleitungen im SharePoint-SDK oder mithilfe von Tools wie SharePoint Designer erstellen.  
  
 Sie können diese Dateien direkt zur Projektmappe hinzufügen, oder Sie importieren können. In beiden Fällen müssen Sie die entsprechenden zugeordneten Ordner für jedes Element erstellen, die Sie hinzufügen. Weitere Informationen dazu, wie Sie einen zugeordneten Ordner erstellen, finden Sie unter [wie: Hinzufügen und Entfernen von zugeordneten Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Weitere Informationen zum Erstellen von Cascading Stylesheets, finden Sie unter [Cascading Style Sheets Class Usage in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098). Weitere Informationen zum Erstellen von JavaScript und JScript-Dateien für eine SharePoint-Lösung finden Sie unter [Einstellung Einrichten eines grundlegenden ASPX-Seite für ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099). Weitere Informationen zu Designs finden Sie unter [Baustein: Seiten und die Benutzeroberfläche](http://go.microsoft.com/fwlink/?LinkID=182095).  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Beschreibt, wie Anwendungsseiten hinzufügen: aspx-Inhalt, der mit einer SharePoint-Masterseite zusammengeführt wird.|  
|[Vorgehensweise: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md)|Zeigt, wie ASP.NET-Seiten erstellen, die auf einer SharePoint-Website ausgeführt.|  
|[Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Zeigt, wie das Entwerfen und Debuggen einer ASP.NET-Webseite für eine SharePoint-Website.|  
  
  