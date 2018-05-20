---
title: 'Vorgehensweise: Überprüfen von Daten, wenn einem ListObject-Steuerelement eine neue Zeile hinzugefügt wird'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55dc8852952482914bc57a41579163c90672d1db
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Vorgehensweise: Überprüfen von Daten, wenn einem ListObject-Steuerelement eine neue Zeile hinzugefügt wird
  Benutzer können einem <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement, das an Daten gebunden ist, neue Zeilen hinzufügen. Sie können die Daten des Benutzers überprüfen, bevor Sie Änderungen in einem Commit an die Datenquelle übertragen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="data-validation"></a>Überprüfen von Daten  
 Sobald einem <xref:Microsoft.Office.Tools.Excel.ListObject> , das an Daten gebunden ist, eine Zeile hinzugefügt wird, wird das <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> -Ereignis ausgelöst. Sie können dieses Ereignis behandeln, um Ihre Datenüberprüfung durchzuführen. Beispielsweise, wenn Ihre Anwendung erfordert, dass die Datenquelle nur Mitarbeiter zwischen 18 und 65 Jahren hinzugefügt werden können, stellen Sie sicher, dass das eingegebene Alter innerhalb dieses Bereichs liegt, bevor die Zeile hinzugefügt wird.  
  
> [!NOTE]  
>  Zusätzlich zum Client sollte die Benutzereingabe auch immer auf dem Server überprüft werden. Weitere Informationen finden Sie unter [sichere Clientanwendungen](/dotnet/framework/data/adonet/secure-client-applications).  
  
### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>So überprüfen Sie Daten, wenn dem datengebundenen ListObject-Steuerelement eine neue Zeile hinzugefügt wird  
  
1.  Erstellen Sie Variablen für die ID und <xref:System.Data.DataTable> auf Klassenebene.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]  
  
2.  Erstellen Sie ein neues <xref:System.Data.DataTable> und fügen Sie Beispielspalten und Daten in der `Startup` -Ereignishandler, der die `Sheet1` -Klasse (in einem Projekt auf Dokumentebene) oder `ThisAddIn` -Klasse (in einem VSTO-Add-in-Projekt).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]  
  
3.  Fügen Sie dem `list1_BeforeAddDataBoundRow` -Ereignishandler Code hinzu, um zu überprüfen, ob das eingegebene Alter innerhalb des zulässigen Bereichs liegt.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 In diesem Codebeispiel wird davon ausgegangen, dass Sie in dem Arbeitsblatt, in dem dieser Code angezeigt wird, über ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Element namens `list1` verfügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject-Steuerelement](../vsto/listobject-control.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Vorgehensweise: Zuordnung von ListObject-Spalten an Daten](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  