---
title: Entwickeln von Office-Projektmappen | Microsoft Docs
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
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
ms.assetid: 7361cfe0-dee4-48d7-a066-232f87f093ca
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 478bd6d27d6e4ef0fe75891d95cdc4b3258a74e8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="developing-office-solutions"></a>Entwickeln von Office-Projektmappen
  Nachdem Sie ein Projekt mit den Office Developer Tools in Visual Studio entworfen und die Projektdateien eingerichtet haben, können Sie damit beginnen, sich auf das Implementieren des Codes und der benutzerdefinierten Benutzeroberfläche (UI) zu konzentrieren.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern "interested" [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins haben einen geringen Ressourcenbedarf im Vergleich zu VSTO-add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.  
  
## <a name="office-solutions-programming-model"></a>Programmiermodell von Office-Projektmappen  
 Über das Office-Objektmodell werden viele verschiedene Objekte für die Programmierung verfügbar gemacht. Wenn Sie Office-Projektmappen mit verwaltetem Code programmieren, schreiben Sie Code, bei dem Typen in den primären Interopassemblys von Office verwendet werden. In Projektmappen, die Sie mit Office-Projektvorlagen in Visual Studio erstellen, können Sie Code auch direkt für generierte Klassen in Ihrem Projekt schreiben. Weitere Informationen finden Sie unter [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="programming-different-types-of-office-solutions"></a>Programmieren verschiedener Typen von Office-Projektmappen  
 Der Typ der Projektmappe, den Sie erstellen, bestimmt, welche Funktionen Sie in Ihrem Projekt verwenden können. Beispielsweise können Sie Anpassungen auf Dokumentebene Windows Forms-Steuerelemente und erweiterte Office-Steuerelemente (als *Hoststeuerelemente*bezeichnet) hinzufügen, indem Sie die Elemente zur Entwurfszeit aus der **Werkzeugpalette** in Visual Studio ziehen. Wenn Sie aber ein VSTO-Add-In entwickeln, können Sie diese Arten von Steuerelementen Dokumenten zur Laufzeit nur hinzufügen, indem Sie Code schreiben.  
  
 Weitere Informationen zu Funktionen, die speziell für verschiedene Typen von Projektmappen gelten, finden Sie unter den folgenden Themen:  
  
-   [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
-   [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
 Hintergrundinformationen zum Planen von Office-Projektmappen und zu den Verfahren zum Erstellen von Projekten finden Sie unter [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)|Hier werden verschiedene Aspekte des Schreibens von Code in Office-Projektmappen beschrieben.|  
|[Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)|Enthält eine Übersicht über das Programmiermodell von VSTO-Add-Ins und die zugehörigen Programmieraufgaben.|  
|[Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)|Enthält eine Übersicht über das Programmiermodell von Anpassungen auf Dokumentebene und die zugehörigen Programmieraufgaben.|  
|[Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)|Hier werden die verschiedenen Wege beschrieben, wie Sie die Benutzeroberfläche von Office-Anwendungen anpassen können, indem Sie VSTO-Add-Ins und Anpassungen auf Dokumentebene verwenden.|  
|[Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)|Hier werden die unterschiedlichen Wege beschrieben, wie Sie in Office-Projektmappen mit Daten arbeiten können, z. B. das Binden von Daten an Steuerelemente und das Zwischenspeichern von Daten in Anpassungen auf Dokumentebene.|  
|[Wie wirkt sich auf AutoSpeichern Office-Projektmappen](./how-autosave-impacts-office-solutions.md)|Beschreibt die Korrekturen, die Sie möglicherweise für Office-Projektmappen zu stellen, wenn AutoSpeichern aktiviert ist.|
|[Problembehandlung für Office-Projektmappen](../vsto/troubleshooting-office-solutions.md)|Enthält Tipps zur Lösung von allgemeinen Problemen, die beim Erstellen von Office-Projektmappen auftreten können.|  
|[Threading-Unterstützung in Office](../vsto/threading-support-in-office.md)|Hier erhalten Sie einen Überblick über die Arbeit mit mehreren Threads in Office-Projektmappen.|  
|[Barrierefreiheit in Office-Projekten](../vsto/accessibility-in-office-projects.md)|Beschreibt die Barrierefreiheitsfunktionen, die in Office-Projektmappen verfügbar sind.|  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Vorgehensweise: Lesen und Schreiben in Dokumenteigenschaften](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Vorgehensweise: Anpassen der mehrsprachige Benutzeroberfläche von Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Exemplarische Vorgehensweise: Erstellen Ihrer ersten VSTO-Add-Ins für PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Exemplarische Vorgehensweise: Erstellen Ihrer ersten VSTO-Add-Ins für Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  