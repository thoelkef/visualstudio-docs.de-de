---
title: "Gewusst wie: &#220;berpr&#252;fen der Daten, wenn einem ListObject-Steuerelement eine neue Zeile hinzugef&#252;gt wird"
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
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Überprüfen von Daten"
  - "ListObject-Steuerelement, neue Zeile"
  - "ListObject-Steuerelement, Überprüfen von Daten"
ms.assetid: 107bce92-e5ef-40be-8c05-cd6861d39d75
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Gewusst wie: &#220;berpr&#252;fen der Daten, wenn einem ListObject-Steuerelement eine neue Zeile hinzugef&#252;gt wird
  Benutzer können einem <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement, das an Daten gebunden ist, neue Zeilen hinzufügen. Sie können die Daten des Benutzers überprüfen, bevor Sie Änderungen in einem Commit an die Datenquelle übertragen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Datenvalidierung  
 Sobald einem <xref:Microsoft.Office.Tools.Excel.ListObject>, das an Daten gebunden ist, eine Zeile hinzugefügt wird, wird das <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>\-Ereignis ausgelöst. Sie können dieses Ereignis behandeln, um Ihre Datenüberprüfung durchzuführen. Wenn die Anwendung z. B. erfordert, dass der Datenquelle nur Mitarbeiter zwischen 18 und 65 Jahren hinzugefügt werden, können Sie vor dem Hinzufügen der Zeile überprüfen, ob das eingegebene Alter innerhalb dieses Bereichs liegt.  
  
> [!NOTE]  
>  Zusätzlich zum Client sollte die Benutzereingabe auch immer auf dem Server überprüft werden. Weitere Informationen finden Sie unter [Sichere Clientanwendungen](http://msdn.microsoft.com/library/6239592e-fa7d-4dea-9f00-d296d0048b01).  
  
#### So überprüfen Sie Daten, wenn dem datengebundenen ListObject\-Steuerelement eine neue Zeile hinzugefügt wird  
  
1.  Erstellen Sie Variablen für die ID und <xref:System.Data.DataTable> auf Klassenebene.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#8)]  
  
2.  Erstellen Sie eine neue <xref:System.Data.DataTable>, und fügen Sie dem `Startup`\-Ereignishandler der `Sheet1`\-Klasse \(in einem Projekt auf Dokumentebene\) oder der `ThisAddIn`\-Klasse \(in einem VSTO\-Add\-In\-Projekt\) Beispielspalten und \-daten hinzu.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#9)]  
  
3.  Fügen Sie dem `list1_BeforeAddDataBoundRow`\-Ereignishandler Code hinzu, um zu überprüfen, ob das eingegebene Alter innerhalb des zulässigen Bereichs liegt.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#10)]  
  
## Kompilieren des Codes  
 In diesem Codebeispiel wird davon ausgegangen, dass Sie in dem Arbeitsblatt, in dem dieser Code angezeigt wird, über ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Element namens `list1` verfügen.  
  
## Siehe auch  
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject-Steuerelement](../vsto/listobject-control.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Gewusst wie: Zuordnung von ListObject-Spalten zu Daten](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  