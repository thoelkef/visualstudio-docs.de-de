---
title: Outlook-Projektmappen | Microsoft Docs
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
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
ms.assetid: 2ae3cd9c-bf31-4efa-8b18-b6b1c34a8d93
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e0784662a1c48602dd8f93f5ae97c0a69192c3a5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="outlook-solutions"></a>Outlook-Projektmappen
  Visual Studio stellt Projektvorlagen bereit, die Sie zum Erstellen von VSTO-Add-Ins für Microsoft Office Outlook verwenden können. Mit VSTO-Add-Ins können Sie Outlook automatisieren, Outlook-Features erweitern oder die Benutzeroberfläche (User Interface, UI) von Outlook anpassen. Weitere Informationen zu VSTO-Add-Ins finden Sie unter [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern "interested" [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins haben einen geringen Ressourcenbedarf im Vergleich zu VSTO-add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.  
  
## <a name="creating-an-outlook-vsto-add-in-project"></a>Erstellen eines Outlook VSTO-Add-In-Projekts  
 Erstellen Sie Outlook-Projekte mithilfe der Projektvorlage **Outlook-Add-In** im Dialogfeld **Neues Projekt** . Diese Vorlage enthält die erforderlichen Assemblyverweise und Projektdateien.  
  
 Weitere Informationen zum Erstellen eines VSTO-Add-in-Projekts finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).  
  
## <a name="outlook-vsto-add-in-programming-model"></a>VSTO-Add-In-Programmiermodell von Outlook  
 Wenn Sie ein VSTO-Add-In-Projekt für Outlook erstellen, generiert Visual Studio eine Klasse mit dem Namen `ThisAddIn`, die die Grundlage für die Projektmappe darstellt. Diese Klasse bietet einen Ausgangspunkt für das Schreiben des Codes, und sie macht auch das Outlook-Objektmodell für das VSTO-Add-In verfügbar.  
  
 Weitere Informationen zu den `ThisAddIn` Klassen- und andere Funktionen Sie in einem VSTO-Add-in können finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automating-outlook-by-using-the-outlook-object-model"></a>Automatisieren von Outlook mithilfe des Outlook-Objektmodells  
 Das Outlook-Objektmodell macht viele Typen verfügbar, die Sie zum Automatisieren von Outlook verwenden können. Diese Typen ermöglichen Ihnen das Schreiben von Code zum Ausführen häufiger Aufgaben:  
  
-   Programmgesteuertes Erstellen und Senden von E-Mails  
  
-   Senden neuer Besprechungsanfragen  
  
-   Suchen nach Elementen in Outlook-Ordnern  
  
 Weitere Informationen finden Sie unter [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md).  
  
## <a name="customizing-the-user-interface-of-an-outlook-application"></a>Anpassen der Benutzeroberfläche einer Outlook-Anwendung  
  
|Aufgabe|Weitere Informationen|  
|----------|--------------------------|  
|Fügen Sie dem Menüband eines Outlook-Inspektors benutzerdefinierte Registerkarten hinzu.|[Übersicht über das Menüband](../vsto/ribbon-overview.md)|  
|Hinzufügen benutzerdefinierter Gruppen zu einer integrierten Registerkarte in einem Outlook-Inspektor|[Vorgehensweise: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)|  
|Hinzufügen eines benutzerdefinierten Aufgabenbereichs, der in einem Outlook-Inspektor angezeigt wird|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md).|  
|Hinzufügen eines Formularbereichs, der erweitert wird oder vorhandene Outlook-Formulare ersetzt.|[Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)|  
  
 Weitere Informationen zum Anpassen der Benutzeroberfläche von Outlook und anderen Microsoft Office-Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)|Bietet einen Überblick über die Objekte, die vom Outlook-Objektmodell bereitgestellt werden.|  
|[Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)|Erläutert die von Visual Studio bereitgestellten Tools, die Ihnen das Entwerfen, Entwickeln und Debuggen von Formularbereichen erleichtern.|  
|[Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Erläutert das Erstellen eines VSTO-Add-Ins für Microsoft Office Outlook.|  
|[Outlook 2010 in der Office-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199013)|Der Bereich der MSDN Library, in dem Sie Artikel und Referenzdokumentation zum Entwickeln von Outlook-Projektmappen finden (nicht spezifisch für die Office-Entwicklung mit Visual Studio).|  
  
  