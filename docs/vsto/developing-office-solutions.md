---
title: "Entwickeln von Office-Projektmappen"
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
  - "Office-Entwicklung in Visual Studio, Informationen zum Entwickeln von Projektmappen"
  - "Projektmappen [Office-Entwicklung in Visual Studio], Entwickeln"
  - "Office-Projektmappen [Office-Entwicklung in Visual Studio], Entwickeln"
ms.assetid: 7361cfe0-dee4-48d7-a066-232f87f093ca
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Entwickeln von Office-Projektmappen
  Nachdem Sie ein Projekt mit den Office Developer Tools in Visual Studio entworfen und die Projektdateien eingerichtet haben, können Sie damit beginnen, sich auf das Implementieren des Codes und der benutzerdefinierten Benutzeroberfläche \(UI\) zu konzentrieren.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Programmiermodell von Office\-Projektmappen  
 Über das Office\-Objektmodell werden viele verschiedene Objekte für die Programmierung verfügbar gemacht. Wenn Sie Office\-Projektmappen mit verwaltetem Code programmieren, schreiben Sie Code, bei dem Typen in den primären Interopassemblys von Office verwendet werden. In Projektmappen, die Sie mit Office\-Projektvorlagen in Visual Studio erstellen, können Sie Code auch direkt für generierte Klassen in Ihrem Projekt schreiben. Weitere Informationen finden Sie unter [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md).  
  
## Programmieren verschiedener Typen von Office\-Projektmappen  
 Der Typ der Projektmappe, den Sie erstellen, bestimmt, welche Funktionen Sie in Ihrem Projekt verwenden können. Beispielsweise können Sie Anpassungen auf Dokumentebene Windows Forms\-Steuerelemente und erweiterte Office\-Steuerelemente \(als *Hoststeuerelemente* bezeichnet\) hinzufügen, indem Sie die Elemente zur Entwurfszeit aus der **Werkzeugpalette** in Visual Studio ziehen. Wenn Sie aber ein VSTO\-Add\-In entwickeln, können Sie diese Arten von Steuerelementen Dokumenten zur Laufzeit nur hinzufügen, indem Sie Code schreiben.  
  
 Weitere Informationen zu Funktionen, die speziell für verschiedene Typen von Projektmappen gelten, finden Sie unter den folgenden Themen:  
  
-   [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md).  
  
-   [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
 Hintergrundinformationen zum Planen von Office\-Projektmappen und zu den Verfahren zum Erstellen von Projekten finden Sie unter [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md).  
  
## Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)|Hier werden verschiedene Aspekte des Schreibens von Code in Office\-Projektmappen beschrieben.|  
|[Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)|Enthält eine Übersicht über das Programmiermodell von VSTO\-Add\-Ins und die zugehörigen Programmieraufgaben.|  
|[Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)|Enthält eine Übersicht über das Programmiermodell von Anpassungen auf Dokumentebene und die zugehörigen Programmieraufgaben.|  
|[Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)|Hier werden die verschiedenen Wege beschrieben, wie Sie die Benutzeroberfläche von Office\-Anwendungen anpassen können, indem Sie VSTO\-Add\-Ins und Anpassungen auf Dokumentebene verwenden.|  
|[Daten in Office-Lösungen](../vsto/data-in-office-solutions.md)|Hier werden die unterschiedlichen Wege beschrieben, wie Sie in Office\-Projektmappen mit Daten arbeiten können, z. B. das Binden von Daten an Steuerelemente und das Zwischenspeichern von Daten in Anpassungen auf Dokumentebene.|  
|[Problembehandlung für Office-Lösungen](../vsto/troubleshooting-office-solutions.md)|Enthält Tipps zur Lösung von allgemeinen Problemen, die beim Erstellen von Office\-Projektmappen auftreten können.|  
|[Threading-Unterstützung in Office](../vsto/threading-support-in-office.md)|Hier erhalten Sie einen Überblick über die Arbeit mit mehreren Threads in Office\-Projektmappen.|  
|[Barrierefreiheit in Office-Projekten](../vsto/accessibility-in-office-projects.md)|Beschreibt die Barrierefreiheitsfunktionen, die in Office\-Projektmappen verfügbar sind.|  
  
## Siehe auch  
 [Gewusst wie: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Gewusst wie: Lesen von und Schreiben in Dokumenteigenschaften](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Gewusst wie: Anpassen an die mehrsprachige Benutzeroberfläche von Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Exemplarische Vorgehensweise: Erstellen eines ersten VSTO-Add-Ins für PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Exemplarische Vorgehensweise: Erstellen Ihres ersten VSTO-Add-Ins für Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  