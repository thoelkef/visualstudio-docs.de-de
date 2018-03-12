---
title: Erste Schritte Programmieren von VSTO-Add-ins | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: f395ce7fb85d71ed6e8c3f7dfb10726907832873
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="getting-started-programming-vsto-add-ins"></a>Getting Started Programming VSTO Add-ins
  Sie können mit VSTO-Add-Ins Microsoft Office-Anwendungen automatisieren, Funktionen der Anwendung erweitern und die Benutzeroberfläche der Anwendung anpassen. Informationen zu VSTO-Add-ins im Vergleich mit anderen Arten von Office-Projektmappen können Sie mithilfe von Visual Studio erstellen, finden Sie unter [Übersicht über die Entwicklung von Office-Lösungen &#40; VSTO- &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="creating-vsto-add-in-projects"></a>Erstellen von VSTO-Add-In-Projekten  
 Erstellen von VSTO-Add-in-Projekte mit einer der VSTO-Add-in-Projektvorlagen in den **neues Projekt** (Dialogfeld). Diese Vorlagen enthalten erforderliche Assemblyverweise und Projektdateien. Visual Studio stellt VSTO-Add-In-Projektvorlagen für die meisten Anwendungen in Office zur Verfügung.  
  
 Weitere Informationen zum Erstellen eines VSTO-Add-in-Projekts finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).  
  
## <a name="developing-vsto-add-in-projects"></a>Entwickeln von VSTO-Add-In-Projekten  
 Wenn Sie ein VSTO-Add-in-Projekt erstellen, erstellt Visual Studio automatisch eine ThisAddIn.vb-Codedatei (in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) oder "ThisAddIn.cs" (in c#)-Codedatei. Diese Datei enthält die `ThisAddIn` -Klasse, die die Grundlage für das VSTO-Add-in bildet. Sie können Member dieser Klasse verwenden, um Code auszuführen, wenn das VSTO-Add-In geladen oder entladen wird, um auf das Objektmodell der Hostanwendung zuzugreifen und um Funktionen der Anwendung zu erweitern. Weitere Informationen finden Sie unter [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automating-applications-by-using-the-object-models"></a>Automatisieren von Anwendungen mithilfe der Objektmodelle  
 Die Objektmodelle von Microsoft Office-Anwendungen machen zahlreiche Typen verfügbar, mit denen Sie in einem VSTO-Add-In programmieren können. Sie können diese Typen verwenden, um die Anwendung zu automatisieren. So haben Sie die Möglichkeit, in Outlook programmgesteuert eine E-Mail zu erstellen und zu senden oder in Word ein Dokument zu öffnen und Inhalt hinzuzufügen. Weitere Informationen über das Zugreifen auf das Objektmodell der hostanwendung im Code finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Weitere Informationen zu den Objektmodellen von bestimmten Microsoft Office-Anwendungen finden Sie unter den folgenden Themen:  
  
-   [Excel Object Model Overview](../vsto/excel-object-model-overview.md)  
  
-   [Word Object Model Overview](../vsto/word-object-model-overview.md)  
  
-   [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)  
  
-   [InfoPath-Projektmappen](../vsto/infopath-solutions.md)  
  
-   [PowerPoint-Projektmappen](../vsto/powerpoint-solutions.md)  
  
-   [Project-Projektmappen](../vsto/project-solutions.md)  
  
-   [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)  
  
## <a name="customizing-the-user-interface-of-applications"></a>Anpassen der Benutzeroberfläche von Anwendungen  
 Es gibt verschiedene Möglichkeiten, die Benutzeroberfläche der Hostanwendung mit einem VSTO-Add-In anzupassen:  
  
-   Für Excel und Word können Sie Dokumenten verwaltete Steuerelemente hinzufügen. Weitere Informationen finden Sie unter [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
-   Sie können das Menüband anpassen, wenn die Anwendung dies unterstützt. Weitere Informationen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).  
  
-   Sie können einen benutzerdefinierten Aufgabenbereich erstellen, wenn die Anwendung dies unterstützt. Weitere Informationen finden Sie unter [von benutzerdefinierten Aufgabenbereichen](../vsto/custom-task-panes.md).  
  
-   Für Outlook können Sie einen benutzerdefinierten Formularbereich erstellen. Weitere Informationen finden Sie unter [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
-   Für alle Microsoft Office-Anwendungen können Sie Windows Forms im VSTO-Add-In anzeigen.  
  
 Weitere Informationen zum Anpassen der Benutzeroberfläche von Microsoft Office-Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wie Sie VSTO-Add-Ins erstellen können, wird in den folgenden exemplarischen Vorgehensweisen näher beschrieben:  
  
-   [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 In diesen exemplarischen Vorgehensweisen machen Sie sich mit den Office-Entwicklungstools in Visual Studio und dem Programmiermodell für VSTO-Add-Ins vertraut.  
  
 Eine Liste der Themen, in denen Sie einige der allgemeinen Aufgaben in Office-Projekten durchlaufen, finden Sie unter [häufige Aufgaben bei der Programmierung mit Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Erste Schritte &#40; Office-Entwicklung in Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Architektur von VSTO-Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  