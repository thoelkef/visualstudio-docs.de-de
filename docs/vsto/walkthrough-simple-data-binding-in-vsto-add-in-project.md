---
title: 'Exemplarische Vorgehensweise: Einfache Datenbindung in VSTO-Add-in-Projekt'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6b6cf1e800c785f73ebb11e09f11b617fe42aa32
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62981080"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>Exemplarische Vorgehensweise: Einfache Datenbindung in VSTO-Add-in-Projekt

Sie können in VSTO-Add-In-Projekten Daten an Hoststeuerelemente und Windows Forms-Steuerelemente binden. Diese exemplarische Vorgehensweise veranschaulicht, wie Sie Microsoft Office Word-Dokument Steuerelemente hinzu, und Binden der Steuerelemente an Daten zur Laufzeit.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen einer <xref:Microsoft.Office.Tools.Word.ContentControl> zu einem Dokument zur Laufzeit.

- Erstellen eines <xref:System.Windows.Forms.BindingSource> -Objekts, das das Steuerelement mit einer Instanz eines Datasets verbindet

- Ermöglichen, dass Benutzer durch die Datensätze scrollen und diese im Steuerelement anzeigen können

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Vorraussetzungen

Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Zugriff auf eine aktive Instanz von SQL Server 2005 oder SQL Server 2005 Express, an die die `AdventureWorksLT` -Beispieldatenbank angefügt ist. Sie können die `AdventureWorksLT` -Datenbank von der [CodePlex-Website](http://go.microsoft.com/fwlink/?LinkId=115611). Weitere Informationen zum Anhängen von Datenbanken finden Sie in den folgenden Themen:

    - Zum Anfügen einer Datenbank mithilfe von SQL Server Management Studio oder SQL Server Management Studio Express finden Sie unter [Vorgehensweise: Anfügen einer Datenbank (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

    - Zum Anfügen einer Datenbank mithilfe der Befehlszeile finden Sie unter [Vorgehensweise: Anfügen eine Datenbankdatei an SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt

Der erste Schritt besteht im Erstellen eines VSTO-Add-In-Projekts für Word.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie mit Visual Basic oder C# ein Word-VSTO-Add-In-Projekt, das den Namen **Füllen von Dokumenten aus einer Datenbank**hat.

     Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet die *"ThisAddIn.vb"* oder *"ThisAddIn.cs"* Datei und fügt die **Füllen von Dokumenten aus einer Datenbank** Projekt **Projektmappen-Explorer** .

2. Wenn das Projekt auf die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], fügen einen Verweis auf die *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* Assembly. Dieser Verweis ist erforderlich, um später in dieser exemplarischen Vorgehensweise dem Dokument programmgesteuert Windows Forms-Steuerelemente hinzuzufügen.

## <a name="create-a-data-source"></a>Erstellen einer Datenquelle

Verwenden das Fenster **Datenquellen** , um dem Projekt ein typisiertes Dataset hinzuzufügen.

### <a name="to-add-a-typed-dataset-to-the-project"></a>So fügen Sie dem Projekt ein typisiertes Dataset hinzu

1. Wenn die **Datenquellen** Fenster ist nicht sichtbar ist, zeigen Sie es an, indem in der Menüleiste die Optionen **Ansicht** > **Other Windows**  >   **Datenquellen**.

2. Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.

3. Klicken Sie auf **Datenbank**, und klicken Sie dann auf **Weiter**.

4. Wenn eine Verbindung mit der `AdventureWorksLT` -Datenbank vorhanden ist, wählen Sie diese Verbindung aus, und klicken Sie auf **Weiter**.

    Klicken Sie andernfalls auf **Neue Verbindung**, und erstellen Sie die neue Verbindung im Dialogfeld **Verbindung hinzufügen** . Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).

5. Klicken Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** auf **Weiter**.

6. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen** , und wählen Sie **Customer (SalesLT)** aus.

7. Klicken Sie auf **Fertig stellen**.

    Die *AdventureWorksLTDataSet.xsd* Datei hinzugefügt wird **Projektmappen-Explorer**. In dieser Datei sind die folgenden Elemente definiert:

   - Ein typisiertes Dataset namens `AdventureWorksLTDataSet`. Dieses Dataset entspricht dem Inhalt der **Customer (SalesLT)** -Tabelle in der AdventureWorksLT-Datenbank.

   - Einen TableAdapter namens `CustomerTableAdapter`. Diese TableAdapter kann verwendet werden, zu lesen und Schreiben von Daten in die `AdventureWorksLTDataSet`. Weitere Informationen finden Sie unter [Übersicht über TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise verwenden Sie beide Objekte.

## <a name="create-controls-and-binding-controls-to-data"></a>Erstellen von Steuerelementen und Binden von Steuerelementen an Daten

Die Schnittstelle zum Anzeigen von Datensätzen in dieser exemplarischen Vorgehensweise ist einfach, und sie wird direkt im Dokument erstellt. In einem <xref:Microsoft.Office.Tools.Word.ContentControl> -Steuerelement wird jeweils ein einzelner Datensatz angezeigt, und mit zwei <xref:Microsoft.Office.Tools.Word.Controls.Button> -Steuerelementen können Sie nach oben und unten durch die Datensätze scrollen. Im Inhaltssteuerelement wird ein <xref:System.Windows.Forms.BindingSource> -Objekt verwendet, um eine Verbindung mit der Datenbank herzustellen.

Weitere Informationen zum Binden von Steuerelementen an Daten finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-the-interface-in-the-document"></a>So erstellen Sie die Benutzeroberfläche im Dokument

1. Deklarieren Sie in der `ThisAddIn` -Klasse die folgenden Steuerelemente, um die `Customer` -Tabelle der `AdventureWorksLTDataSet` -Datenbank anzuzeigen und sie durchlaufen zu können.

     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]

2. Fügen Sie der `ThisAddIn_Startup` -Methode den folgenden Code hinzu, um das Dataset zu initialisieren und es mit Daten aus der `AdventureWorksLTDataSet` -Datenbank zu füllen.

     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]

3. Fügen Sie der `ThisAddIn_Startup` -Methode folgenden Code hinzu. Dadurch wird ein Hostelement generiert, das das Dokument erweitert. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]

