---
title: "Exemplarische Vorgehensweise: Komplexe Datenbindung in einem VSTO-Add-In-Projekt | Microsoft Docs"
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
  - "Datenbindung [Office-Entwicklung in Visual Studio], Excel"
  - "Daten [Office-Entwicklung in Visual Studio], Binden von Daten"
  - "Komplexe Daten [Office-Entwicklung in Visual Studio]"
ms.assetid: ff52fb56-1f67-4ae2-a3d1-93038619d4e6
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Exemplarische Vorgehensweise: Komplexe Datenbindung in einem VSTO-Add-In-Projekt
  Sie können in VSTO\-Add\-In\-Projekten Daten an Hoststeuerelemente und Windows Forms\-Steuerelemente binden. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie einem Microsoft Office Excel\-Arbeitsblatt zur Laufzeit Steuerelemente hinzugefügt und diese Steuerelemente an Daten gebunden werden.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen eines <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelements zu einem Arbeitsblatt zur Laufzeit  
  
-   Erstellen eines <xref:System.Windows.Forms.BindingSource>\-Objekts, das das Steuerelement mit einer Instanz eines Datasets verbindet  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Zugriff auf eine aktive Instanz von SQL Server 2005 oder SQL Server 2005 Express, an die die `AdventureWorksLT`\-Beispieldatenbank angefügt ist. Sie können die `AdventureWorksLT`\-Datenbank von der [CodePlex\-Website](http://go.microsoft.com/fwlink/?LinkId=115611) herunterladen. Weitere Informationen zum Anhängen von Datenbanken finden Sie in den folgenden Themen:  
  
    -   Informationen zum Anfügen einer Datenbank mit SQL Server Management Studio oder SQL Server Management Studio Express finden Sie unter [Gewusst wie: Anfügen einer Datenbank \(SQL Server Management Studio\)](http://msdn.microsoft.com/de-de/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Informationen zum Anfügen einer Datenbank über die Befehlszeile finden Sie unter [Gewusst wie: Anfügen einer Datenbankdatei an SQL Server Express](http://msdn.microsoft.com/de-de/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## Erstellen eines neuen Projekts  
 Der erste Schritt besteht im Erstellen eines VSTO\-Add\-In\-Projekts für Excel.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie mit Visual Basic oder C\# ein Excel\-VSTO\-Add\-In\-Projekt, das den Namen **Füllen von Arbeitsblättern aus einer Datenbank** hat.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die Datei `ThisAddIn.vb` oder `ThisAddIn.cs` und fügt dem **Projektmappen\-Explorer** das Projekt **Füllen von Arbeitsblättern aus einer Datenbank** hinzu.  
  
## Erstellen einer Datenquelle  
 Verwenden das Fenster **Datenquellen**, um dem Projekt ein typisiertes Dataset hinzuzufügen.  
  
#### So fügen Sie dem Projekt ein typisiertes Dataset hinzu  
  
1.  Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie in der Menüleiste **Ansicht**, **Weitere Fenster** und **Datenquellen** wählen.  
  
2.  Wählen Sie **Neue Datenquelle hinzufügen**, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Klicken Sie auf **Datenbank**, und klicken Sie dann auf **Weiter**.  
  
4.  Wenn eine Verbindung mit der `AdventureWorksLT`\-Datenbank vorhanden ist, wählen Sie diese Verbindung aus, und klicken Sie auf **Weiter**.  
  
     Klicken Sie andernfalls auf **Neue Verbindung**, und erstellen Sie die neue Verbindung im Dialogfeld **Verbindung hinzufügen**. Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
5.  Klicken Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** auf **Weiter**.  
  
6.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**, und wählen Sie **Address \(SalesLT\)** aus.  
  
7.  Klicken Sie auf **Fertig stellen**.  
  
     Öffnen Sie im **Projektmappen\-Explorer** die Datei „AdventureWorksLTDataSet.xsd“. In dieser Datei sind die folgenden Elemente definiert:  
  
    -   Ein typisiertes Dataset namens `AdventureWorksLTDataSet`. Dieses Dataset entspricht dem Inhalt der **Address \(SalesLT\)**\-Tabelle in der AdventureWorksLT\-Datenbank.  
  
    -   Eine TableAdapter mit dem Namen `AddressTableAdapter`. Dieser TableAdapter kann zum Lesen von Daten aus und zum Schreiben von Daten in `AdventureWorksLTDataSet` verwendet werden. Weitere Informationen finden Sie unter [Übersicht über TableAdapters](/visual-studio/data-tools/tableadapter-overview).  
  
     Zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise verwenden Sie beide Objekte.  
  
## Erstellen von Steuerelementen und Binden von Steuerelementen an Daten  
 In dieser exemplarischen Vorgehensweise zeigt das <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement alle von Ihnen ausgewählten Daten in der Tabelle an, sobald der Benutzer die Arbeitsmappe öffnet. Das Listenobjekt stellt mit einer <xref:System.Windows.Forms.BindingSource> eine Verbindung zwischen Steuerelement und Datenbank her.  
  
 Weitere Informationen zum Binden von Steuerelementen an Daten finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### So fügen Sie das Listenobjekt, das Dataset und den Tabellenadapter hinzu  
  
1.  Deklarieren Sie in der `ThisAddIn`\-Klasse die folgenden Steuerelemente, um die `Address`\-Tabelle des `AdventureWorksLTDataSet`\-Datsets anzuzeigen.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#1)]  
  
2.  Fügen Sie der `ThisAddIn_Startup`\-Methode den folgenden Code hinzu, um das Dataset zu initialisieren und es mit Daten aus dem `AdventureWorksLTDataSet`\-Dataset zu füllen.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#2)]  
  
3.  Fügen Sie der `ThisAddIn_Startup`\-Methode folgenden Code hinzu. Dadurch wird ein Hostelement generiert, das das Arbeitsblatt erweitert. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-csharp[Trin_ExcelAddInDatabase#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#3)]  
  
4.  Erstellen Sie einen Bereich und fügen das <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement hinzu.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#4)]  
  
5.  Binden Sie das Listenobjekt mithilfe der <xref:System.Windows.Forms.BindingSource> an das `AdventureWorksLTDataSet`. Übergeben Sie die Namen der Spalten, die an das Listenobjekt gebunden werden sollen.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#5)]  
  
## Testen des Add\-Ins  
 Beim Öffnen von Excel zeigt das <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement die Daten aus der `Address`\-Tabelle des `AdventureWorksLTDataSet`\-Datasets .  
  
#### So testen Sie das VSTO\-Add\-In  
  
-   Drücken Sie **F5**.  
  
     Im Arbeitsblatt wird ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement namens `addressListObject` erstellt. Gleichzeitig werden dem Projekt ein Datasetobjekt namens `adventureWorksLTDataSet` und ein <xref:System.Windows.Forms.BindingSource>\-Objekt namens `addressBindingSource` hinzugefügt. Das <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement ist an das <xref:System.Windows.Forms.BindingSource>\-Objekt gebunden, das wiederum an das Datasetobjekt gebunden ist.  
  
## Siehe auch  
 [Daten in Office-Lösungen](../vsto/data-in-office-solutions.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Gewusst wie: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Gewusst wie: Auffüllen von Dokumente mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Gewusst wie: Auffüllen von Dokumenten mit Daten von Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Gewusst wie: Ausführen eines Bildlaufs durch Datenbankdatensätze in einem Arbeitsblatt](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Exemplarische Vorgehensweise: Einfache Datenbindung in Projekten auf Dokumentebene](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)   
 [Exemplarische Vorgehensweise: Komplexe Datenbindung in Projekten auf Dokumentebene](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)   
 [Übersicht über die Verwendung lokaler Datenbankdateien in Office-Lösungen](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Übersicht über die Verwendung lokaler Datenbankdateien in Office-Lösungen](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Herstellen einer Verbindung mit Daten in Windows Forms-Anwendungen](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Übersicht über die BindingSource-Komponente](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  