---
title: 'Exemplarische Vorgehensweise: Komplexe Datenbindung in einem VSTO-add-in-Projekt | Microsoft Docs'
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
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 95f8d2d30bb5d8bedfe70f0b15f9e956d91f4345
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Exemplarische Vorgehensweise: Komplexe Datenbindung in einem VSTO-Add-In-Projekt
  Sie können in VSTO-Add-In-Projekten Daten an Hoststeuerelemente und Windows Forms-Steuerelemente binden. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie einem Microsoft Office Excel-Arbeitsblatt zur Laufzeit Steuerelemente hinzugefügt und diese Steuerelemente an Daten gebunden werden.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen eines <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements zu einem Arbeitsblatt zur Laufzeit  
  
-   Erstellen eines <xref:System.Windows.Forms.BindingSource> -Objekts, das das Steuerelement mit einer Instanz eines Datasets verbindet  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Zugriff auf eine aktive Instanz von SQL Server 2005 oder SQL Server 2005 Express, an die die `AdventureWorksLT` -Beispieldatenbank angefügt ist. Sie können die `AdventureWorksLT` -Datenbank von der [CodePlex-Website](http://go.microsoft.com/fwlink/?LinkId=115611)herunterladen. Weitere Informationen zum Anhängen von Datenbanken finden Sie in den folgenden Themen:  
  
    -   Informationen zum Anfügen einer Datenbank mit SQL Server Management Studio oder SQL Server Management Studio Express finden Sie unter [Gewusst wie: Anfügen einer Datenbank (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Informationen zum Anfügen einer Datenbank über die Befehlszeile finden Sie unter [Gewusst wie: Anfügen einer Datenbankdatei an SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="creating-a-new-project"></a>Erstellen eines neuen Projekts  
 Der erste Schritt besteht im Erstellen eines VSTO-Add-In-Projekts für Excel.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie mit Visual Basic oder C# ein Excel-VSTO-Add-In-Projekt, das den Namen **Füllen von Arbeitsblättern aus einer Datenbank**hat.  
  
     Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die Datei `ThisAddIn.vb` oder `ThisAddIn.cs` und fügt dem **Projektmappen-Explorer** das Projekt **Füllen von Arbeitsblättern aus einer Datenbank**hinzu.  
  
## <a name="creating-a-data-source"></a>Erstellen einer Datenquelle  
 Verwenden das Fenster **Datenquellen** , um dem Projekt ein typisiertes Dataset hinzuzufügen.  
  
#### <a name="to-add-a-typed-dataset-to-the-project"></a>So fügen Sie dem Projekt ein typisiertes Dataset hinzu  
  
1.  Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie in der Menüleiste **Ansicht**, **Weitere Fenster**und **Datenquellen**wählen.  
  
2.  Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.  
  
3.  Klicken Sie auf **Datenbank**, und klicken Sie dann auf **Weiter**.  
  
4.  Wenn eine Verbindung mit der `AdventureWorksLT` -Datenbank vorhanden ist, wählen Sie diese Verbindung aus, und klicken Sie auf **Weiter**.  
  
     Klicken Sie andernfalls auf **Neue Verbindung**, und erstellen Sie die neue Verbindung im Dialogfeld **Verbindung hinzufügen** . Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).  
  
5.  Klicken Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** auf **Weiter**.  
  
6.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen** , und wählen Sie **Address (SalesLT)**aus.  
  
7.  Klicken Sie auf **Fertig stellen**.  
  
     Öffnen Sie im **Projektmappen-Explorer**die Datei „AdventureWorksLTDataSet.xsd“. In dieser Datei sind die folgenden Elemente definiert:  
  
    -   Ein typisiertes Dataset namens `AdventureWorksLTDataSet`. Dieses Dataset entspricht dem Inhalt der **Address (SalesLT)** -Tabelle in der AdventureWorksLT-Datenbank.  
  
    -   Einen TableAdapter namens `AddressTableAdapter`. Diese TableAdapter dienen zum Lesen und Schreiben von Daten in der `AdventureWorksLTDataSet`. Weitere Informationen finden Sie unter [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise verwenden Sie beide Objekte.  
  
## <a name="creating-controls-and-binding-controls-to-data"></a>Erstellen von Steuerelementen und Binden von Steuerelementen an Daten  
 In dieser exemplarischen Vorgehensweise zeigt das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement alle von Ihnen ausgewählten Daten in der Tabelle an, sobald der Benutzer die Arbeitsmappe öffnet. Das Listenobjekt stellt mit einer <xref:System.Windows.Forms.BindingSource> eine Verbindung zwischen Steuerelement und Datenbank her.  
  
 Weitere Informationen zum Binden von Steuerelementen an Daten finden Sie unter [Binding Data to Controls in Office Solutions](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>So fügen Sie das Listenobjekt, das Dataset und den Tabellenadapter hinzu  
  
1.  Deklarieren Sie in der `ThisAddIn` -Klasse die folgenden Steuerelemente, um die `Address` -Tabelle des `AdventureWorksLTDataSet` -Datsets anzuzeigen.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]  
  
2.  Fügen Sie der `ThisAddIn_Startup` -Methode den folgenden Code hinzu, um das Dataset zu initialisieren und es mit Daten aus dem `AdventureWorksLTDataSet` -Dataset zu füllen.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]  
  
3.  Fügen Sie der `ThisAddIn_Startup` -Methode folgenden Code hinzu. Dadurch wird ein Hostelement generiert, das das Arbeitsblatt erweitert. Weitere Informationen finden Sie unter [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]  
  
4.  Erstellen Sie einen Bereich und fügen das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement hinzu.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]  
  
5.  Binden Sie das Listenobjekt mithilfe der `AdventureWorksLTDataSet` an das <xref:System.Windows.Forms.BindingSource>. Übergeben Sie die Namen der Spalten, die an das Listenobjekt gebunden werden sollen.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]  
  
## <a name="testing-the-add-in"></a>Testen des Add-Ins  
 Beim Öffnen von Excel zeigt das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement die Daten aus der `Address` -Tabelle des `AdventureWorksLTDataSet` -Datasets .  
  
#### <a name="to-test-the-vsto-add-in"></a>So testen Sie das VSTO-Add-In  
  
-   Drücken Sie **F5**.  
  
     Im Arbeitsblatt wird ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement namens `addressListObject` erstellt. Gleichzeitig werden dem Projekt ein Datasetobjekt namens `adventureWorksLTDataSet` und ein <xref:System.Windows.Forms.BindingSource> -Objekt namens `addressBindingSource` hinzugefügt. Das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement ist an das <xref:System.Windows.Forms.BindingSource>-Objekt gebunden, das wiederum an das Datasetobjekt gebunden ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Vorgehensweise: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Vorgehensweise: Führen Sie einen Bildlauf durch Datenbankdatensätze in einem Arbeitsblatt](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Exemplarische Vorgehensweise: Einfache Datenbindung in einem Projekt auf Dokumentebene](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)   
 [Exemplarische Vorgehensweise: Komplexe Datenbindung in einem Projekt auf Dokumentebene](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)   
 [Verwendung lokaler Datenbankdateien in Office-Projektmappen (Übersicht)](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Neue Datenquellen hinzufügen](/visualstudio/data-tools/add-new-data-sources)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Verwendung lokaler Datenbankdateien in Office-Projektmappen (Übersicht)](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Herstellen einer Verbindung mit Daten in Windows Forms-Anwendungen](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Übersicht über die BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  