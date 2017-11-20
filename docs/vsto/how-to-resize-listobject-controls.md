---
title: "Vorgehensweise: Ändern der Größe eines ListObject-Steuerelements | Microsoft Docs"
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
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
ms.assetid: a4c7dceb-7b55-447e-9b88-c3596a2fc361
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9aafcb9a131743c09d139f6f210c0d50425f4cba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-resize-listobject-controls"></a>Gewusst wie: Ändern der Größe von ListObject-Steuerelementen
  Sie legen die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements fest, wenn Sie es einer Microsoft Office Excel-Arbeitsmappe hinzufügen. Möglicherweise möchten Sie dessen Größe jedoch zu einem späteren Zeitpunkt ändern. Beispielsweise könnte es sein, dass Sie eine zweispaltige Liste in eine dreispaltige Liste ändern möchten.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements in einem Projekt auf Dokumentebene zur Entwurfszeit oder zur Laufzeit ändern. Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements in einem VSTO-Add-In-Projekt zur Laufzeit ändern.  
  
 In diesem Thema werden die folgenden Aufgaben beschrieben:  
  
-   [Ändern der Größe eines ListObject-Steuerelements zur Entwurfszeit](#designtime)  
  
-   [Ändern der Größe eines ListObject-Steuerelements zur Laufzeit in einem Projekt auf Dokumentebene](#runtimedoclevel)  
  
-   [Ändern der Größe eines ListObject-Steuerelements zur Laufzeit in einem VSTO-Add-In-Projekt](#runtimeaddin)  
  
 Weitere Informationen zu <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelementen finden Sie unter [ListObject Control](../vsto/listobject-control.md).  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [wie Do I: Add Columns, ein Data-Bound List Object at RunTime?](http://go.microsoft.com/fwlink/?LinkID=130318).  
  
##  <a name="designtime"></a> Ändern der Größe eines ListObject-Steuerelements zur Entwurfszeit  
 Sie können die Größe einer Liste ändern, indem Sie auf einen der Ziehpunkte klicken und diesen ziehen oder indem Sie die Größe im Dialogfeld **Größe der Liste ändern** neu definieren.  
  
#### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>So ändern Sie die Größe einer Liste im Dialogfeld „Größe der Liste ändern“  
  
  
1.  Klicken Sie auf eine beliebige Stelle der <xref:Microsoft.Office.Tools.Excel.ListObject> Tabelle. Die **Tabellentools, Design** Registerkarte im Menüband angezeigt wird.  
  
2.  Klicken Sie im Abschnitt "Eigenschaften", auf **Größe Tabelle**.  

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)
  
3.  Wählen Sie den neuen Datenbereich für die Tabelle ein.  
  
4.  Klicken Sie auf **OK**.  
  
##  <a name="runtimedoclevel"></a> Ändern der Größe eines ListObject-Steuerelements zur Laufzeit in einem Projekt auf Dokumentebene  
 Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements zur Laufzeit ändern, indem Sie die <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> -Methode verwenden. Mit dieser Methode ist es jedoch nicht möglich, das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement auf eine neue Position auf dem Arbeitsblatt zu verschieben. Die Überschriften müssen in derselben Zeile bleiben, und das in der Größe geänderte <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement muss das ursprüngliche Listenobjekt überlappen. Das in der Größe geänderte <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement muss eine Überschriftenzeile und mindestens eine Zeile mit Daten enthalten.  
  
#### <a name="to-resize-a-list-object-programmatically"></a>So ändern Sie die Größe eines Listenobjekts programmgesteuert  
  
1.  Erstellen Sie ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement, das sich auf **über die Zellen** A1 **bis** B3 `Sheet1`erstreckt.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]  
  
2.  Ändern Sie die Größe der Liste, sodass sie die Zellen **A1** bis **C5**umfasst.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> Ändern der Größe eines ListObject zur Laufzeit in einem VSTO-Add-In-Projekt  
 Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements in jedem beliebigen geöffneten Arbeitsblatt zur Laufzeit ändern. Weitere Informationen zum Hinzufügen eines <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements zu einem Arbeitsblatt mit einem VSTO-Add-In finden Sie unter [How to: Add ListObject Controls to Worksheets](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
#### <a name="to-resize-a-list-object-programmatically"></a>So ändern Sie die Größe eines Listenobjekts programmgesteuert  
  
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
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject-Steuerelement](../vsto/listobject-control.md)   
 [Vorgehensweise: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Vorgehensweise: Ändern der Größe Lesezeichen-Steuerelementen](../vsto/how-to-resize-bookmark-controls.md)   
 [Vorgehensweise: Ändern der Größe von NamedRange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)  
  
  