4. Definieren Sie am Anfang des Dokuments mehrere Bereiche. Diese Bereiche geben an, wo Text eingefügt und die Steuerelemente positioniert werden sollen.

     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]

5. Fügen Sie den zuvor definierten Bereichen die Steuerelemente der Benutzeroberfläche hinzu.

     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]

6. Binden Sie das Inhaltssteuerelement an `AdventureWorksLTDataSet` , indem Sie das <xref:System.Windows.Forms.BindingSource>-Objekt verwenden. C#-Entwickler müssen zwei Ereignishandler für die <xref:Microsoft.Office.Tools.Word.Controls.Button> -Steuerelemente hinzufügen.

     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]

7. Fügen Sie den folgenden Code hinzu, damit durch die Datenbankdatensätze navigiert werden kann.

     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]

## <a name="test-the-add-in"></a>Testen Sie das Add-in

Wenn Sie Word öffnen, werden im Inhaltssteuerelement Daten aus dem `AdventureWorksLTDataSet` -Dataset angezeigt. Durchlaufen Sie die Datenbankdatensätze, indem Sie auf die Schaltflächen **Next** und **Previous** klicken.

### <a name="to-test-the-vsto-add-in"></a>So testen Sie das VSTO-Add-In

1. Drücken Sie **F5**.

     Das Inhaltssteuerelement `customerContentControl` wird erstellt und mit Daten gefüllt. Gleichzeitig werden dem Projekt ein Datasetobjekt namens `adventureWorksLTDataSet` und ein <xref:System.Windows.Forms.BindingSource> -Objekt namens `customerBindingSource` hinzugefügt. Das <xref:Microsoft.Office.Tools.Word.ContentControl> -Steuerelement ist an das <xref:System.Windows.Forms.BindingSource>-Objekt gebunden, das wiederum an das Datasetobjekt gebunden ist.

2. Klicken Sie auf die Schaltflächen **Next** und **Previous** , um die Datenbankdatensätze zu durchlaufen.

## <a name="see-also"></a>Siehe auch

- [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Vorgehensweise: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Vorgehensweise: Führen Sie einen Bildlauf durch Datenbankdatensätze in einem Arbeitsblatt](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Exemplarische Vorgehensweise: Einfache Datenbindung in einem Projekt auf Dokumentebene](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Exemplarische Vorgehensweise: Komplexe Datenbindung in einem Projekt auf Dokumentebene](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Verwenden Sie lokaler Datenbankdateien in Office Solutions (Übersicht)](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)
- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Verwenden Sie lokaler Datenbankdateien in Office Solutions (Übersicht)](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource component overview (Übersicht über die BindingSource-Komponente)](/dotnet/framework/winforms/controls/bindingsource-component-overview)