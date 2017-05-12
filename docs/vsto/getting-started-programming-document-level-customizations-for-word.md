---
title: "Erste Schritte: Programmieren von Anpassungen auf Dokumentebene f&#252;r Word"
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
  - "Word-Projekte [Office-Entwicklung in Visual Studio], Erste Schritte"
  - "Word-Projektmappen in Visual Studio"
ms.assetid: 30593c47-1658-4fca-b9a9-36fbdf73c901
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Erste Schritte: Programmieren von Anpassungen auf Dokumentebene f&#252;r Word
  Wenn Sie gerade unternehmen, auf Dokumentebene für Microsoft Office Word Anpassungen erstellen, indem Sie Visual Studio verwenden, ist hier, was Sie kennen müssen.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## Grundlegendes zur Funktionsweise von Anpassungen auf Dokumentebene für Word  
 Jede Word\-Anpassung, die Sie erstellen, basiert auf einem einzelnen Dokument.  Um die Anpassung zu verwenden, öffnet der Endbenutzer das Dokument oder erstellt es anhand einer Word\-Vorlage.  Ereignisse im Dokument, z. B. das Bewegen des Cursors in bestimmte Bereiche oder das Klicken auf Schaltflächen und Menüpunkte, können zum Aufruf von Ereignisbehandlungsmethoden in der Assembly führen.  Wenn das Dokument geschlossen wird, sind die von der Anpassung bereitgestellten Funktionen nicht mehr in Word verfügbar.  
  
 Weitere Informationen finden Sie unter [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).  
  
## Erstellen von Projekten auf Dokumentebene für Word  
 Um eine Anpassung auf Dokumentebene für Word zu erstellen, verwenden Sie die Word\-Dokument\- oder Word\-Vorlagenprojektvorlagen im Dialogfeld **Neues Projekt**.  Diese Vorlagen enthalten erforderliche Assemblyverweise und Projektdateien.  
  
 Weitere Informationen zum Erstellen eines Projekts auf Dokumentebene für Word finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).  
  
## Programmieren von Word\-Dokumenten mithilfe von Hostelementen und Hoststeuerelementen  
 *Hostelemente* und *Hoststeuerelemente* sind Klassen, die das Programmiermodell für Anpassungen auf Dokumentebene bereitstellen.  
  
 Hostelemente stellen einen Einstiegspunkt für den Code bereit, und sie können als Container für Hoststeuerelemente und Windows Forms\-Steuerelemente dienen.  In Projekten auf Dokumentebene für Word wird das Hostelement durch die `ThisDocument`\-Klasse dargestellt.  
  
 Hoststeuerelemente basieren auf systemeigenen Word\-Objekten, z. B. Inhaltssteuerelementen, Lesezeichen und XML\-Knoten.  Hoststeuerelemente stellen für die systemeigenen Word\-Objekte ähnliche Funktionen bereit, verfügen aber auch über neue Ereignisse und Designerunterstützung und Datenbindungsfähigkeiten.  Sie sind als Erstklassenobjekte im Projektcode und in IntelliSense zu finden. Dadurch wird es leichter, direkt im Code auf bestimmte Objekte zu verweisen, da Sie das Word\-Objektmodell nicht durchlaufen müssen.  
  
 Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)  
  
-   [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
## Anpassen der Word\-Benutzeroberfläche  
 Die meisten Microsoft Office\-Projektmappen ändern die Benutzeroberfläche der Office\-Anwendung, damit Benutzer mit der Projektmappe interagieren können.  Es gibt eine Reihe von Möglichkeiten, die Word\-Benutzeroberfläche mithilfe einer Anpassung auf Dokumentebene zu ändern.  Beispielsweise können Sie dem Menüband Steuerelemente hinzufügen, und Sie können einen Aktionsbereich anzeigen.  Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
 Sie können auch das Dokument öffnen, das dem Projekt direkt in Visual Studio zugeordnet ist.  Wenn das Dokument in Visual Studio geöffnet ist, können Sie dieses mithilfe der Word\-Benutzeroberfläche ändern.  Sie können auch das Dokument als Entwurfsoberfläche verwenden, sodass Sie Steuerelemente darauf ziehen können.  Weitere Informationen finden Sie unter [Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Binden von Steuerelementen an Daten  
 Die Inhaltssteuerelemente und das <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelement befinden sich in der Liste von Steuerelementen, die Sie aus dem Fenster **Datenquellen** ziehen können.  Wenn Sie Inhaltssteuerelemente und Lesezeichen auf diese Art hinzufügen, werden diese automatisch an die Datenquelle gebunden, die Sie in dem Fenster einrichten.  Ohne Code zu schreiben, können Sie Daten aus Datenbanken, Diensten und Geschäftsobjekten anzeigen.  Weitere Informationen finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## Nächste Schritte  
 Weitere Informationen zum Erstellen einer Anpassung auf Dokumentebene für Word finden Sie unter [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md).  In dieser exemplarischen Vorgehensweise machen Sie sich mit den Office\-Entwicklungstools in Visual Studio und dem Programmiermodell für Word\-Anpassungen auf Dokumentebene vertraut.  
  
 Eine Liste der Themen mit exemplarischen Vorgehensweisen für gängige Aufgaben in Word\-Projekten finden Sie unter [Häufige Aufgaben bei der Programmierung mit Office](../vsto/common-tasks-in-office-programming.md).  
  
## Siehe auch  
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)   
 [Word-Projektmappen](../vsto/word-solutions.md)   
 [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Exemplarische Vorgehensweisen in Word](../vsto/walkthroughs-using-word.md)   
 [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)  
  
  