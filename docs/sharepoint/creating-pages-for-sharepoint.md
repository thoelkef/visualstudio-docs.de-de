---
title: Erstellen von Seiten für SharePoint | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: overview
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
ms.openlocfilehash: 942891bc9281c07966160ea9df065408fcbfd5ff
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015162"
---
# <a name="create-pages-for-sharepoint"></a>Erstellen von Seiten für SharePoint
  Sie können Anwendungs Seiten, Website Seiten, Masterseiten und Seitenlayouts für eine SharePoint-Website erstellen.

 Sie können Anwendungs Seiten mithilfe einer Vorlage in Visual Studio erstellen. Erstellen Sie mithilfe von SharePoint Designer Website Seiten, Masterseiten und Seitenlayouts. Anschließend können Sie diese Seiten in Visual Studio importieren, um Sie in einem SharePoint-Projekt zu verwenden.

 Sie können auch die Darstellung und das Verhalten von Seiten mithilfe von Cascading Stylesheets, ECMAScript und Designs ändern.

## <a name="types-of-sharepoint-pages"></a>Typen von SharePoint-Seiten
 In der folgenden Tabelle werden die vier Haupttypen von Seiten beschrieben, die eine SharePoint-Website enthält.

|Seitentyp|BESCHREIBUNG|
|---------------|-----------------|
|Anwendungs Seiten|Erstellen Sie eine Anwendungsseite, wenn die Seite benutzerdefinierten Code enthalten soll oder wenn die Seite für mehrere Websites freigegeben werden soll. Andernfalls ist eine Website Seite möglicherweise die beste Wahl.|
|Website Seiten|Erstellen Sie eine Website Seite, wenn Sie eine der folgenden Aufgaben ausführen möchten:<br /><br /> -Hinzufügen der Seite zu einer SharePoint-Bibliothek.<br />-Aktivieren Sie die Seite, um Funktionen wie dynamische Webparts und Webpartzonen zu hosten.<br />-Ermöglicht Benutzern das Anpassen der Seite mithilfe von SharePoint Designer.<br /><br /> Erstellen Sie keine Website Seite, wenn die Seite benutzerdefinierten Code enthalten soll. Obwohl Sie benutzerdefinierten Code zu einer Website Seite hinzufügen können, wird der Code nicht mehr ausgeführt, wenn der Benutzer die Seite mithilfe von SharePoint Designer anpasst.|
|Master Seiten|Erstellen Sie eine Master Seite, wenn Sie eine gemeinsame Struktur für Website Seiten und Anwendungs Seiten definieren möchten.|
|Seitenlayouts|Seitenlayouts sind spezifisch für [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] und ermöglichen es Ihnen, eine gemeinsame Struktur für Website Seiten und Anwendungs Seiten weiter zu definieren.|

 Eine Übersicht über die einzelnen Seiten Typen finden Sie unter [Baustein: Seiten und Benutzeroberfläche](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14))sowie Seiten [Layouts und Master Seiten](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14)).

## <a name="create-application-pages"></a>Erstellen von Anwendungs Seiten
 Sie können Anwendungs Seiten in Visual Studio erstellen, indem Sie einem SharePoint-Projekt ein **Anwendungs Seiten** Element hinzufügen. Sie können der Seite Steuerelemente hinzufügen und anschließend Steuerelement Ereignisse behandeln, indem Sie Code hinzufügen.

 Sie können in der Codedatei der Seite Breakpoints festlegen, den Debugger starten und die Seite auf einer lokalen SharePoint-Website testen, ohne zusätzliche Konfigurationsschritte auszuführen. Weitere Informationen finden Sie unter [Erstellen von Anwendungs Seiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Erstellen von Website Seiten, Masterseiten und Seitenlayouts
 Sie können mithilfe von SharePoint Designer Website Seiten, Masterseiten und Seitenlayouts erstellen. Anschließend können Sie diese Seiten in Visual Studio importieren. Importieren Sie Ihre Seiten, wenn Sie die in Visual Studio verfügbaren Funktionen für die Bereitstellung oder die Quell Code Verwaltung nutzen möchten. Weitere Informationen finden Sie unter [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Da es schwierig ist, diese Seiten nach dem Importieren zu ändern, sollten Sie diese Seiten vor dem Importieren entwerfen.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Erstellen von Cascading Stylesheets, ECMAScript und Designs
 Visual Studio stellt keine Vorlagen zum Entwickeln von Cascading Stylesheets (CSS), ECMAScript (JavaScript, JScript) oder Designdateien für SharePoint-Websites bereit. Sie können diese Dateien mit dem Leitfaden erstellen, der im SharePoint-SDK oder mithilfe von Tools wie SharePoint Designer verfügbar ist.

 Sie können diese Dateien direkt Ihrer Projekt Mappe hinzufügen, oder Sie können Sie importieren. In jedem Fall müssen Sie die entsprechenden zugeordneten Ordner für jedes Element erstellen, das Sie hinzufügen. Weitere Informationen zum Erstellen eines zugeordneten Ordners finden Sie unter Gewusst [wie: Hinzufügen und entfernen](../sharepoint/how-to-add-and-remove-mapped-folders.md)von zugeordneten Ordnern.

 Weitere Informationen zum Erstellen von Cascading Stylesheets finden Sie unter [Cascading Stylesheets Class Usage in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14)). Weitere Informationen zum Erstellen von JavaScript-und JScript-Dateien für eine SharePoint-Lösung finden [Sie unter Einrichten einer einfachen ASPX-Seite für ECMAScript](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14)). Weitere Informationen zu Designs finden Sie unter [Baustein: Seiten und die Benutzeroberfläche](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)).

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Erstellen von Anwendungs Seiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Hier wird beschrieben, wie Anwendungs Seiten hinzugefügt werden: *aspx* -Inhalte, die mit einer SharePoint-Master Seite zusammengeführt werden.|
|[Vorgehensweise: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md)|Zeigt, wie Sie ASP.NET-Seiten erstellen, die auf einer SharePoint-Website ausgeführt werden.|
|[Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Zeigt, wie Sie eine ASP.NET-Webseite für eine SharePoint-Website entwerfen und Debuggen.|
