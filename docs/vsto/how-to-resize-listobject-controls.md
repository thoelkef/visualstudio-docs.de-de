---
title: 'Vorgehensweise: Größe von ListObject-Steuerelementen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e655305400915f1ac97a042ac1cca26e52a05ec5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909683"
---
# <a name="how-to-resize-listobject-controls"></a>Vorgehensweise: Größe von ListObject-Steuerelementen
  Sie legen die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements fest, wenn Sie es einer Microsoft Office Excel-Arbeitsmappe hinzufügen. Möglicherweise möchten Sie dessen Größe jedoch zu einem späteren Zeitpunkt ändern. Beispielsweise könnte es sein, dass Sie eine zweispaltige Liste in eine dreispaltige Liste ändern möchten.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Sie können die Größe <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelemente zur Entwurfszeit oder zur Laufzeit in Projekten auf Dokumentebene. Sie können die Größe <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt.  
  
 In diesem Thema werden die folgenden Aufgaben beschrieben:  
  
- [Größe von ListObject-Steuerelementen zur Entwurfszeit](#designtime)  
  
- [Größe von ListObject-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene](#runtimedoclevel)  
  
- [Größe von ListObject-Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt](#runtimeaddin)  
  
  Weitere Informationen zu <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelemente finden Sie [ListObject-Steuerelement](../vsto/listobject-control.md).  
  
  ![Link zum Video](../vsto/media/playvideo.gif "Link zum Video") eine entsprechende Videodemo finden Sie unter [Gewusst wie: Hinzufügen von Spalten zu einer datengebundenen List-Objekt zur Laufzeit? ](http://go.microsoft.com/fwlink/?LinkID=130318).  
  
##  <a name="designtime"></a> Ändern der Größe eines ListObject-Steuerelements zur Entwurfszeit  
 Sie können die Größe einer Liste ändern, indem Sie auf einen der Ziehpunkte klicken und diesen ziehen oder indem Sie die Größe im Dialogfeld **Größe der Liste ändern** neu definieren.  
  
### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>So ändern Sie die Größe einer Liste im Dialogfeld „Größe der Liste ändern“  
  
  
1.  Klicken Sie auf eine beliebige Stelle der <xref:Microsoft.Office.Tools.Excel.ListObject> Tabelle. Die **Tabellentools** > **Entwurf** Registerkarte im Menüband angezeigt wird.  
  
2.  Klicken Sie im Abschnitt mit Eigenschaften auf **Ändern der Größe der Tabelle**.  

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)
  
3.  Wählen Sie den neuen Datenbereich für die Tabelle ein.  
  
4.  Klicken Sie auf **OK**.  
  
##  <a name="runtimedoclevel"></a> Die Größe eines ListObject-Steuerelements zur Laufzeit in einem Projekt auf Dokumentebene  
 Sie können die Größe einer <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement zur Laufzeit mithilfe der <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> Methode. Mit dieser Methode ist es jedoch nicht möglich, das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement auf eine neue Position auf dem Arbeitsblatt zu verschieben. Die Überschriften müssen in derselben Zeile bleiben, und das in der Größe geänderte <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement muss das ursprüngliche Listenobjekt überlappen. Das in der Größe geänderte <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement muss eine Überschriftenzeile und mindestens eine Zeile mit Daten enthalten.  
  
### <a name="to-resize-a-list-object-programmatically"></a>So ändern Sie die Größe eines Listenobjekts programmgesteuert  
  
1.  Erstellen Sie ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement, das sich auf **über die Zellen** A1 **bis** B3 `Sheet1`erstreckt.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]  
  
2.  Ändern Sie die Größe der Liste, sodass sie die Zellen **A1** bis **C5**umfasst.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> Ändern der Größe eines ListObject zur Laufzeit in einem VSTO-Add-in-Projekt  
 Sie können die Größe einer <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement auf jedem geöffneten Arbeitsblatt zur Laufzeit. Weitere Informationen zur Vorgehensweise beim Hinzufügen einer <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements zu einem Arbeitsblatt mithilfe eines VSTO-Add-Ins, finden Sie unter [Vorgehensweise: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
### <a name="to-resize-a-list-object-programmatically"></a>So ändern Sie die Größe eines Listenobjekts programmgesteuert  
  
1.  Erstellen Sie ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement, das sich auf **über die Zellen** A1 **bis** B3 `Sheet1`erstreckt.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]  
  
2.  Ändern Sie die Größe der Liste, sodass sie die Zellen **A1** bis **C5**umfasst.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject-Steuerelement](../vsto/listobject-control.md)   
 [Vorgehensweise: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Vorgehensweise: Größe von Bookmark-Steuerelementen](../vsto/how-to-resize-bookmark-controls.md)   
 [Vorgehensweise: Ändern der Größe von NamedRange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)  
