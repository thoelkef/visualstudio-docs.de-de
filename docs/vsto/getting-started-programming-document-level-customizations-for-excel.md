---
title: "Programmieren von Anpassungen auf Dokumentebene für Excel erste Schritte | Microsoft Docs"
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
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
ms.assetid: 8b73cf08-a173-4b49-b20f-2d2456dbe925
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0c2f8d0a8360153b81d54b5d1867af452e6aaf9d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-programming-document-level-customizations-for-excel"></a>Erste Schritte beim Programmieren von Anpassungen auf Dokumentebene für Excel
  Wenn Sie nur die ersten Schritte Erstellen von Anpassungen auf Dokumentebene für Microsoft Office Excel mithilfe von Visual Studio machen, ist hier was Sie wissen müssen.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understanding-how-document-level-customizations-for-excel-work"></a>Grundlegendes zu wie Anpassungen auf Dokumentebene für Excel arbeiten  
 Eine Anpassung auf Dokumentebene für Excel basiert auf einer einzelnen Arbeitsmappe. Um mit der Anpassung zu starten, der Endbenutzer öffnet die Arbeitsmappe oder die Arbeitsmappe aus einer Excel-Vorlage erstellt. Ereignisse in der Arbeitsmappe, z. B. in Zellen eingeben, oder klicken auf Schaltflächen und Menüelementen können Ereignisbehandlungsmethoden in der Assembly aufrufen. Wenn die Arbeitsmappe geschlossen wird, sind die von der Anpassung bereitgestellten Funktionen nicht mehr verfügbar in Excel können nur in das Dokument, das sie enthalten.  
  
 Weitere Informationen finden Sie unter [Architektur Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="creating-document-level-projects-for-excel"></a>Erstellen von Projekten auf Dokumentebene für Excel  
 Um eine Anpassung auf Dokumentebene für Excel zu erstellen, verwenden Sie die Excel-Arbeitsmappen oder Excel-Vorlagen-Projektvorlage in die **neues Projekt** (Dialogfeld). Diese Vorlagen enthalten erforderliche Assemblyverweise und Projektdateien.  
  
 Weitere Informationen zum Erstellen von einem Projekt auf Dokumentebene für Excel finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).  
  
## <a name="programming-excel-workbooks-by-using-host-items-and-host-controls"></a>Programmieren von Excel-Arbeitsmappen mithilfe von Hostelementen und Hoststeuerelementen  
 *Hostelemente* und *Hoststeuerelemente* sind Klassen, die für Anpassungen auf Dokumentebene, die mithilfe von Visual Studio erstellt das Programmiermodell bereitstellen.  
  
 Hostelemente stellen einen Einstiegspunkt für Ihren Code bereit, und sie können auch dienen als Container für Hoststeuerelemente und Windows Forms-Steuerelemente. In Projekten auf Dokumentebene für Excel werden diese Hostelemente dargestellt, durch die `ThisWorkbook`, `Sheet1`, `Sheet2`, und `Sheet3` Klassen.  
  
 Hoststeuerelemente basieren auf systemeigenen Excel-Objekte, z. B. List-Objekte und Bereiche. Hoststeuerelemente stellen ähnliche Funktionen wie die systemeigenen Excel-Objekte, jedoch auch über neue Ereignisse, die Designer-Unterstützung und Datenbindungsfunktion. Sie sind als erstklassige Objekte in Ihrem Projektcode und in IntelliSense zu auf bestimmte Objekte direkt im Code zu verweisen, ohne Excel-Objektmodell zu navigieren.  
  
 Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  
-   [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customizing-the-user-interface-of-excel"></a>Anpassen der Excel-Benutzeroberfläche  
 Die meisten Microsoft Office-Projektmappen Anpassen der Benutzeroberfläche (UI) der Office-Anwendung für Benutzer für die Interaktion mit der Lösung einige Möglichkeit bereitstellen. Es gibt viele Möglichkeiten, die in denen Sie die UI von Excel mit einer Anpassung auf Dokumentebene ändern. Z. B. Hinzufügen von Steuerelementen auf dem Menüband, oder Sie können einen Aktionsbereich anzeigen. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
 Sie können auch die Arbeitsmappe öffnen, die das Projekt in Visual Studio direkt zugeordnet ist. Wenn die Arbeitsmappe in Visual Studio geöffnet ist, können Sie die Arbeitsmappe mit der Excel-Benutzeroberfläche ändern. Sie können auch die Arbeitsmappe als Entwurfsoberfläche, die Sie Steuerelemente auf Arbeitsblätter ziehen können. Weitere Informationen finden Sie unter [Office-Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="using-data-binding"></a>Verwenden der Datenbindung  
 Die Hoststeuerelemente sind auch in der Liste der Steuerelemente, die Sie ziehen können, aus der **Datenquellen** Fenster. Hinzufügen von Hoststeuerelementen in dieser Weise automatisch bindet diese an die Datenquelle, die Sie im Fenster "" eingerichtet. Ohne Code schreiben zu müssen, können Sie Daten aus Datenbanken, Webdienste und Geschäftsobjekten anzeigen. Weitere Informationen finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Nächste Schritte  
 Gewusst wie: erstellen eine Anpassung auf Dokumentebene für Excel finden Sie unter [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). In dieser exemplarischen Vorgehensweise werden die Office-Entwicklungstools in Visual Studio und dem Programmiermodell für Anpassungen auf Anwendungsebene Excel vorgestellt.  
  
 Eine Liste der Themen, in denen Sie einige der allgemeinen Aufgaben in Excel-Projekten durchlaufen, finden Sie unter [häufige Aufgaben bei der Programmierung mit Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)   
 [Excel-Projektmappen](../vsto/excel-solutions.md)   
 [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)   
 [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  