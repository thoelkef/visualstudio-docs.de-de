---
title: "Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements | Microsoft Docs"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Datenquellenaktualisierungen"
  - "Daten [Office-Entwicklung in Visual Studio], Aktualisieren einer Datenquelle aus einem Dokument"
  - "Hoststeuerelemente [Office-Entwicklung in Visual Studio], Datenquellenaktualisierungen"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Datenquellen"
ms.assetid: b91025af-1eaa-44ee-88f2-71ecaa7a0440
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements
  Sie können ein Hoststeuerelement an eine Datenquelle binden und die Datenquelle mit den Änderungen aktualisieren, die im Steuerelement an den Daten vorgenommen werden. In diesem Prozess gibt es zwei Hauptschritte:  
  
1.  Aktualisieren der In\-Memory\-Datenquelle mit den geänderten Daten im Steuerelement. In der Regel ist die In\-Memory\-Datenquelle ein <xref:System.Data.DataSet>, eine <xref:System.Data.DataTable> oder ein anderes Datenobjekt.  
  
2.  Aktualisieren der Datenbank mit den geänderten Daten in der In\-Memory\-Datenquelle. Dies trifft nur zu, wenn die Datenquelle mit einer Back\-End\-Datenbank verbunden ist, beispielsweise einer SQL Server\- oder Microsoft Office Access\-Datenbank.  
  
 Weitere Informationen über Hoststeuerelemente und Datenbindung finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md) und [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Aktualisieren der In\-Memory\-Datenquelle  
 Standardmäßig speichern Hoststeuerelemente, die eine einfache Datenbindung ermöglichen \(z. B. Inhaltssteuerelemente auf einem Word\-Dokument oder NamedRange\-Steuerelemente auf einem Excel\-Arbeitsblatt\), keine Datenänderungen in der In\-Memory\-Datenquelle. Das heißt, wenn ein Endbenutzer einen Wert in einem Hoststeuerelement ändert und anschließend das Steuerelement verlässt, wird der neue Wert im Steuerelement nicht automatisch in der Datenquelle gespeichert.  
  
 Um die Daten in der Datenquelle zu speichern, können Sie Code erstellen, mit dem die Datenquelle als Reaktion auf ein bestimmtes Ereignis zur Laufzeit aktualisiert wird. Sie können das Steuerelement aber auch so konfigurieren, dass die Datenquelle automatisch aktualisiert wird, wenn sich der Wert im Steuerelement ändert.  
  
 <xref:Microsoft.Office.Tools.Excel.ListObject>\-Änderungen an der In\-Memory\-Datenquelle müssen nicht gespeichert werden. Wenn Sie ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement an Daten binden, speichert das <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement automatisch Änderungen in der In\-Memory\-Datenquelle, ohne dass zusätzlicher Code benötigt wird.  
  
#### So aktualisieren Sie die In\-Memory\-Datenquelle zur Laufzeit  
  
-   Rufen Sie die <xref:System.Windows.Forms.Binding.WriteValue%2A>\-Methode des <xref:System.Windows.Forms.Binding>\-Objekts auf, über das das Steuerelement an die Datenquelle gebunden ist.  
  
     Im folgenden Beispiel werden Änderungen, die an einem <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement auf einem Excel\-Arbeitsblatt vorgenommen wurden, in der Datenquelle gespeichert. Für dieses Beispiel wird davon ausgegangen, dass Sie ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement namens `namedRange1` haben, dessen <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>\-Eigenschaft an ein Feld in einer Datenquelle gebunden ist.  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#1)]  
  
### Automatisches Aktualisieren der In\-Memory\-Datenquelle  
 Sie können ein Steuerelement auch so konfigurieren, dass es die In\-Memory\-Datenquelle automatisch aktualisiert. In einem Projekt auf Dokumentebene ist dies mithilfe von Code oder mit dem Designer möglich. In einem VSTO Add\-In\-Projekt müssen Sie Code verwenden.  
  
##### So legen Sie fest, dass ein Steuerelement die In\-Memory\-Datenquelle automatisch über Code aktualisiert  
  
1.  Verwenden Sie den System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged \-Modus des <xref:System.Windows.Forms.Binding>\-Objekts, über das das Steuerelement an die Datenquelle gebunden ist. Es gibt zwei Optionen zum Aktualisieren der Datenquelle:  
  
    -   Um die Datenquelle zu aktualisieren, wenn das Steuerelement validiert wird, legen Sie diese Eigenschaft auf System.Windows.Forms.DataSourceUpdateMode.OnValidation fest.  
  
    -   Um die Datenquelle zu aktualisieren, wenn sich der Wert der datengebundenen Eigenschaft des Steuerelements ändert, legen Sie diese Eigenschaft auf System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged fest.  
  
        > [!NOTE]  
        >  Die System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged\-Option gilt nicht für Word\-Hoststeuerelemente, da Word keine Benachrichtigungen über Dokument\- oder Steuerelementänderungen bereitstellt. Diese Option kann jedoch für Windows Forms\-Steuerelemente auf Word\-Dokumenten verwendet werden.  
  
     Im folgenden Beispiel wird ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement so konfiguriert, dass die Datenquelle automatisch aktualisiert wird, wenn sich der Wert im Steuerelement ändert. Für dieses Beispiel wird davon ausgegangen, dass Sie ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement namens `namedRange1` haben, dessen <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>\-Eigenschaft an ein Feld in einer Datenquelle gebunden ist.  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#19)]  
  
##### So legen Sie mit dem Designer fest, dass ein Steuerelement die In\-Memory\-Datenquelle automatisch aktualisiert  
  
1.  Öffnen Sie in Visual Studio das Word\-Dokument oder die Excel\-Arbeitsmappe im Designer.  
  
2.  Klicken Sie auf das Steuerelement, von dem die Datenquelle automatisch aktualisiert werden soll.  
  
3.  Erweitern Sie im Fenster **Eigenschaften** die **\(DataBindings\)**\-Eigenschaft.  
  
4.  Klicken Sie neben der **\(Advanced\)**\-Eigenschaft auf die Schaltfläche mit den Auslassungszeichen \(![VisualStudioEllipsesButton-Bildschirmabbildung](../vsto/media/vbellipsesbutton.png "VisualStudioEllipsesButton-Bildschirmabbildung")\).  
  
5.  Klicken Sie im Dialogfeld **Formatierung und erweiterte Bindung** auf die Dropdownliste **Datenquellen\-Aktualisierungsmodus**, und wählen Sie einen der folgenden Werte aus:  
  
    -   Um die Datenquelle zu aktualisieren, wenn das Steuerelement validiert wird, wählen Sie **OnValidation** aus.  
  
    -   Um die Datenquelle zu aktualisieren, wenn sich der Wert der datengebundenen Eigenschaft des Steuerelements ändert, wählen Sie **OnPropertyChanged** aus.  
  
        > [!NOTE]  
        >  Die **OnPropertyChanged**\-Option gilt nicht für Word\-Hoststeuerelemente, da Word keine Benachrichtigungen über Dokument\- oder Steuerelementänderungen bereitstellt. Diese Option kann jedoch für Windows Forms\-Steuerelemente auf Word\-Dokumenten verwendet werden.  
  
6.  Schließen sie das Dialogfeld **Formatierung und erweiterte Bindung**.  
  
## Aktualisieren der Datenbank  
 Wenn die In\-Memory\-Datenquelle mit einer Datenbank verknüpft ist, müssen Sie die Datenbank mit den Änderungen an der Datenquelle aktualisieren. Weitere Informationen zum Aktualisieren einer Datenbank finden Sie unter [Speichern von Daten in Datasets](../Topic/Saving%20data%20back%20to%20the%20database.md) und [Gewusst wie: Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
#### So aktualisieren Sie die Datenbank  
  
1.  Rufen Sie die <xref:System.Windows.Forms.BindingSource.EndEdit%2A>\-Methode der <xref:System.Windows.Forms.BindingSource>\-Instanz für das Steuerelement auf.  
  
     Die <xref:System.Windows.Forms.BindingSource>\-Instanz wird automatisch generiert, wenn Sie einem Dokument oder einer Arbeitsmappe zur Entwurfszeit ein datengebundenes Steuerelement hinzufügen. Die <xref:System.Windows.Forms.BindingSource>\-Instanz verbindet das Steuerelement mit dem typisierten Dataset im Projekt. Weitere Informationen finden Sie unter [Übersicht über die BindingSource-Komponente](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f).  
  
     Für das folgende Codebeispiel wird vorausgesetzt, dass das Projekt eine <xref:System.Windows.Forms.BindingSource>\-Instanz namens `customersBindingSource` enthält.  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#20)]  
  
2.  Rufen Sie im Projekt die `Update`\-Methode des generierten TableAdapter auf.  
  
     Die TableAdapter\-Instanz wird automatisch generiert, wenn Sie einem Dokument oder einer Arbeitsmappe zur Entwurfszeit ein datengebundenes Steuerelement hinzufügen. Die TableAdapter\-Instanz verbindet das typisierte Dataset im Projekt mit der Datenbank. Weitere Informationen finden Sie unter [Übersicht über TableAdapters](/visual-studio/data-tools/tableadapter-overview).  
  
     Für das folgende Codebeispiel wird vorausgesetzt, dass eine Verbindung mit der Customers\-Tabelle der Northwind\-Datenbank besteht und dass das Projekt einen TableAdapter namens `customersTableAdapter` sowie ein typisiertes Dataset namens `northwindDataSet` enthält.  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#21)]  
  
## Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Speichern von Daten in Datasets](../Topic/Saving%20data%20back%20to%20the%20database.md)   
 [Gewusst wie: Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Gewusst wie: Ausführen eines Bildlaufs durch Datenbankdatensätze in einem Arbeitsblatt](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Gewusst wie: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Gewusst wie: Auffüllen von Dokumenten mit Daten von Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Gewusst wie: Auffüllen von Dokumente mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  