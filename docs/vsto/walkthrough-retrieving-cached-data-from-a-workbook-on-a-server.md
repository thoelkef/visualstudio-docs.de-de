---
title: 'Exemplarische Vorgehensweise: Abrufen von zwischengespeicherten Daten aus einer Arbeitsmappe auf einem server'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ddf7bd222b61b3eb72a571857336c69deba6499f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421784"
---
# <a name="walkthrough-retrieve-cached-data-from-a-workbook-on-a-server"></a>Exemplarische Vorgehensweise: Abrufen von zwischengespeicherten Daten aus einer Arbeitsmappe auf einem server
  Diese exemplarische Vorgehensweise veranschaulicht, wie Sie Daten aus einem Dataset abzurufen, die in einer Microsoft Office Excel-Arbeitsmappe zwischengespeichert werden, ohne Excel zu starten mithilfe der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Definieren eines Datasets, die Daten aus der *AdventureWorksLT* Datenbank.

- Erstellen Instanzen des Datasets in ein Excel-Workbook-Projekt und ein Konsolenanwendungsprojekt.

- Erstellen einer <xref:Microsoft.Office.Tools.Excel.ListObject> ist gebunden an das Dataset in der Arbeitsmappe und Auffüllen der <xref:Microsoft.Office.Tools.Excel.ListObject> mit Daten, wenn die Arbeitsmappe geöffnet wird.

- Hinzufügen des Datasets in der Arbeitsmappe, das dem Datencache.

