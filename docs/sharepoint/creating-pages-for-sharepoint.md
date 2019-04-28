---
title: Erstellen von Seiten für SharePoint | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f58af55b18d7cd6341b779d71da2994875c98a62
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62419884"
---
# <a name="create-pages-for-sharepoint"></a>Erstellen von Seiten für SharePoint
  Sie können die Anwendungsseiten, Websiteseiten, Gestaltungsvorlagen und Seitenlayouts für eine SharePoint-Website erstellen.

 Anwendungsseiten können Sie mithilfe einer Vorlage in Visual Studio erstellen. Erstellen von Websiteseiten, Gestaltungsvorlagen und Seitenlayouts mit SharePoint Designer. Anschließend können Sie diese Seiten in Visual Studio Ihre Verwendung in einem SharePoint-Projekt importieren.

 Sie können auch das Aussehen und Verhalten der Seiten, die mithilfe von cascading Stylesheets, ECMAScript und Designs ändern.

## <a name="types-of-sharepoint-pages"></a>Typen von SharePoint-Seiten
 Die folgende Tabelle beschreibt die vier wichtigsten Typen von Seiten, die eine SharePoint-Website enthält.

|Seitentyp|Beschreibung|
|---------------|-----------------|
|Anwendungsseiten|Erstellen Sie eine Anwendungsseite, wenn Sie die Seite, um benutzerdefinierten Code enthalten oder die Seite für mehrere Standorte freigegeben werden soll. Andernfalls kann eine Seite "Website" die beste Wahl sein.|
|Seiten der Website|Erstellen Sie eine Seite "Website", wenn Sie eine der folgenden Aufgaben ausführen möchten:<br /><br /> -Fügen Sie die Seite in einer SharePoint-Bibliothek hinzu.<br />-Aktivieren Sie die Seite, um den Hostfeatures wie dynamisches Webparts und Webpartzonen.<br />-Aktivieren Sie Benutzer auf die Seite anpassen, indem Sie mithilfe von SharePoint Designer.<br /><br /> Eine Seite "Website" kann nicht erstellt werden, wenn Sie die benutzerdefinierten Code enthalten soll. Obwohl Sie benutzerdefinierten Code auf einer Webseite hinzufügen können, beendet der Code ausgeführt, wenn der Benutzer die Seite mit SharePoint Designer anpasst.|
|Masterseiten|Erstellen Sie eine Masterseite, wenn Sie eine gemeinsame Struktur für die Seiten der Website zu definieren möchten und Anwendungsseiten.|
|Seitenlayouts|Seitenlayouts sind spezifisch für [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] und ermöglichen es Ihnen, eine gemeinsame Struktur für die Seiten der Website und Anwendungsseiten genauer zu definieren.|

 Eine Übersicht über jede Seite, finden Sie unter [Baustein: Seiten und die Benutzeroberfläche](http://go.microsoft.com/fwlink/?LinkID=182095), und [Seite Layouts und Masterseiten](http://go.microsoft.com/fwlink/?LinkID=182096).

## <a name="create-application-pages"></a>Erstellen von Anwendungsseiten
 Sie können die Anwendungsseiten in Visual Studio erstellen, durch das Hinzufügen einer **Anwendungsseite** einem SharePoint-Projekt. Hinzufügen von Steuerelementen auf der Seite, und klicken Sie dann Behandeln von Ereignissen durch Hinzufügen von Code.

 Sie können Haltepunkte in der Codedatei der Seite, starten Sie den Debugger und die Seite in einer lokalen SharePoint-Website testen, ohne alle zusätzlichen Konfigurationsschritte auszuführen. Weitere Informationen finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Erstellen von Websiteseiten, Gestaltungsvorlagen und Seitenlayouts
 Sie können die Websiteseiten, Gestaltungsvorlagen und Seitenlayouts mit SharePoint Designer erstellen. Anschließend können Sie diese Seiten in Visual Studio importieren. Importieren Sie Ihre Seiten, sollten Sie nutzen die bereitstellungs- noch die Quellcodeverwaltungsfunktionen, die in Visual Studio verfügbar sind. Weitere Informationen finden Sie unter [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Da es schwierig ist, diese Seiten zu ändern, nachdem Sie diese importieren, sollten Sie diese Seiten entwerfen, bevor Sie sie importieren.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Erstellen von cascading Stylesheets, ECMAScript und Designs
 Visual Studio stellt keine Vorlagen Entwickeln von Cascading Stylesheets (CSS) ECMAScript (JavaScript, JScript) oder Dateien für SharePoint-Websites bereit. Sie können diese Dateien anhand der Anleitungen im SharePoint SDK oder mit Tools wie SharePoint Designer erstellen.

 Sie können diese Dateien direkt der Projektmappe hinzufügen, oder Sie können Sie importieren. In beiden Fällen müssen Sie die entsprechenden zugeordneten Ordner für jedes Element erstellen, die Sie hinzufügen. Weitere Informationen zum Erstellen eines zugeordneten Ordners finden Sie unter [Vorgehensweise: Hinzufügen und entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Weitere Informationen zum Erstellen von Cascading Style Sheets finden Sie unter [Cascading Style Sheets Klasse Usage in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098). Weitere Informationen zum Erstellen von JavaScript und JScript-Dateien für eine SharePoint-Lösung finden Sie unter [Setting Up a Basic ASPX Page für ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099). Weitere Informationen zu Designs finden Sie unter [Baustein: Seiten und die Benutzeroberfläche](http://go.microsoft.com/fwlink/?LinkID=182095).

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Beschreibt das Hinzufügen von Anwendungsseiten: *aspx* Inhalte, die mit einer SharePoint-Masterseite zusammengeführt wird.|
|[Vorgehensweise: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md)|Erfahren Sie, wie ASP.NET-Seiten zu erstellen, die auf einer SharePoint-Website ausgeführt.|
|[Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Erfahren Sie, wie das Entwerfen und Debuggen einer ASP.NET-Webseite für eine SharePoint-Website.|
