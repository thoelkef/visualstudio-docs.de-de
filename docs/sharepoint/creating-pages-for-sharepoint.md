---
title: "Erstellen von Seiten f&#252;r SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Inhaltsseiten [SharePoint-Entwicklung in Visual Studio], Entwerfen"
  - "Masterseiten [SharePoint-Entwicklung in Visual Studio], Entwerfen"
  - "Seitenlayouts [SharePoint-Entwicklung in Visual Studio], Entwerfen"
  - "SharePoint-Entwicklung in Visual Studio, Inhaltsseiten"
  - "SharePoint-Entwicklung in Visual Studio, Masterseiten"
  - "SharePoint-Entwicklung in Visual Studio, Seitenlayouts"
ms.assetid: 57678ed1-841f-45de-a1d3-5f9e233bf3ce
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Erstellen von Seiten f&#252;r SharePoint
  Sie können Anwendungsseiten, Websiteseiten, Gestaltungsvorlagen und Seitenlayouts für eine SharePoint\-Website erstellen.  
  
 Sie können Anwendungsseiten mit einer Vorlage in Visual Studio erstellen.  Websiteseiten, Gestaltungsvorlagen und Seitenlayouts können Sie mithilfe von SharePoint Designer erstellen.  Dann können Sie diese Seiten in Visual Studio importieren, um sie in einem SharePoint\-Projekt zu verwenden.  
  
 Sie können auch die Darstellung und das Verhalten von Seiten mit Cascading Stylesheets, ECMAScript und Designs ändern.  
  
## Typen von SharePoint\-Seiten  
 In der folgenden Tabelle werden die vier Hauptseitentypen einer SharePoint\-Website beschrieben.  
  
|Seitentyp|**Beschreibung**|  
|---------------|----------------------|  
|Anwendungsseiten|Erstellen Sie eine Anwendungsseite, wenn die Seite benutzerdefinierten Code enthalten soll oder von mehreren Websites verwendet wird.  Andernfalls ist wahrscheinlich eine Websiteseite die beste Wahl.|  
|Websiteseiten|Erstellen Sie eine Websiteseite, wenn Sie eine der folgenden Aufgaben ausführen möchten:<br /><br /> -   Die Seite soll einer SharePoint\-Bibliothek hinzugefügt werden.<br />-   Die Seite soll Funktionen hosten können, z. B. dynamische Webparts und Webpartzonen.<br />-   Benutzer sollen die Seite mit SharePoint Designer anpassen können.<br /><br /> Erstellen Sie keine Websiteseite, wenn die Seite benutzerdefinierten Code enthalten soll.  Obwohl Sie einer Websiteseite benutzerdefinierten Code hinzufügen können, wird die Ausführung des Codes beendet, sobald der Benutzer die Seite mit Tools wie dem SharePoint Designer anpasst.|  
|Gestaltungsvorlagen.|Erstellen Sie eine Gestaltungsvorlage, wenn Sie eine allgemeine Struktur für Websiteseiten und Anwendungsseiten definieren möchten.|  
|Seitenlayouts|Seitenlayouts sind spezifisch für [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] und ermöglichen es Ihnen, eine weitergehende allgemeine Struktur für Websiteseiten und Anwendungsseiten zu definieren.|  
  
 Eine Übersicht zu den einzelnen Seitentypen, finden Sie unter [Baustein: Seiten und die Benutzeroberfläche](http://go.microsoft.com/fwlink/?LinkID=182095) und [Gestaltungsvorlagen und Seitenlayouts](http://go.microsoft.com/fwlink/?LinkID=182096).  
  
## Erstellen von Anwendungsseiten  
 Sie können Anwendungsseiten in Visual Studio erstellen, indem Sie einem SharePoint\-Projekt das Element **Anwendungsseite** hinzufügen.  Sie können der Seite Steuerelemente hinzufügen und anschließend die Steuerelementereignisse durch Hinzufügen von Code behandeln.  
  
 Sie können Haltepunkte in der Codedatei der Seite festlegen, den Debugger starten und die Seite ohne zusätzliche Konfigurationsschritte auf einer lokalen SharePoint\-Website testen.  Weitere Informationen finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
## Erstellen von Websiteseiten, Gestaltungsvorlagen und Seitenlayouts  
 Websiteseiten, Gestaltungsvorlagen und Seitenlayouts können Sie mithilfe von SharePoint Designer erstellen.  Anschließend können Sie diese Seiten in Visual Studio importieren.  Importieren Sie die Seiten, wenn Sie die Funktionen zur Bereitstellung oder Quellcodeverwaltung nutzen möchten, die in Visual Studio verfügbar sind.  Weitere Informationen finden Sie unter [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
 Da es schwierig ist, diese Seiten nach dem Import zu ändern, sollten Sie diese Seiten entwerfen, bevor Sie sie importieren.  
  
## Erstellen von Cascading Stylesheets, ECMAScript und Designs  
 Visual Studio stellt keine Vorlagen zum Entwickeln von Cascading Stylesheets \(CSS\), ECMAScript \(JavaScript, JScript\) oder Designdateien für SharePoint\-Websites bereit.  Sie können diese Dateien mit der Anleitung im SharePoint\-SDK oder mit entsprechenden Tools, z. B. SharePoint Designer, erstellen.  
  
 Sie können diese Dateien direkt zur Projektmappe hinzufügen oder die Dateien importieren.  In beiden Fällen müssen Sie die entsprechenden zugeordneten Ordner für jedes Element erstellen, das Sie hinzufügen.  Weitere Informationen zum Erstellen eines zugeordneten Ordners finden Sie unter [Gewusst wie: Hinzufügen und Entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Weitere Informationen zum Erstellen von Cascading Stylesheets, Sie finden [Cascading Stylesheet\-Klassen\-Verwendung in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098).  Weitere Informationen zum Erstellen von JavaScript\- und JScript\-Dateien für eine SharePoint\-Lösung, Sie finden [Installieren einer grundlegenden .aspx\-Seite für ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099).  Weitere Informationen zu Designs, Sie finden. [Baustein: Seiten und die Benutzeroberfläche](http://go.microsoft.com/fwlink/?LinkID=182095)  
  
## Verwandte Themen  
  
|Titel|**Beschreibung**|  
|-----------|----------------------|  
|[Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Beschreibt, wie Anwendungen Seiten hinzugefügt werden: ASPX\-Inhalt, der mit einer SharePoint\-Gestaltungsvorlage zusammengeführt wird.|  
|[Gewusst wie: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md)|Zeigt das Erstellen von ASP.NET\-Seiten, die auf einer SharePoint\-Website ausgeführt werden.|  
|[Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Zeigt, wie Sie eine ASP.NET\-Webseite für eine SharePoint\-Website entwerfen und debuggen.|  
|[Arbeiten mit Visual Web Developer](http://msdn.microsoft.com/de-de/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|Beschreibt die Verwendung des Designers, der angezeigt wird, wenn Sie im Projekt eine Webseite öffnen.|  
  
  