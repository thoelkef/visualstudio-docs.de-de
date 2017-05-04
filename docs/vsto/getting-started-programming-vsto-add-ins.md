---
title: "Erste Schritte beim Programmieren von VSTO-Add-Ins | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.Outlook"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Add-Ins [Office-Entwicklung in Visual Studio], Erste Schritte"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Erste Schritte"
ms.assetid: 9ac1e6ea-9511-4633-80f9-dc7641f22b63
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Erste Schritte beim Programmieren von VSTO-Add-Ins
  Sie können mit VSTO\-Add\-Ins Microsoft Office\-Anwendungen automatisieren, Funktionen der Anwendung erweitern und die Benutzeroberfläche der Anwendung anpassen.  Informationen zu VSTO\-Add\-Ins im Vergleich mit anderen Typen von Office\-Projektmappen, die Sie mit Visual Studio erstellen können, finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## Erstellen von VSTO\-Add\-In\-Projekten  
 Erstellen Sie VSTO\-Add\-In\-Projekte mit einer der VSTO\-Add\-In\-Projektvorlagen im Dialogfeld **Neues Projekt**.  Diese Vorlagen enthalten erforderliche Assemblyverweise und Projektdateien.  Visual Studio stellt VSTO\-Add\-In\-Projektvorlagen für die meisten Anwendungen in Office zur Verfügung.  
  
 Weitere Informationen zur Erstellung eines VSTO\-Add\-In\-Projekts finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).  
  
## Entwickeln von VSTO\-Add\-In\-Projekten  
 Wenn Sie ein VSTO\-Add\-In\-Projekt erstellen, erstellt Visual Studio automatisch eine ThisAddIn.vb\-Codedatei \(in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) bzw. eine ThisAddIn.cs\-Codedatei \(in C\#\).  Diese Datei enthält die `ThisAddIn`\-Klasse, die die Grundlage für das VSTO\-Add\-In bildet.  Sie können Member dieser Klasse verwenden, um Code auszuführen, wenn das VSTO\-Add\-In geladen oder entladen wird, um auf das Objektmodell der Hostanwendung zuzugreifen und um Features der Anwendung zu erweitern.  Weitere Informationen finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
## Automatisieren von Anwendungen mithilfe der Objektmodelle  
 Die Objektmodelle von Microsoft Office\-Anwendungen machen zahlreiche Typen verfügbar, mit denen Sie in einem VSTO\-Add\-In programmieren können.  Sie können diese Typen verwenden, um die Anwendung zu automatisieren.  So haben Sie die Möglichkeit, in Outlook programmgesteuert eine E\-Mail zu erstellen und zu senden oder in Word ein Dokument zu öffnen und Inhalt hinzuzufügen.  Weitere Informationen zum Zugreifen auf das Objektmodell der Hostanwendung im Code finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Weitere Informationen zu den Objektmodellen von bestimmten Microsoft Office\-Anwendungen finden Sie unter den folgenden Themen:  
  
-   [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)  
  
-   [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)  
  
-   [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath-Projektmappen](../vsto/infopath-solutions.md)  
  
-   [PowerPoint-Projektmappen](../vsto/powerpoint-solutions.md)  
  
-   [Projektmappen](../vsto/project-solutions.md)  
  
-   [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)  
  
## Anpassen der Benutzeroberfläche von Anwendungen  
 Es gibt verschiedene Möglichkeiten, die Benutzeroberfläche der Hostanwendung mit einem VSTO\-Add\-In anzupassen:  
  
-   Für Excel und Word können Sie Dokumenten verwaltete Steuerelemente hinzufügen.  Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
-   Sie können das Menüband anpassen, wenn die Anwendung dies unterstützt.  Weitere Informationen finden Sie unter [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md).  
  
-   Sie können einen benutzerdefinierten Aufgabenbereich erstellen, wenn die Anwendung dies unterstützt.  Weitere Informationen finden Sie unter [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md).  
  
-   Für Outlook können Sie einen benutzerdefinierten Formularbereich erstellen.  Weitere Informationen finden Sie unter [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).  
  
-   Für alle Microsoft Office\-Anwendungen können Sie Windows Forms im VSTO\-Add\-In anzeigen.  
  
 Weitere Informationen zum Anpassen der Benutzeroberfläche von Microsoft Office\-Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
## Nächste Schritte  
 Wie Sie VSTO\-Add\-Ins erstellen können, wird in den folgenden exemplarischen Vorgehensweisen näher beschrieben:  
  
-   [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Exemplarische Vorgehensweise: Erstellen eines ersten VSTO-Add-Ins für PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Exemplarische Vorgehensweise: Erstellen Ihres ersten VSTO-Add-Ins für Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 In diesen exemplarischen Vorgehensweisen machen Sie sich mit den Office\-Entwicklungstools in Visual Studio und dem Programmiermodell für VSTO\-Add\-Ins vertraut.  
  
 Eine Liste der Themen mit exemplarischen Vorgehensweisen für gängige Aufgaben in Office\-Projekten finden Sie unter [Häufige Aufgaben bei der Programmierung mit Office](../vsto/common-tasks-in-office-programming.md).  
  
## Siehe auch  
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  