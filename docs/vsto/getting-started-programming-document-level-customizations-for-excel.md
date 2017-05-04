---
title: "Erste Schritte beim Programmieren von Anpassungen auf Dokumentebene f&#252;r Excel | Microsoft Docs"
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
  - "Excel-Projekte [Office-Entwicklung in Visual Studio], Erste Schritte"
  - "Excel-Projektmappen in Visual Studio"
ms.assetid: 8b73cf08-a173-4b49-b20f-2d2456dbe925
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Erste Schritte beim Programmieren von Anpassungen auf Dokumentebene f&#252;r Excel
  Wenn Sie gerade unternehmen, auf Dokumentebene für Microsoft Office Excel erstellen Anpassungen, indem Sie Visual Studio verwenden, ist hier, was Sie kennen müssen.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## Grundlegendes zur Funktionsweise von Anpassungen auf Dokumentebene für Excel  
 Eine Anpassung auf Dokumentebene für Excel basiert auf einer einzelnen Arbeitsmappe.  Um die Anpassung zu verwenden, öffnet der Endbenutzer die Arbeitsmappe oder erstellt sie anhand einer Excel\-Vorlage.  Ereignisse in der Arbeitsmappe, zum Beispiel Eingaben in Zellen oder das Klicken auf Schaltflächen und Menüpunkte, können zum Aufruf von Ereignisbehandlungsmethoden in der Assembly führen.  Wenn die Arbeitsmappe geschlossen wird, sind die Funktionen, die von der Anpassung bereitgestellten werden, nicht mehr in Excel, nur im Dokument verfügbar, das sie enthält.  
  
 Weitere Informationen finden Sie unter [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).  
  
## Erstellen von Projekten auf Dokumentebene für Excel  
 Verwenden Sie zum Erstellen einer Anpassung auf Dokumentebene für Excel die Projektvorlage für Excel\-Arbeitsmappen oder Excel\-Vorlagen im Dialogfeld **Neues Projekt**.  Diese Vorlagen enthalten erforderliche Assemblyverweise und Projektdateien.  
  
 Weitere Informationen zum Erstellen eines Projekts auf Dokumentebene für Excel finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).  
  
## Programmieren von Excel\-Arbeitsmappen mithilfe von Hostelementen und Hoststeuerelementen  
 *Hostelemente* und *Hoststeuerelemente* sind Klassen, die das Programmiermodell für Anpassungen auf Dokumentebene bereitstellen, die mithilfe von Visual Studio erstellt wurden, verwenden.  
  
 Hostelemente stellen einen Einstiegspunkt für den Code bereit, und sie können als Container für Hoststeuerelemente und Windows Forms\-Steuerelemente dienen.  In Projekten auf Dokumentebene für Excel werden diese Hostelemente durch die Klassen `ThisWorkbook`, `Sheet1`, `Sheet2` und `Sheet3` dargestellt.  
  
 Hoststeuerelemente basieren auf systemeigenen Excel\-Objekten, z. B. Listenobjekten und Bereichen.  Hoststeuerelemente stellen für die systemeigenen Excel\-Objekte ähnliche Funktionen bereit, verfügen aber auch über neue Ereignisse und Designerunterstützung und Datenbindungsfähigkeiten.  Sie sind als Erstklassenobjekte im Projektcode und in IntelliSense zu finden. Dadurch wird es leichter, direkt im Code auf bestimmte Objekte zu verweisen, da Sie das Excel\-Objektmodell nicht durchlaufen müssen.  
  
 Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)  
  
-   [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
## Anpassen der Excel\-Benutzeroberfläche  
 Die meisten Microsoft Office\-Projektmappen ändern die Benutzeroberfläche der Office\-Anwendung, damit Benutzer mit der Projektmappe interagieren können.  Es gibt eine Reihe von Möglichkeiten, die Excel\-Benutzeroberfläche mithilfe einer Anpassung auf Dokumentebene zu ändern.  Beispielsweise können Sie dem Menüband Steuerelemente hinzufügen, oder Sie können einen Aktionsbereich anzeigen.  Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
 Sie können auch die Arbeitsmappe öffnen, die dem Projekt direkt in Visual Studio zugeordnet ist.  Wenn die Arbeitsmappe in Visual Studio geöffnet ist, können Sie diese mithilfe der Excel\-Benutzeroberfläche ändern.  Sie können auch die Arbeitsmappe als Entwurfsoberfläche verwenden, sodass Sie Steuerelemente auf Arbeitsblätter ziehen können.  Weitere Informationen finden Sie unter [Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Verwenden der Datenbindung  
 Die Hoststeuerelemente befinden sich auch in der Liste der Steuerelemente, die Sie aus dem **Datenquellenfenster** ziehen können.  Wenn Sie Hoststeuerelemente auf diese Art hinzufügen, werden sie automatisch an die Datenquellen gebunden, die Sie in dem Fenster einrichten.  Ohne Code zu schreiben, können Sie Daten aus Datenbanken, Webdiensten und Geschäftsobjekten anzeigen.  Weitere Informationen finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## Nächste Schritte  
 Weitere Informationen zum Erstellen einer Anpassung auf Dokumentebene für Excel finden Sie unter [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md).  In dieser exemplarischen Vorgehensweise machen Sie sich mit den Office\-Entwicklungstools in Visual Studio und dem Programmiermodell für Excel\-Anpassungen auf Dokumentebene vertraut.  
  
 Eine Liste der Themen mit exemplarischen Vorgehensweisen für gängige Aufgaben in Excel\-Projekten finden Sie unter [Häufige Aufgaben bei der Programmierung mit Office](../vsto/common-tasks-in-office-programming.md).  
  
## Siehe auch  
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)   
 [Excel-Projektmappen](../vsto/excel-solutions.md)   
 [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)   
 [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)  
  
  