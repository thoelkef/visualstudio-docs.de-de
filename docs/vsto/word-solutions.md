---
title: Word-Lösungen | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 44cd5633d7cc03fb78c6508c24a117a0500fa142
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="word-solutions"></a>Word-Projektmappen
  Visual Studio stellt Projektvorlagen bereit, die Sie verwenden können, um Anpassungen auf Dokumentebene und VSTO-Add-Ins für Microsoft Office Word zu erstellen. Mit diesen Projektmappen können Sie Word automatisieren, Word-Features erweitern und die Word-Benutzeroberfläche anpassen. Weitere Informationen zu den Unterschieden zwischen Anpassungen auf Dokumentebene und VSTO-Add-ins finden Sie unter [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
> [!NOTE]  
>  Bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern "interested" [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins haben einen geringen Ressourcenbedarf im Vergleich zu VSTO-add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.  
  
 Dieses Thema enthält folgende Informationen:  
  
-   [Automatisieren von Word](#automating).  
  
-   [Entwickeln von Anpassungen auf Dokumentebene für Word](#doclevel).  
  
-   [Entwickeln von VSTO-Add-Ins für Word](#applevel).  
  
-   [Anpassen der Word-Benutzeroberfläche](#UI).  
  
##  <a name="automating"></a> Automatisieren von Word  
 Das Word-Objektmodell macht viele Typen verfügbar, die Sie zum Automatisieren von Word verwenden können. Sie können beispielsweise Tabellen programmgesteuert erstellen, Dokumente formatieren und den Text in Bereichen und Absätzen festlegen. Weitere Informationen finden Sie unter [Word Object Model Overview](../vsto/word-object-model-overview.md).  
  
 Wenn Sie Word-Projektmappen in Visual Studio entwickeln, können Sie auch *Hostelemente* und *Hoststeuerelemente* in den Projektmappen verwenden. Dabei handelt es sich um Objekte, die bestimmte häufig verwendete Objekte im Word-Objektmodell erweitern, z. B. das <xref:Microsoft.Office.Interop.Word.Document> -Objekt und das <xref:Microsoft.Office.Interop.Word.ContentControl> -Objekt. Die erweiterten Objekte verhalten sich wie die Word-Objekte, auf denen sie basieren, fügen den Objekten jedoch zusätzliche Ereignis- und Datenbindungsfunktionen hinzu. Weitere Informationen finden Sie unter [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Developing Document-Level Customizations for Word  
 Eine Anpassung auf Dokumentebene für Microsoft Office Word besteht aus einer Assembly, die einem spezifischen Dokument zugeordnet ist. Die Assembly erweitert das Dokument normalerweise durch das Anpassen der UI und das Automatisieren von Word. Im Gegensatz zu einem VSTO-Add-In, das Word direkt zugeordnet ist, sind Funktionen, die in einer Anpassung implementiert werden, nur dann verfügbar, wenn das zugehörige Dokument in Word geöffnet ist.  
  
 Um ein Anpassungsprojekt auf Dokumentebene für Word zu erstellen, verwenden Sie die Word-Dokument- oder Word-Vorlagenprojektvorlagen im Dialogfeld **Neues Projekt** von Visual Studio. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Weitere Informationen zur Funktionsweise von Anpassungen auf Dokumentebene finden Sie unter [Architecture of Document-Level Customizations](../vsto/architecture-of-document-level-customizations.md).  
  
### <a name="word-customization-programming-model"></a>Programmiermodell für die Anpassung von Word  
 Wenn Sie ein Projekt auf Dokumentebene für Word erstellen, generiert Visual Studio eine Klasse mit dem Namen `ThisDocument`, die die Grundlage der Projektmappe bildet. Diese Klasse stellt das Dokument dar, das der Projektmappe zugeordnet ist, und bietet einen Ausgangspunkt zum Schreiben des Codes.  
  
 Weitere Informationen zur `ThisDocument` -Klasse und zu anderen Features, die Sie in einem Projekt auf Dokumentebene verwenden können, finden Sie unter [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Entwickeln von VSTO-Add-Ins für Word  
 Ein VSTO-Add-In für Microsoft Office Word besteht aus einer Assembly, die von Word geladen wird. Die Assembly erweitert Word normalerweise durch das Anpassen der UI und das Automatisieren von Word. Im Gegensatz zu einer Anpassung auf Dokumentebene, die einem bestimmten Dokument zugeordnet wird, sind Funktionen, die in ein VSTO-Add-In implementiert werden, nicht auf ein einzelnes Dokument beschränkt.  
  
 Wenn Sie ein VSTO-Add-In-Projekt für Word erstellen möchte, verwenden Sie die Add-In-Projektvorlagen von Word im Dialogfeld **Neues Projekt** von Visual Studio. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Allgemeine Informationen über die Funktionsweise von VSTO-Add-Ins finden Sie unter [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="word-add-in-programming-model"></a>Add-In-Programmiermodell von Word  
 Wenn Sie ein VSTO-Add-In-Projekt für Word erstellen, generiert Visual Studio eine Klasse namens `ThisAddIn`, die die Grundlage für die Projektmappe darstellt. Diese Klasse bietet einen Ausgangspunkt für das Schreiben des Codes, und sie macht auch das Word-Objektmodell für das VSTO-Add-In verfügbar.  
  
 Weitere Informationen zur `ThisAddIn` -Klasse und weitere Features, die in einem VSTO-Add-In verwendet werden können, finden Sie unter [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Customizing the User Interface of Word  
 Es gibt weitere Möglichkeiten, die Benutzeroberfläche von Word anzupassen. Einige Optionen sind für alle Projekttypen verfügbar, andere Optionen sind jedoch nur für VSTO-Add-Ins oder Anpassungen auf Dokumentebene verfügbar.  
  
### <a name="options-for-all-project-types"></a>Optionen für alle Projekttypen  
 In der folgenden Tabelle sind die Anpassungsoptionen aufgeführt, die sowohl für Anpassungen auf Dokumentebene als auch für VSTO-Add-Ins zur Verfügung stehen.  
  
|Aufgabe|Weitere Informationen|  
|----------|--------------------------|  
|Anpassen des Menübands|[Übersicht über das Menüband](../vsto/ribbon-overview.md)|  
|Hinzufügen von Windows Forms-Steuerelementen oder erweiterten Word-Steuerelemente zum angepassten Dokument (für eine Anpassung auf Dokumentebene) oder zu einem beliebigen geöffneten Dokument (für ein VSTO-Add-In).|[Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Vorgehensweise: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Vorgehensweise: Hinzufügen von Bookmark-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|  
  
### <a name="options-for-document-level-customizations"></a>Optionen für Anpassungen auf Dokumentebene  
 In der folgenden Tabelle sind Anpassungsoptionen aufgeführt, die nur für Anpassungen auf Dokumentebene zur Verfügung stehen.  
  
|Aufgabe|Weitere Informationen|  
|----------|--------------------------|  
|Hinzufügen eines Aktionsbereichs zum Dokument|[Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)<br /><br /> [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Fügen Sie der Dokumentoberfläche erweiterte XMLNode- und XMLNodes-Steuerelemente hinzu.|[Vorgehensweise: Hinzufügen von XMLNode-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Vorgehensweise: Hinzufügen von XMLNodes-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|  
  
### <a name="options-for-vsto-add-ins"></a>Optionen für VSTO-Add-Ins  
 In der folgenden Tabelle werden Anpassungsoptionen aufgeführt, die nur für VSTO-Add-Ins zur Verfügung stehen.  
  
|Aufgabe|Weitere Informationen|  
|----------|--------------------------|  
|Erstellen eines benutzerdefinierten Aufgabenbereichs|[Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Word Object Model Overview](../vsto/word-object-model-overview.md)|Hier finden Sie eine Übersicht über die wichtigsten Typen im Word-Objektmodell.|  
|[Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)|Hier finden Sie Informationen zu erweiterten Objekten (der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]), die in Word-Projektmappen verwendet werden können.|  
|[Übersicht über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)|Hier wird beschrieben, wie Sie Word-Dokumenten Windows Forms-Steuerelemente hinzufügen können.|  
|[Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokumentebene für Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Veranschaulicht, wie eine grundlegende Anpassung auf Dokumentebene für Word erstellt wird.|  
|[Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Veranschaulicht die Erstellung eines grundlegenden VSTO-Add-Ins für Word.|  
|[Exemplarische Vorgehensweise: Hinzufügen von Steuerelementen zu einem Dokument zur Laufzeit in einem VSTO-Add-In](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Veranschaulicht, wie Sie einem Dokument zur Laufzeit mithilfe eines VSTO-Add-Ins eine Windows Forms-Schaltfläche und ein <xref:Microsoft.Office.Tools.Word.RichTextContentControl> hinzufügen können.|  
|[Word 2010 in Office-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199020)|Hier finden Sie Links zu Artikeln und Referenzdokumentation zur Entwicklung von Word-Projektmappen (nicht spezifisch für die Office-Entwicklung mit Visual Studio).|  
  
  