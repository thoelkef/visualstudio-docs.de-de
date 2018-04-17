---
title: Diagramm-Steuerelement | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c473c026f5d5f9a5919626fb667994e6ffdc01f4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="chart-control"></a>Chart Control
  Das <xref:Microsoft.Office.Tools.Excel.Chart>-Steuerelement ist ein Diagrammobjekt, das Ereignisse verfügbar macht. Beim Hinzufügen eines Diagramms zu einem Arbeitsblatt erstellt Visual Studio ein <xref:Microsoft.Office.Tools.Excel.Chart>-Objekt, für das Sie direkt programmieren können, ohne das Objektmodell von Microsoft Office Excel zu durchlaufen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="creating-the-control"></a>Erstellen des Steuerelements  
 Sie können einem Microsoft Office Excel-Arbeitsblatt in einem Projekt auf Dokumentebene <xref:Microsoft.Office.Tools.Excel.Chart>-Steuerelemente zur Entwurfszeit oder zur Laufzeit hinzufügen.  
  
 Sie können einem Arbeitsblatt <xref:Microsoft.Office.Tools.Excel.Chart>-Steuerelemente zur Laufzeit in einem VSTO-Add-In hinzufügen. Weitere Informationen finden Sie unter [wie: Hinzufügen von Diagrammsteuerelementen zu Arbeitsblättern](../vsto/how-to-add-chart-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Dynamisch erstellte Diagrammobjekte werden nicht im Arbeitsblatt als Hoststeuerelemente dauerhaft gespeichert, wenn das Arbeitsblatt geschlossen wird. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="formatting"></a>Formatierung  
 Die gesamte Formatierung, die auf <xref:Microsoft.Office.Interop.Excel.Chart> angewendet werden kann, ist auch auf ein <xref:Microsoft.Office.Tools.Excel.Chart>-Steuerelement anwendbar. Dies umfasst Rahmen, Schriftarten, Diagrammtypen, Gitternetzlinien, Legenden und Datenbezeichnungen.  
  
## <a name="events"></a>Ereignisse  
 Die folgenden Ereignisse sind für das <xref:Microsoft.Office.Tools.Excel.Chart>-Steuerelement verfügbar:  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Resize>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>  
  
## <a name="see-also"></a>Siehe auch  
 [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)   
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Vorgehensweise: Hinzufügen von Diagrammsteuerelementen zu Arbeitsblättern](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  