- Lesen von Daten aus das zwischengespeicherte Dataset in das Dataset in der Konsolenanwendung, ohne Excel zu starten.

  Obwohl in dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie den Code auf Ihrem Entwicklungscomputer ausgeführt werden, kann von in dieser exemplarischen Vorgehensweise gezeigten Code auf einem Server verwendet werden, die keine für Excel installiert.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Zugriff auf eine ausgeführte Instanz von Microsoft SQL Server oder Microsoft SQL Server Express, die die Beispieldatenbank "AdventureWorksLT" angefügt ist. Sie können die AdventureWorksLT-datenbankvon der [CodePlex-Website](http://go.microsoft.com/fwlink/?linkid=87843). Weitere Informationen zum Anhängen von Datenbanken finden Sie in den folgenden Themen:

    - Zum Anfügen einer Datenbank mithilfe von SQL Server Management Studio oder SQL Server Management Studio Express finden Sie unter [Vorgehensweise: Anfügen einer Datenbank (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

    - Zum Anfügen einer Datenbank mithilfe der Befehlszeile finden Sie unter [Vorgehensweise: Anfügen eine Datenbankdatei an SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Erstellen Sie ein Klassenbibliotheksprojekt, das ein Dataset definiert.
 Um dasselbe Dataset in ein Excel-Workbook-Projekt und eine Konsolenanwendung zu verwenden, müssen Sie das Dataset in einer separaten Assembly definieren, die beide Projekte verwiesen wird. In dieser exemplarischen Vorgehensweise definieren Sie das Dataset in ein Klassenbibliotheksprojekt.

### <a name="create-the-class-library-project"></a>Erstellen des Klassenbibliotheksprojekts

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

3. Erweitern Sie im Vorlagenbereich **Visual C#-** oder **Visual Basic**, und klicken Sie dann auf **Windows**.

4. Wählen Sie in der Liste der Projektvorlagen das Projekt **Klassenbibliothek**.

5. In der **Namen** geben **AdventureWorksDataSet**.

6. Klicken Sie auf **Durchsuchen**, navigieren Sie zu Ihrem *%UserProfile%\My Dokumente* (für Windows XP und früher) oder *%UserProfile%\Documents* (für Windows Vista), und klicken Sie dann auf **Wählen Sie Ordner**.

7. In der **neues Projekt** Dialogfeld sicher, dass die **Projektmappenverzeichnis erstellen** das Kontrollkästchen nicht aktiviert ist.

8. Klicken Sie auf **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **AdventureWorksDataSet** Projekt **Projektmappen-Explorer** und öffnet die *"Class1.cs"* oder *"Class1.vb"* Codedatei.

9. In **Projektmappen-Explorer**, mit der rechten Maustaste *"Class1.cs"* oder *"Class1.vb"*, und klicken Sie dann auf **löschen**. Sie können diese Datei ist nicht in dieser exemplarischen Vorgehensweise erforderlich.

## <a name="define-a-dataset-in-the-class-library-project"></a>Definieren Sie ein Dataset in das Klassenbibliotheksprojekt hinzu
 Definieren Sie ein typisiertes Dataset, das Daten aus der AdventureWorksLT-Datenbank für SQL Server 2005 enthält. Weiter unten in dieser exemplarischen Vorgehensweise werden Sie dieses Dataset aus einer Excel-Workbook-Projekt und ein Konsolenanwendungsprojekt verweisen.

 Das Dataset ist eine *typisiertes Dataset* , die die Daten in der Product-Tabelle der AdventureWorksLT-Datenbank darstellt. Weitere Informationen zu typisierten "Datasets", finden Sie unter [datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="define-a-typed-dataset-in-the-class-library-project"></a>Definieren Sie ein typisiertes Dataset in das Klassenbibliotheksprojekt hinzu

1. In **Projektmappen-Explorer**, klicken Sie auf die **AdventureWorksDataSet** Projekt.

2. Wenn die **Datenquellen** Fenster ist nicht sichtbar ist, zeigen Sie es an, indem in der Menüleiste die Optionen **Ansicht** > **Other Windows**  >   **Datenquellen**.

3. Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.

4. Klicken Sie auf **Datenbank**, und klicken Sie dann auf **Weiter**.

5. Wenn Sie eine vorhandene Verbindung mit der AdventureWorksLT-Datenbank verfügen, wählen Sie diese Verbindung, und klicken Sie auf **Weiter**.

    Klicken Sie andernfalls auf **Neue Verbindung**, und erstellen Sie die neue Verbindung im Dialogfeld **Verbindung hinzufügen** . Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).

6. Klicken Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** auf **Weiter**.

7. In der **Datenbankobjekte auswählen** Seite **Tabellen** , und wählen Sie **Product (SalesLT)**.

8. Klicken Sie auf **Fertig stellen**.

    Die *AdventureWorksLTDataSet.xsd* Datei wird hinzugefügt, um die **AdventureWorksDataSet** Projekt. In dieser Datei sind die folgenden Elemente definiert:

   - Ein typisiertes Dataset namens `AdventureWorksLTDataSet`. Dieses Dataset stellt die Inhalte der Product-Tabelle in der AdventureWorksLT-Datenbank dar.

   - Einen TableAdapter namens `ProductTableAdapter`. Diese TableAdapter kann verwendet werden, zu lesen und Schreiben von Daten in die `AdventureWorksLTDataSet`. Weitere Informationen finden Sie unter [Übersicht über TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise verwenden Sie beide Objekte.

9. In **Projektmappen-Explorer**, mit der rechten Maustaste **AdventureWorksDataSet** , und klicken Sie auf **erstellen**.

     Vergewissern Sie sich, dass das Projekt ohne Fehler erstellt wurde.

## <a name="create-an-excel-workbook-project"></a>Erstellen Sie ein Excel-Workbook-Projekt
 Erstellen Sie ein Excel-Workbook-Projekt für die Schnittstelle für die Daten an. Weiter unten in dieser exemplarischen Vorgehensweise erstellen Sie eine <xref:Microsoft.Office.Tools.Excel.ListObject> , die die Daten anzeigt, und fügen Sie eine Instanz des Datasets, das dem Datencache in der Arbeitsmappe.

### <a name="create-the-excel-workbook-project"></a>Erstellen der Excel-Workbook-Projekt

1. In **Projektmappen-Explorer**, mit der rechten Maustaste die **AdventureWorksDataSet** Projektmappe, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neues Projekt**.

2. Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic**und dann **Office/SharePoint**.

3. Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **Office-Add-Ins** aus.

4. Wählen Sie in der Liste der Projektvorlagen das Projekt **Excel 2010-Arbeitsmappe** oder **Excel 2013-Arbeitsmappe** aus.

5. In der **Namen** geben **AdventureWorksReport**. Ändern Sie den Speicherort nicht.

6. Klicken Sie auf **OK**.

     Der **Projekt-Assistent aus Visual Studio Tools for Office** wird geöffnet.

7. Sicherstellen, dass **ein neues Dokument erstellen** ausgewählt ist, und klicken Sie auf **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Öffnet die **AdventureWorksReport** Arbeitsmappe im Designer und fügt die **AdventureWorksReport** Projekt **Projektmappen-Explorer**.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Fügen Sie das Dataset zu Datenquellen in der Excel-Workbook-Projekt
 Bevor Sie das Dataset in der Excel-Arbeitsmappe anzeigen können, müssen Sie zunächst das Dataset zu Datenquellen in der Excel-Workbook-Projekt hinzufügen.

1. In **Projektmappen-Explorer**, doppelklicken Sie auf *Sheet1.cs* oder *Sheet1.vb* unter der **AdventureWorksReport** Projekt.

     Die Arbeitsmappe im Designer wird geöffnet.

2. Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.

     Der **Assistent zum Konfigurieren von Datenquellen** wird geöffnet.

3. Klicken Sie auf **Objekt**, und klicken Sie dann auf **Weiter**.

4. In der **auswählen, das Objekt an das Bindung hergestellt** Seite, klicken Sie auf **Verweis hinzufügen**.

5. Auf der **Projekte** auf **AdventureWorksDataSet** , und klicken Sie dann auf **OK**.

6. Unter den **AdventureWorksDataSet** Namespace, der die **AdventureWorksDataSet** Assembly klicken Sie auf **AdventureWorksLTDataSet** , und klicken Sie dann auf **Fertig stellen** .

     Die **Datenquellen** Fenster geöffnet wird, und **AdventureWorksLTDataSet** wird die Liste der Datenquellen hinzugefügt.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Erstellen Sie ein ListObject, die mit einer Instanz des Datasets gebunden ist
 Um das Dataset in der Arbeitsmappe anzuzeigen, erstellen eine <xref:Microsoft.Office.Tools.Excel.ListObject> , die mit einer Instanz des Datasets gebunden ist. Weitere Informationen zum Binden von Steuerelementen an Daten finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).

1. In der **Datenquellen** Fenster, erweitern Sie die **AdventureWorksLTDataSet** Knoten unter **AdventureWorksDataSet**.

2. Wählen Sie die **Produkt** Knoten, klicken Sie auf den Dropdown-Pfeil, der angezeigt wird, und wählen Sie **ListObject** in der Dropdown-Liste.

     Wenn der Dropdownpfeil nicht angezeigt wird, vergewissern Sie sich, dass die Arbeitsmappe im Designer geöffnet.

3. Ziehen Sie die **Produkt** Tabelle in Zelle A1.

     Ein <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement mit dem Namen `productListObject` wird erstellt, auf dem Arbeitsblatt, in die Zelle A1 ab. Gleichzeitig werden dem Projekt ein Datasetobjekt namens `adventureWorksLTDataSet` und ein <xref:System.Windows.Forms.BindingSource> -Objekt namens `productBindingSource` hinzugefügt. Das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement ist an das <xref:System.Windows.Forms.BindingSource>-Objekt gebunden, das wiederum an das Datasetobjekt gebunden ist.

## <a name="add-the-dataset-to-the-data-cache"></a>Fügen Sie das Dataset, das dem Datencache
 Um Code außerhalb der Excel-Workbook-Projekt, den Zugriff auf das Dataset in der Arbeitsmappe zu aktivieren, müssen Sie das Dataset, das dem Datencache hinzufügen. Weitere Informationen zu den Datencache, finden Sie unter [zwischengespeicherten Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md) und [Zwischenspeichern von Daten](../vsto/caching-data.md).

1. Klicken Sie im Designer auf **AdventureWorksLTDataSet**.

2. In der **Eigenschaften** legen die **Modifizierer** Eigenschaft **öffentliche**.

3. Legen Sie die **CacheInDocument** Eigenschaft **"true"**.

## <a name="initialize-the-dataset-in-the-workbook"></a>Initialisieren Sie das Dataset in der Arbeitsmappe
 Bevor Sie die Daten aus das zwischengespeicherte Dataset mithilfe der Konsolenanwendung abrufen können, müssen Sie zuerst das zwischengespeicherte Dataset mit Daten auffüllen.

1. In **Projektmappen-Explorer**, mit der rechten Maustaste die *Sheet1.cs* oder *Sheet1.vb* Datei, und klicken Sie auf **Ansichtscode**.

2. Ersetzen Sie den `Sheet1_Startup` -Ereignishandler durch den folgenden Code. Dieser Code wird eine Instanz der dem `ProductTableAdapter` -Klasse, die in definiert ist die **AdventureWorksDataSet** Projekt, um das zwischengespeicherte Dataset mit Daten auszufüllen, wenn sie derzeit leer ist.

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>Checkpoint
 Erstellen Sie und führen Sie die Excel-Workbook-Projekt, um sicherzustellen, dass er kompiliert und ohne Fehler ausgeführt wird. Dieser Vorgang wird auch das zwischengespeicherte Dataset füllt und speichert die Daten in der Arbeitsmappe.

### <a name="build-and-run-the-project"></a>Erstellen und Ausführen des Projekts

1. In **Projektmappen-Explorer**, mit der rechten Maustaste die **AdventureWorksReport** Projekts **Debuggen**, und klicken Sie dann auf **neue Instanz starten**.

     Das Projekt erstellt wird, und die Arbeitsmappe in Excel geöffnet. Überprüfen Sie Folgendes:

    - Die <xref:Microsoft.Office.Tools.Excel.ListObject> mit Daten füllt.

    - Der Wert in der **ListPrice** Spalte für die erste Zeile der <xref:Microsoft.Office.Tools.Excel.ListObject> ist 1431.5. Später in dieser exemplarischen Vorgehensweise verwenden Sie eine Konsolenanwendung, so ändern Sie die Werte in der **ListPrice** Spalte.

2. Speichern Sie die Arbeitsmappe. Ändern Sie den Dateinamen oder den Speicherort der Arbeitsmappe nicht.

3. Schließen Sie Excel.

## <a name="create-a-console-application-project"></a>Erstellen Sie ein Konsolenanwendungsprojekt
 Erstellen Sie ein Konsolenanwendungsprojekt zu verwenden, um Daten in das zwischengespeicherte Dataset in der Arbeitsmappe zu ändern.

1. In **Projektmappen-Explorer**, mit der rechten Maustaste die **AdventureWorksDataSet** Projektmappe, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neues Projekt**.

2. In der **Projekttypen** Bereich, erweitern Sie **Visual C#-** oder **Visual Basic**, und klicken Sie dann auf **Windows**.

3. In der **Vorlagen** wählen Sie im Bereich **Konsolenanwendung**.

4. In der **Namen** geben **DataReader**. Ändern Sie den Speicherort nicht.

5. Klicken Sie auf **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **DataReader** Projekt **Projektmappen-Explorer** und öffnet die *"Program.cs"* oder *"Module1.vb"* Codedatei.

## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>Abrufen von Daten aus das zwischengespeicherte Dataset mithilfe der Konsolenanwendung
 Verwenden der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse in der Konsolenanwendung zum Lesen der Daten in eine lokale `AdventureWorksLTDataSet` Objekt. Um zu bestätigen, dass die lokale Dataset mit Daten aus das zwischengespeicherte Dataset initialisiert wurde, zeigt die Anwendung die Anzahl der Zeilen in der lokalen Dataset an.

### <a name="retrieve-data-from-the-cached-dataset"></a>Abrufen von Daten aus das zwischengespeicherte dataset

1. In **Projektmappen-Explorer**, mit der rechten Maustaste die **DataReader** Projekt, und klicken Sie auf **Verweis hinzufügen**.

2. Auf der **.NET** Registerkarte **Microsoft.VisualStudio.Tools.Applications.ServerDocument**.

3. Klicken Sie auf **OK**.

4. In **Projektmappen-Explorer**, mit der rechten Maustaste die **DataReader** Projekt, und klicken Sie auf **Verweis hinzufügen**.

5. Auf der **Projekte** Registerkarte **AdventureWorksDataSet**, und klicken Sie auf **OK**.

6. Öffnen der *"Program.cs"* oder *"Module1.vb"* Datei im Code-Editor.

7. Fügen Sie die folgenden **mit** (für c#) oder **Importe** (für Visual Basic)-Anweisung am Anfang der Codedatei zu verlassen.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. Fügen Sie der `Main` -Methode folgenden Code hinzu. Dieser Code deklariert die folgenden Objekte:

   - Eine Instanz von der `AdventureWorksLTDataSet` in definierten Typs der **AdventureWorksDataSet** Projekt.

   - Der Pfad zur Arbeitsmappe AdventureWorksReport im Ordner für Builds von der **AdventureWorksReport** Projekt.

   - Ein <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Objekt, das Zugriff auf den Datencache in der Arbeitsmappe verwendet.

     > [!NOTE]
     > Der folgende Code wird davon ausgegangen, dass die Arbeitsmappe gespeichert wird, mit der *XLSX* Erweiterung. Wenn die Arbeitsmappe in Ihrem Projekt eine andere Erweiterung enthält, ändern Sie den Pfad nach Bedarf.

     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]

9. Fügen Sie den folgenden Code der `Main` Methode, nach dem Code, die Sie im vorherigen Schritt hinzugefügt haben. Mit diesem Code werden die folgenden Aufgaben ausgeführt:

   - Er verwendet den <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Eigenschaft der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse den Zugriff auf das zwischengespeicherte Dataset in der Arbeitsmappe.

   - Es liest die Daten aus das zwischengespeicherte Dataset aus, in das lokale Dataset.

   - Es zeigt die Anzahl der Zeilen in der lokalen Dataset aus, um sicherzustellen, dass sie Daten enthält.

     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]

10. Auf der **erstellen** Menü klicken Sie auf **DataReader erstellen**.

## <a name="test-the-project"></a>Testen Sie das Projekt
 Wenn Sie die Konsolenanwendung ausführen, wird die Anzahl der Zeilen im lokalen Dataset angezeigt.

### <a name="test-the-workbook"></a>Testen Sie die Arbeitsmappe

1. In **Projektmappen-Explorer**, mit der rechten Maustaste die **DataReader** Projekt, zeigen Sie auf **Debuggen**, und klicken Sie dann auf **neue Instanz starten**.

     Stellen Sie sicher, dass die Anwendung meldet, dass die lokale Dataset 295 Zeilen verfügt.

2. Drücken Sie **EINGABETASTE** zum Schließen der Anwendung.

## <a name="next-steps"></a>Nächste Schritte
 Erfahren Sie mehr über das Arbeiten mit zwischengespeicherten Daten in den folgenden Themen:

- Ändern die Daten in ein zwischengespeichertes Dataset, ohne Excel zu starten. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Ändern Sie die zwischengespeicherte Daten in einer Arbeitsmappe auf einem Server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Einfügen von Daten in einer Arbeitsmappe auf einem server](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
- [Exemplarische Vorgehensweise: Ändern Sie die zwischengespeicherte Daten in einer Arbeitsmappe auf einem server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
