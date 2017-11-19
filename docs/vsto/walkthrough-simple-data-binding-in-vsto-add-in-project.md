---
title: 'Exemplarische Vorgehensweise: Einfache Datenbindung in einem VSTO-add-in-Projekt | Microsoft Docs'
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
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
ms.assetid: b248d194-a8b1-4f87-94c4-24e940eea1fd
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fe1626a818a6442e56e8934b142a31b65f83c0a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>Exemplarische Vorgehensweise: Einfache Datenbindung in einem VSTO-Add-In-Projek
  Sie können in VSTO-Add-In-Projekten Daten an Hoststeuerelemente und Windows Forms-Steuerelemente binden. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie einem Microsoft Office Word-Dokument zur Laufzeit Steuerelemente hinzugefügt und diese Steuerelemente an Daten gebunden werden.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen eines <xref:Microsoft.Office.Tools.Word.ContentControl> -Steuerelements zu einem Dokument zur Laufzeit  
  
-   Erstellen eines <xref:System.Windows.Forms.BindingSource> -Objekts, das das Steuerelement mit einer Instanz eines Datasets verbindet  
  
-   Ermöglichen, dass Benutzer durch die Datensätze scrollen und diese im Steuerelement anzeigen können  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Zugriff auf eine aktive Instanz von SQL Server 2005 oder SQL Server 2005 Express, an die die `AdventureWorksLT` -Beispieldatenbank angefügt ist. Sie können die `AdventureWorksLT` -Datenbank von der [CodePlex-Website](http://go.microsoft.com/fwlink/?LinkId=115611)herunterladen. Weitere Informationen zum Anhängen von Datenbanken finden Sie in den folgenden Themen:  
  
    -   Informationen zum Anfügen einer Datenbank mit SQL Server Management Studio oder SQL Server Management Studio Express finden Sie unter [Gewusst wie: Anfügen einer Datenbank (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Informationen zum Anfügen einer Datenbank über die Befehlszeile finden Sie unter [Gewusst wie: Anfügen einer Datenbankdatei an SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="creating-a-new-project"></a>Erstellen eines neuen Projekts  
 Der erste Schritt besteht im Erstellen eines VSTO-Add-In-Projekts für Word.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie mit Visual Basic oder C# ein Word-VSTO-Add-In-Projekt, das den Namen **Füllen von Dokumenten aus einer Datenbank**hat.  
  
     Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die Datei „ThisAddIn.vb“ oder „ThisAddIn.cs“ und fügt dem **Projektmappen-Explorer** das Projekt **Füllen von Dokumenten aus einer Datenbank**hinzu.  
  
2.  Wenn das Projekt für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]vorgesehen ist, fügen Sie einen Verweis auf die Assembly „Microsoft.Office.Tools.Word.v4.0.Utilities.dll“ hinzu. Dieser Verweis ist erforderlich, um später in dieser exemplarischen Vorgehensweise dem Dokument programmgesteuert Windows Forms-Steuerelemente hinzuzufügen.  
  
## <a name="creating-a-data-source"></a>Erstellen einer Datenquelle  
 Verwenden das Fenster **Datenquellen** , um dem Projekt ein typisiertes Dataset hinzuzufügen.  
  
#### <a name="to-add-a-typed-dataset-to-the-project"></a>So fügen Sie dem Projekt ein typisiertes Dataset hinzu  
  
1.  Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie in der Menüleiste **Ansicht**, **Weitere Fenster**und **Datenquellen**wählen.  
  
2.  Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.  
  
3.  Klicken Sie auf **Datenbank**, und klicken Sie dann auf **Weiter**.  
  
4.  Wenn eine Verbindung mit der `AdventureWorksLT` -Datenbank vorhanden ist, wählen Sie diese Verbindung aus, und klicken Sie auf **Weiter**.  
  
     Klicken Sie andernfalls auf **Neue Verbindung**, und erstellen Sie die neue Verbindung im Dialogfeld **Verbindung hinzufügen** . Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).  
  
5.  Klicken Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** auf **Weiter**.  
  
6.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen** , und wählen Sie **Customer (SalesLT)**aus.  
  
7.  Klicken Sie auf **Fertig stellen**.  
  
     Öffnen Sie im **Projektmappen-Explorer**die Datei „AdventureWorksLTDataSet.xsd“. In dieser Datei sind die folgenden Elemente definiert:  
  
    -   Ein typisiertes Dataset namens `AdventureWorksLTDataSet`. Dieses Dataset entspricht dem Inhalt der **Customer (SalesLT)** -Tabelle in der AdventureWorksLT-Datenbank.  
  
    -   Einen TableAdapter namens `CustomerTableAdapter`. Diese TableAdapter dienen zum Lesen und Schreiben von Daten in der `AdventureWorksLTDataSet`. Weitere Informationen finden Sie unter [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise verwenden Sie beide Objekte.  
  
## <a name="creating-controls-and-binding-controls-to-data"></a>Erstellen von Steuerelementen und Binden von Steuerelementen an Daten  
 Die Benutzeroberfläche zum Anzeigen von Datensätzen hat in dieser exemplarischen Vorgehensweise einen sehr begrenzten Umfang, und sie wird direkt im Dokument erstellt. In einem <xref:Microsoft.Office.Tools.Word.ContentControl> -Steuerelement wird jeweils ein einzelner Datensatz angezeigt, und mit zwei <xref:Microsoft.Office.Tools.Word.Controls.Button> -Steuerelementen können Sie nach oben und unten durch die Datensätze scrollen. Im Inhaltssteuerelement wird ein <xref:System.Windows.Forms.BindingSource> -Objekt verwendet, um eine Verbindung mit der Datenbank herzustellen.  
  
 Weitere Informationen zum Binden von Steuerelementen an Daten finden Sie unter [Binding Data to Controls in Office Solutions](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### <a name="to-create-the-interface-in-the-document"></a>So erstellen Sie die Benutzeroberfläche im Dokument  
  
1.  Deklarieren Sie in der `ThisAddIn` -Klasse die folgenden Steuerelemente, um die `Customer` -Tabelle der `AdventureWorksLTDataSet` -Datenbank anzuzeigen und sie durchlaufen zu können.  
  
     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]  
  
2.  Fügen Sie der `ThisAddIn_Startup` -Methode den folgenden Code hinzu, um das Dataset zu initialisieren und es mit Daten aus der `AdventureWorksLTDataSet` -Datenbank zu füllen.  
  
     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]  
  
3.  Fügen Sie der `ThisAddIn_Startup` -Methode folgenden Code hinzu. Dadurch wird ein Hostelement generiert, das das Dokument erweitert. Weitere Informationen finden Sie unter [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]  
  
4.  Definieren Sie am Anfang des Dokuments mehrere Bereiche. Diese Bereiche geben an, wo Text eingefügt und die Steuerelemente positioniert werden sollen.  
  
     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]  
  
5.  Fügen Sie den zuvor definierten Bereichen die Steuerelemente der Benutzeroberfläche hinzu.  
  
     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]  
  
