---
title: "Outlook-Projektmappen"
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
  - "Projektmappen [Office-Entwicklung in Visual Studio], Outlook"
  - "Office-Projekte [Office-Entwicklung in Visual Studio], Outlook"
  - "Office-Projektmappen [Office-Entwicklung in Visual Studio], Outlook"
  - "Projektmappen [Office-Entwicklung in Visual Studio], Outlook"
  - "Projekte [Office-Entwicklung in Visual Studio], Outlook"
  - "Outlook [Office-Entwicklung in Visual Studio]"
  - "E-Mail [Office-Entwicklung in Visual Studio], Outlook-Projektmappen"
ms.assetid: 2ae3cd9c-bf31-4efa-8b18-b6b1c34a8d93
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Outlook-Projektmappen
  Visual Studio stellt Projektvorlagen bereit, die Sie zum Erstellen von VSTO\-Add\-Ins für Microsoft Office Outlook verwenden können. Mit VSTO\-Add\-Ins können Sie Outlook automatisieren, Outlook\-Features erweitern oder die Benutzeroberfläche \(User Interface, UI\) von Outlook anpassen. Weitere Informationen zu VSTO\-Add\-Ins finden Sie unter [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Erstellen eines Outlook VSTO\-Add\-In\-Projekts  
 Erstellen Sie Outlook\-Projekte mithilfe der Projektvorlage **Outlook\-Add\-In** im Dialogfeld **Neues Projekt**. Diese Vorlage enthält die erforderlichen Assemblyverweise und Projektdateien.  
  
 Weitere Informationen zum Erstellen eines VSTO\-Add\-In\-Projekts finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).  
  
## VSTO\-Add\-In\-Programmiermodell von Outlook  
 Wenn Sie ein VSTO\-Add\-In\-Projekt für Outlook erstellen, generiert Visual Studio eine Klasse mit dem Namen `ThisAddIn`, die die Grundlage für die Projektmappe darstellt. Diese Klasse bietet einen Ausgangspunkt für das Schreiben des Codes, und sie macht auch das Outlook\-Objektmodell für das VSTO\-Add\-In verfügbar.  
  
 Weitere Informationen über die `ThisAddIn`\-Klasse und weitere Funktionen, die in einem VSTO\-Add\-In verwendet werden können, finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
## Automatisieren von Outlook mithilfe des Outlook\-Objektmodells  
 Das Outlook\-Objektmodell macht viele Typen verfügbar, die Sie zum Automatisieren von Outlook verwenden können. Diese Typen ermöglichen Ihnen das Schreiben von Code zum Ausführen häufiger Aufgaben:  
  
-   Programmgesteuertes Erstellen und Senden von E\-Mails  
  
-   Senden neuer Besprechungsanfragen  
  
-   Suchen nach Elementen in Outlook\-Ordnern  
  
 Weitere Informationen finden Sie unter [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md).  
  
## Anpassen der Benutzeroberfläche einer Outlook\-Anwendung  
  
|Aufgabe|Weitere Informationen|  
|-------------|---------------------------|  
|Fügen Sie dem Menüband eines Outlook\-Inspektors benutzerdefinierte Registerkarten hinzu.|[Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)|  
|Hinzufügen benutzerdefinierter Gruppen zu einer integrierten Registerkarte in einem Outlook\-Inspektor|[Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)|  
|Hinzufügen eines benutzerdefinierten Aufgabenbereichs, der in einem Outlook\-Inspektor angezeigt wird|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md).|  
|Hinzufügen eines Formularbereichs, der erweitert wird oder vorhandene Outlook\-Formulare ersetzt.|[Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)|  
  
 Weitere Informationen zum Anpassen der Benutzeroberfläche von Outlook und anderen Microsoft Office\-Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
## Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)|Bietet einen Überblick über die Objekte, die vom Outlook\-Objektmodell bereitgestellt werden.|  
|[Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)|Erläutert die von Visual Studio bereitgestellten Tools, die Ihnen das Entwerfen, Entwickeln und Debuggen von Formularbereichen erleichtern.|  
|[Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Erläutert das Erstellen eines VSTO\-Add\-Ins für Microsoft Office Outlook.|  
|[Outlook 2010 in der Office\-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199013)|Der Bereich der MSDN Library, in dem Sie Artikel und Referenzdokumentation zum Entwickeln von Outlook\-Projektmappen finden \(nicht spezifisch für die Office\-Entwicklung mit Visual Studio\).|  
  
  