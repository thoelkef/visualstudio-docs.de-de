---
title: "Exemplarische Vorgehensweise: Einfache Datenbindung in einem VSTO-Add-In-Projek | Microsoft Docs"
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
  - "Daten [Office-Entwicklung in Visual Studio], Binden von Daten"
  - "Datenbindung [Office-Entwicklung in Visual Studio], Word"
  - "Daten [Office-Entwicklung in Visual Studio], Einfaches Binden von Daten"
ms.assetid: b248d194-a8b1-4f87-94c4-24e940eea1fd
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Exemplarische Vorgehensweise: Einfache Datenbindung in einem VSTO-Add-In-Projek
  Sie können in VSTO\-Add\-In\-Projekten Daten an Hoststeuerelemente und Windows Forms\-Steuerelemente binden. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie einem Microsoft Office Word\-Dokument zur Laufzeit Steuerelemente hinzugefügt und diese Steuerelemente an Daten gebunden werden.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen eines <xref:Microsoft.Office.Tools.Word.ContentControl>\-Steuerelements zu einem Dokument zur Laufzeit  
  
-   Erstellen eines <xref:System.Windows.Forms.BindingSource>\-Objekts, das das Steuerelement mit einer Instanz eines Datasets verbindet  
  
-   Ermöglichen, dass Benutzer durch die Datensätze scrollen und diese im Steuerelement anzeigen können  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Zugriff auf eine aktive Instanz von SQL Server 2005 oder SQL Server 2005 Express, an die die `AdventureWorksLT`\-Beispieldatenbank angefügt ist. Sie können die `AdventureWorksLT`\-Datenbank von der [CodePlex\-Website](http://go.microsoft.com/fwlink/?LinkId=115611) herunterladen. Weitere Informationen zum Anhängen von Datenbanken finden Sie in den folgenden Themen:  
  
    -   Informationen zum Anfügen einer Datenbank mit SQL Server Management Studio oder SQL Server Management Studio Express finden Sie unter [Gewusst wie: Anfügen einer Datenbank \(SQL Server Management Studio\)](http://msdn.microsoft.com/de-de/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Informationen zum Anfügen einer Datenbank über die Befehlszeile finden Sie unter [Gewusst wie: Anfügen einer Datenbankdatei an SQL Server Express](http://msdn.microsoft.com/de-de/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## Erstellen eines neuen Projekts  
 Der erste Schritt besteht im Erstellen eines VSTO\-Add\-In\-Projekts für Word.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie mit Visual Basic oder C\# ein Word\-VSTO\-Add\-In\-Projekt, das den Namen **Füllen von Dokumenten aus einer Datenbank** hat.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die Datei „ThisAddIn.vb“ oder „ThisAddIn.cs“ und fügt dem **Projektmappen\-Explorer** das Projekt **Füllen von Dokumenten aus einer Datenbank** hinzu.  
  
2.  Wenn das Projekt für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] vorgesehen ist, fügen Sie einen Verweis auf die Assembly „Microsoft.Office.Tools.Word.v4.0.Utilities.dll“ hinzu. Dieser Verweis ist erforderlich, um später in dieser exemplarischen Vorgehensweise dem Dokument programmgesteuert Windows Forms\-Steuerelemente hinzuzufügen.  
  
## Erstellen einer Datenquelle  
 Verwenden Sie das Fenster **Datenquellen**, um dem Projekt ein typisiertes Dataset hinzuzufügen.  
  
#### So fügen Sie dem Projekt ein typisiertes Dataset hinzu  
  
1.  Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie in der Menüleiste **Ansicht**, **Weitere Fenster** und **Datenquellen** wählen.  
  
2.  Wählen Sie **Neue Datenquelle hinzufügen**, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Klicken Sie auf **Datenbank**, und klicken Sie dann auf **Weiter**.  
  
4.  Wenn eine Verbindung mit der `AdventureWorksLT`\-Datenbank vorhanden ist, wählen Sie diese Verbindung aus, und klicken Sie auf **Weiter**.  
  
     Klicken Sie andernfalls auf **Neue Verbindung**, und erstellen Sie die neue Verbindung im Dialogfeld **Verbindung hinzufügen**. Weitere Informationen finden Sie unter [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
5.  Klicken Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** auf **Weiter**.  
  
6.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**, und wählen Sie **Customer \(SalesLT\)** aus.  
  
7.  Klicken Sie auf **Fertig stellen**.  
  
     Die Datei „AdventureWorksLTDataSet.xsd“ wird dem **Projektmappen\-Explorer** hinzugefügt. In dieser Datei sind die folgenden Elemente definiert:  
  
    -   Ein typisiertes Dataset namens `AdventureWorksLTDataSet`. Dieses Dataset entspricht dem Inhalt der **Customer \(SalesLT\)**\-Tabelle in der AdventureWorksLT\-Datenbank.  
  
    -   Eine TableAdapter mit dem Namen `CustomerTableAdapter`. Dieser TableAdapter kann zum Lesen von Daten aus und zum Schreiben von Daten in `AdventureWorksLTDataSet` verwendet werden. Weitere Informationen finden Sie unter [Übersicht über TableAdapters](/visual-studio/data-tools/tableadapter-overview).  
  
     Zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise verwenden Sie beide Objekte.  
  
## Erstellen von Steuerelementen und Binden von Steuerelementen an Daten  
 Die Benutzeroberfläche zum Anzeigen von Datensätzen hat in dieser exemplarischen Vorgehensweise einen sehr begrenzten Umfang, und sie wird direkt im Dokument erstellt. In einem <xref:Microsoft.Office.Tools.Word.ContentControl>\-Steuerelement wird jeweils ein einzelner Datensatz angezeigt, und mit zwei <xref:Microsoft.Office.Tools.Word.Controls.Button>\-Steuerelementen können Sie nach oben und unten durch die Datensätze scrollen. Im Inhaltssteuerelement wird ein <xref:System.Windows.Forms.BindingSource>\-Objekt verwendet, um eine Verbindung mit der Datenbank herzustellen.  
  
 Weitere Informationen zum Binden von Steuerelementen an Daten finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### So erstellen Sie die Benutzeroberfläche im Dokument  
  
1.  Deklarieren Sie in der `ThisAddIn`\-Klasse die folgenden Steuerelemente, um die `Customer`\-Tabelle der `AdventureWorksLTDataSet`\-Datenbank anzuzeigen und sie durchlaufen zu können.  
  
     [!code-csharp[Trin_WordAddInDatabase#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDatabase#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#1)]  
  
2.  Fügen Sie der `ThisAddIn_Startup`\-Methode den folgenden Code hinzu, um das Dataset zu initialisieren und es mit Daten aus der `AdventureWorksLTDataSet`\-Datenbank zu füllen.  
  
     [!code-csharp[Trin_WordAddInDatabase#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDatabase#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#2)]  
  
3.  Fügen Sie der `ThisAddIn_Startup`\-Methode folgenden Code hinzu. Dadurch wird ein Hostelement generiert, das das Dokument erweitert. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-csharp[Trin_WordAddInDatabase#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDatabase#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#3)]  
  
4.  Definieren Sie am Anfang des Dokuments mehrere Bereiche. Diese Bereiche geben an, wo Text eingefügt und die Steuerelemente positioniert werden sollen.  
  
     [!code-csharp[Trin_WordAddInDatabase#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddInDatabase#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#4)]  
  
5.  Fügen Sie den zuvor definierten Bereichen die Steuerelemente der Benutzeroberfläche hinzu.  
  
     [!code-csharp[Trin_WordAddInDatabase#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddInDatabase#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#5)]  
  
6.  Binden Sie das Inhaltssteuerelement an `AdventureWorksLTDataSet`, indem Sie das <xref:System.Windows.Forms.BindingSource>\-Objekt verwenden. C\#\-Entwickler müssen zwei Ereignishandler für die <xref:Microsoft.Office.Tools.Word.Controls.Button>\-Steuerelemente hinzufügen.  
  
     [!code-csharp[Trin_WordAddInDatabase#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddInDatabase#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#6)]  
  
7.  Fügen Sie den folgenden Code hinzu, damit durch die Datenbankdatensätze navigiert werden kann.  
  
     [!code-csharp[Trin_WordAddInDatabase#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_WordAddInDatabase#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#7)]  
  
## Testen des Add\-Ins  
 Wenn Sie Word öffnen, werden im Inhaltssteuerelement Daten aus dem `AdventureWorksLTDataSet`\-Dataset angezeigt. Durchlaufen Sie die Datenbankdatensätze, indem Sie auf die Schaltflächen **Next** und **Previous** klicken.  
  
#### So testen Sie das VSTO\-Add\-In  
  
1.  Drücken Sie **F5**.  
  
     Das Inhaltssteuerelement `customerContentControl` wird erstellt und mit Daten gefüllt. Gleichzeitig werden dem Projekt ein Datasetobjekt namens `adventureWorksLTDataSet` und ein <xref:System.Windows.Forms.BindingSource>\-Objekt namens `customerBindingSource` hinzugefügt. Das <xref:Microsoft.Office.Tools.Word.ContentControl>\-Steuerelement ist an das <xref:System.Windows.Forms.BindingSource>\-Objekt gebunden, das wiederum an das Datasetobjekt gebunden ist.  
  
2.  Klicken Sie auf die Schaltflächen **Next** und **Previous**, um die Datenbankdatensätze zu durchlaufen.  
  
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
 [Gewusst wie: Auffüllen von Dokumenten mit Daten von Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Übersicht über die Verwendung lokaler Datenbankdateien in Office-Lösungen](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Herstellen einer Verbindung mit Daten in Windows Forms-Anwendungen](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Übersicht über die BindingSource-Komponente](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  