6.  Binden Sie das Inhaltssteuerelement an `AdventureWorksLTDataSet` , indem Sie das <xref:System.Windows.Forms.BindingSource>-Objekt verwenden. C#-Entwickler müssen zwei Ereignishandler für die <xref:Microsoft.Office.Tools.Word.Controls.Button> -Steuerelemente hinzufügen.  
  
     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]  
  
7.  Fügen Sie den folgenden Code hinzu, damit durch die Datenbankdatensätze navigiert werden kann.  
  
     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]  
  
## <a name="testing-the-add-in"></a>Testen des Add-Ins  
 Wenn Sie Word öffnen, werden im Inhaltssteuerelement Daten aus dem `AdventureWorksLTDataSet` -Dataset angezeigt. Durchlaufen Sie die Datenbankdatensätze, indem Sie auf die Schaltflächen **Next** und **Previous** klicken.  
  
#### <a name="to-test-the-vsto-add-in"></a>So testen Sie das VSTO-Add-In  
  
1.  Drücken Sie **F5**.  
  
     Das Inhaltssteuerelement `customerContentControl` wird erstellt und mit Daten gefüllt. Gleichzeitig werden dem Projekt ein Datasetobjekt namens `adventureWorksLTDataSet` und ein <xref:System.Windows.Forms.BindingSource> -Objekt namens `customerBindingSource` hinzugefügt. Das <xref:Microsoft.Office.Tools.Word.ContentControl> -Steuerelement ist an das <xref:System.Windows.Forms.BindingSource>-Objekt gebunden, das wiederum an das Datasetobjekt gebunden ist.  
  
2.  Klicken Sie auf die Schaltflächen **Next** und **Previous** , um die Datenbankdatensätze zu durchlaufen.  
  
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
 [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Verwendung lokaler Datenbankdateien in Office-Projektmappen (Übersicht)](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Herstellen einer Verbindung mit Daten in Windows Forms-Anwendungen](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Übersicht über die BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  