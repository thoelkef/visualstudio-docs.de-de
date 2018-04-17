---
title: 'Exemplarische Vorgehensweise: Abrufen von zwischengespeicherten Daten aus einer Arbeitsmappe auf einem Server | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e259142ce37115196c7bc0dd0390d162020c476d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-retrieving-cached-data-from-a-workbook-on-a-server"></a>Exemplarische Vorgehensweise: Abrufen zwischengespeicherter Daten aus einer Arbeitsmappe auf einem Server
  Diese exemplarische Vorgehensweise veranschaulicht, wie Daten aus einem Dataset abzurufen, die in einer Microsoft Office Excel-Arbeitsmappe zwischengespeichert ist, ohne Excel zu starten, mit der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Definieren eines Datasets, die Daten aus der AdventureWorksLT-Datenbank enthält.  
  
-   Erstellen von Instanzen des Datasets in einem Excel-Arbeitsmappenprojekt und ein Konsolenanwendungsprojekt.  
  
-   Erstellen einer <xref:Microsoft.Office.Tools.Excel.ListObject> ist gebunden an das Dataset in der Arbeitsmappe und Auffüllen der <xref:Microsoft.Office.Tools.Excel.ListObject> mit Daten, wenn die Arbeitsmappe geöffnet wird.  
  
-   Hinzufügen des Datasets in der Arbeitsmappe für den Datencache.  
  
-   Lesen von Daten aus das zwischengespeicherte Dataset in das Dataset in der Konsolenanwendung ohne Excel zu starten.  
  
 Obwohl in dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie den Code auf dem Entwicklungscomputer ausgeführt werden, kann der Code in dieser exemplarischen Vorgehensweise veranschaulichten auf einem Server verwendet werden, die über keinen Excel installiert.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Zugriff auf eine ausgeführte Instanz von Microsoft SQL Server oder Microsoft SQL Server Express, die AdventureWorksLT-Beispieldatenbank angefügt ist. Sie können die AdventureWorksLT-datenbankvon der [CodePlex-Website](http://go.microsoft.com/fwlink/?linkid=87843). Weitere Informationen zum Anhängen von Datenbanken finden Sie in den folgenden Themen:  
  
    -   Informationen zum Anfügen einer Datenbank mit SQL Server Management Studio oder SQL Server Management Studio Express finden Sie unter [Gewusst wie: Anfügen einer Datenbank (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Informationen zum Anfügen einer Datenbank über die Befehlszeile finden Sie unter [Gewusst wie: Anfügen einer Datenbankdatei an SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="creating-a-class-library-project-that-defines-a-dataset"></a>Erstellen ein Klassenbibliotheksprojekt, die ein Dataset definiert  
 Um das gleiche Dataset in einem Excel-Arbeitsmappenprojekt und einer Konsolenanwendung zu verwenden, müssen Sie das Dataset in einer separaten Assembly definieren, die beide Projekte verwiesen wird. In dieser exemplarischen Vorgehensweise definieren Sie das Dataset in einem Klassenbibliotheksprojekt aus.  
  
#### <a name="to-create-the-class-library-project"></a>Um das Klassenbibliotheksprojekt zu erstellen.  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Erweitern Sie im Vorlagenbereich **Visual C#-** oder **Visual Basic**, und klicken Sie dann auf **Windows**.  
  
4.  Wählen Sie in der Liste der Projektvorlagen **-Klassenbibliothek**.  
  
5.  In der **Namen** geben **AdventureWorksDataSet**.  
  
6.  Klicken Sie auf **Durchsuchen**, navigieren Sie zu Ihrer %UserProfile%\My Dokumente (für Windows XP und ältere Versionen) bzw. den Ordner %UserProfile%\Documents (für Windows Vista), und klicken Sie dann auf **Ordner auswählen**.  
  
7.  In der **neues Projekt** Dialogfeld sicher, dass die **Projektmappenverzeichnis erstellen** das Kontrollkästchen nicht aktiviert ist.  
  
8.  Klicken Sie auf **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **AdventureWorksDataSet** Projekt **Projektmappen-Explorer** und öffnet die **"Class1.cs"** oder **Class1.vb** -Codedatei.  
  
9. In **Projektmappen-Explorer**, mit der rechten Maustaste **"Class1.cs"** oder **Class1.vb**, und klicken Sie dann auf **löschen**. Sie können diese Datei ist nicht für diese exemplarische Vorgehensweise erforderlich.  
  
## <a name="defining-a-dataset-in-the-class-library-project"></a>Definieren eines Datasets in das Klassenbibliotheksprojekt  
 Definieren Sie ein typisiertes Dataset, das Daten aus der AdventureWorksLT-Datenbank für SQL Server 2005 enthält. Weiter unten in dieser exemplarischen Vorgehensweise werden Sie dieses Dataset aus einem Excel-Arbeitsmappenprojekt und ein Konsolenanwendungsprojekt verweisen.  
  
 Das Dataset ist ein *typisiertes Dataset* , die die Daten in der Product-Tabelle der AdventureWorksLT-Datenbank darstellt. Weitere Informationen zu typisierten "Datasets", finden Sie unter [Dataset-Tools in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
#### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>So definieren Sie ein typisiertes Dataset in das Klassenbibliotheksprojekt  
  
1.  In **Projektmappen-Explorer**, klicken Sie auf die **AdventureWorksDataSet** Projekt.  
  
2.  Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie in der Menüleiste **Ansicht**, **Weitere Fenster**und **Datenquellen**wählen.  
  
3.  Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.  
  
4.  Klicken Sie auf **Datenbank**, und klicken Sie dann auf **Weiter**.  
  
5.  Wenn Sie eine vorhandene Verbindung zur Datenbank AdventureWorksLT haben, wählen Sie diese Verbindung, und klicken Sie auf **Weiter**.  
  
     Klicken Sie andernfalls auf **Neue Verbindung**, und erstellen Sie die neue Verbindung im Dialogfeld **Verbindung hinzufügen** . Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).  
  
6.  Klicken Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** auf **Weiter**.  
  
7.  In der **Datenbankobjekte auswählen** Seite **Tabellen** , und wählen Sie **Product (SalesLT)**.  
  
8.  Klicken Sie auf **Fertig stellen**.  
  
     Die Datei "AdventureWorksLTDataSet.xsd" wird hinzugefügt, um die **AdventureWorksDataSet** Projekt. In dieser Datei sind die folgenden Elemente definiert:  
  
    -   Ein typisiertes Dataset namens `AdventureWorksLTDataSet`. Dieses Dataset stellt den Inhalt der Product-Tabelle in der AdventureWorksLT-Datenbank dar.  
  
    -   Einen TableAdapter namens `ProductTableAdapter`. Diese TableAdapter dienen zum Lesen und Schreiben von Daten in der `AdventureWorksLTDataSet`. Weitere Informationen finden Sie unter [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise verwenden Sie beide Objekte.  
  
9. In **Projektmappen-Explorer**, mit der rechten Maustaste **AdventureWorksDataSet** , und klicken Sie auf **erstellen**.  
  
     Vergewissern Sie sich, dass das Projekt ohne Fehler erstellt wurde.  
  
## <a name="creating-an-excel-workbook-project"></a>Erstellen eines Excel-Arbeitsmappenprojekts  
 Erstellen Sie ein Excel-Arbeitsmappenprojekt für die Schnittstelle, um die Daten an. Später in dieser exemplarischen Vorgehensweise erstellen Sie eine <xref:Microsoft.Office.Tools.Excel.ListObject> , die die Daten anzeigt, und fügen Sie eine Instanz des Datasets für den Datencache in der Arbeitsmappe.  
  
#### <a name="to-create-the-excel-workbook-project"></a>So erstellen die Excel-Arbeitsmappenprojekts  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **AdventureWorksDataSet** Projektmappe, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neues Projekt**.  
  
2.  Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic**und dann **Office/SharePoint**.  
  
3.  Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **Office-Add-Ins** aus.  
  
4.  Wählen Sie in der Liste der Projektvorlagen das Projekt **Excel 2010-Arbeitsmappe** oder **Excel 2013-Arbeitsmappe** aus.  
  
5.  In der **Namen** geben **AdventureWorksReport**. Ändern Sie den Speicherort nicht.  
  
6.  Klicken Sie auf **OK**.  
  
     Der **Projekt-Assistent aus Visual Studio Tools for Office** wird geöffnet.  
  
7.  Sicherstellen, dass **erstellen Sie ein neues Dokument** ausgewählt ist, und klicken Sie auf **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Öffnet die **AdventureWorksReport** Arbeitsmappe im Designer und fügt die **AdventureWorksReport** Projekt **Projektmappen-Explorer**.  
  
## <a name="adding-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Hinzufügen des Datasets zu Datenquellen in der Excel-Arbeitsmappenprojekts  
 Bevor Sie das Dataset in der Excel-Arbeitsmappe angezeigt werden können, müssen Sie zuerst das Dataset mit Datenquellen in der Excel-Arbeitsmappenprojekt hinzufügen.  
  
#### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>So fügen Sie das Dataset mit den Datenquellen in der Excel-Arbeitsmappenprojekt hinzu  
  
1.  In **Projektmappen-Explorer**, doppelklicken Sie auf **Sheet1.cs** oder **Sheet1.vb** unter der **AdventureWorksReport** Projekt.  
  
     Die Arbeitsmappe im Designer geöffnet.  
  
2.  Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.  
  
     Die **Data Source Configuration Wizard** wird geöffnet.  
  
3.  Klicken Sie auf **Objekt**, und klicken Sie dann auf **Weiter**.  
  
4.  In der **auswählen, das Objekt zu bindende** Seite, klicken Sie auf **Verweis hinzufügen**.  
  
5.  Auf der **Projekte** auf **AdventureWorksDataSet** , und klicken Sie dann auf **OK**.  
  
6.  Unter den **AdventureWorksDataSet** Namespace, der die **AdventureWorksDataSet** Assembly, klicken Sie auf **AdventureWorksLTDataSet** , und klicken Sie dann auf **Fertig stellen** .  
  
     Die **Datenquellen** Fenster geöffnet ist, und **AdventureWorksLTDataSet** wird zur Liste der Datenquellen hinzugefügt.  
  
## <a name="creating-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Erstellen ein ListObject, das mit einer Instanz des Datasets gebunden ist  
 Um das Dataset in der Arbeitsmappe anzuzeigen, erstellen eine <xref:Microsoft.Office.Tools.Excel.ListObject> , die mit einer Instanz des Datasets gebunden ist. Weitere Informationen zum Binden von Steuerelementen an Daten finden Sie unter [Binding Data to Controls in Office Solutions](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Um ein ListObject erstellen, die an eine Instanz des Datasets gebunden ist  
  
1.  In der **Datenquellen** Fenster, erweitern Sie die **AdventureWorksLTDataSet** Knoten unter **AdventureWorksDataSet**.  
  
2.  Wählen Sie die **Produkt** Knoten, klicken Sie auf den Dropdown-Pfeil, der angezeigt wird, und wählen Sie **ListObject** in der Dropdown-Liste.  
  
     Wenn der Dropdownpfeil nicht angezeigt wird, vergewissern Sie sich, dass die Arbeitsmappe im Designer geöffnet ist.  
  
3.  Ziehen Sie die **Produkt** Tabelle in die Zelle A1.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement namens `productListObject` wird erstellt, auf dem Arbeitsblatt, in die Zelle A1 ab. Gleichzeitig, ein Dataset-Objekt, das mit dem Namen `adventureWorksLTDataSet` und ein <xref:System.Windows.Forms.BindingSource> mit dem Namen `productBindingSource` werden dem Projekt hinzugefügt. Das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement ist an das <xref:System.Windows.Forms.BindingSource>-Objekt gebunden, das wiederum an das Datasetobjekt gebunden ist.  
  
## <a name="adding-the-dataset-to-the-data-cache"></a>Hinzufügen des Datasets für den Datencache  
 Um Code außerhalb der Excel-Arbeitsmappenprojekt, den Zugriff auf das Dataset in der Arbeitsmappe zu aktivieren, müssen Sie das Dataset für den Datencache hinzufügen. Weitere Informationen zu den Datencache, finden Sie unter [zwischengespeicherte Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md) und [Zwischenspeichern von Daten](../vsto/caching-data.md).  
  
#### <a name="to-add-the-dataset-to-the-data-cache"></a>So fügen Sie das Dataset für den Datencache hinzu  
  
1.  Klicken Sie im Designer auf **AdventureWorksLTDataSet**.  
  
2.  In der **Eigenschaften** legen die **Modifizierer** Eigenschaft **öffentlichen**.  
  
3.  Legen Sie die **CacheInDocument** Eigenschaft **"true"**.  
  
## <a name="initializing-the-dataset-in-the-workbook"></a>Initialisieren das Dataset in der Arbeitsmappe  
 Bevor Sie die Daten aus das zwischengespeicherte Dataset mithilfe der Konsolenanwendung abrufen können, müssen Sie zuerst das zwischengespeicherte Dataset mit Daten auffüllen.  
  
#### <a name="to-initialize-the-dataset-in-the-workbook"></a>Um das Dataset in der Arbeitsmappe zu initialisieren.  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **Sheet1.cs** oder **Sheet1.vb** Datei, und klicken Sie auf **Code anzeigen**.  
  
2.  Ersetzen Sie den `Sheet1_Startup`-Ereignishandler durch den folgenden Code. Dieser Code verwendet eine Instanz von der `ProductTableAdapter` in definierten Klasse der **AdventureWorksDataSet** Projekt, um das zwischengespeicherte Dataset mit Daten aufgefüllt werden, wenn sie derzeit leer ist.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Erstellen Sie und führen Sie die Excel-Arbeitsmappenprojekt, um sicherzustellen, dass die Kompilierung und ohne Fehler ausgeführt wird. Dieser Vorgang wird auch das zwischengespeicherte Dataset füllt und speichert die Daten in der Arbeitsmappe.  
  
#### <a name="to-build-and-run-the-project"></a>So erstellen Sie das Projekt und führen es aus  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **AdventureWorksReport** Projekts **Debuggen**, und klicken Sie dann auf **neue Instanz starten**.  
  
     Das Projekt wird erstellt, und die Arbeitsmappe in Excel geöffnet. Überprüfen Sie Folgendes:  
  
    -   Die <xref:Microsoft.Office.Tools.Excel.ListObject> mit Daten füllt.  
  
    -   Der Wert in der **ListPrice** für die erste Zeile der Spalte die <xref:Microsoft.Office.Tools.Excel.ListObject> 1431.5 ist. Weiter unten in dieser exemplarischen Vorgehensweise verwenden Sie eine Konsolenanwendung, so ändern Sie die Werte in der **ListPrice** Spalte.  
  
2.  Speichern Sie die Arbeitsmappe. Ändern Sie den Dateinamen oder den Speicherort der Arbeitsmappe nicht.  
  
3.  Schließen Sie Excel.  
  
## <a name="creating-a-console-application-project"></a>Erstellen ein Konsolenanwendungsprojekt  
 Erstellen Sie ein Konsolenanwendungsprojekt zu verwenden, um Daten in das zwischengespeicherte Dataset in der Arbeitsmappe zu ändern.  
  
#### <a name="to-create-the-console-application-project"></a>Um das Konsolenanwendungsprojekt zu erstellen.  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **AdventureWorksDataSet** Projektmappe, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neues Projekt**.  
  
2.  In der **Projekttypen** Bereich, erweitern Sie **Visual C#-** oder **Visual Basic**, und klicken Sie dann auf **Windows**.  
  
3.  In der **Vorlagen** klicken Sie im Bereich **Konsolenanwendung**.  
  
4.  In der **Namen** geben **DataReader**. Ändern Sie den Speicherort nicht.  
  
5.  Klicken Sie auf **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **DataReader** Projekt **Projektmappen-Explorer** und öffnet die **"Program.cs"** oder **"Module1.vb"** -Codedatei.  
  
## <a name="retrieving-data-from-the-cached-dataset-by-using-the-console-application"></a>Abrufen von Daten aus das zwischengespeicherte Dataset mithilfe der Konsolenanwendung  
 Verwenden der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse in der Konsolenanwendung zum Lesen der Daten in einer lokalen `AdventureWorksLTDataSet` Objekt. Um zu bestätigen, dass das lokale Dataset mit Daten aus das zwischengespeicherte Dataset initialisiert wurde, zeigt die Anwendung die Anzahl der Zeilen im lokalen Dataset an.  
  
#### <a name="to-retrieve-data-from-the-cached-dataset"></a>Zum Abrufen von Daten aus dem zwischengespeicherten dataset  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **DataReader** Projekt, und klicken Sie auf **Verweis hinzufügen**.  
  
2.  Auf der **.NET** Registerkarte, wählen Sie "Microsoft.VisualStudio.Tools.Applications.ServerDocument" hinzu.  
  
3.  Klicken Sie auf **OK**.  
  
4.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **DataReader** Projekt, und klicken Sie auf **Verweis hinzufügen**.  
  
5.  Auf der **Projekte** Registerkarte **AdventureWorksDataSet**, und klicken Sie auf **OK**.  
  
6.  Öffnen Sie die Datei "Program.cs" oder "Module1.vb" im Code-Editor.  
  
7.  Fügen Sie die folgenden **mit** (für c#) oder **Importe** (für Visual Basic) Anweisungen am Anfang der Codedatei an.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]  
  
8.  Fügen Sie der `Main` -Methode folgenden Code hinzu. Dieser Code deklariert die folgenden Objekte:  
  
    -   Eine Instanz von der `AdventureWorksLTDataSet` in definierten Typs der **AdventureWorksDataSet** Projekt.  
  
    -   Der Pfad zur Arbeitsmappe AdventureWorksReport im Ordner "Builds" von der **AdventureWorksReport** Projekt.  
  
    -   Ein <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Objekt, mit dem Datencache in der Arbeitsmappe zugreifen.  
  
        > [!NOTE]  
        >  Im folgende Code wird davon ausgegangen, dass die Arbeitsmappe mit der Erweiterung XLSX gespeichert wird. Wenn die Arbeitsmappe in Ihrem Projekt eine andere Erweiterung enthält, ändern Sie den Pfad nach Bedarf.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]  
  
9. Fügen Sie folgenden Code, der `Main` -Methode nach der im vorherigen Schritt hinzugefügten Code. Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Er verwendet die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Eigenschaft von der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse den Zugriff auf das zwischengespeicherte Dataset in der Arbeitsmappe.  
  
    -   Er liest die Daten aus dem zwischengespeicherten Dataset in das lokale Dataset.  
  
    -   Es zeigt die Anzahl der Zeilen in der lokalen Dataset aus, um sicherzustellen, dass es Daten enthält.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]  
  
10. Auf der **erstellen** Menü klicken Sie auf **DataReader erstellen**.  
  
## <a name="testing-the-project"></a>Testen des Projekts  
 Wenn Sie die Konsolenanwendung ausführen, zeigt die Anzahl der Zeilen im lokalen Dataset an.  
  
#### <a name="to-test-the-workbook"></a>So testen Sie die Arbeitsmappe  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **DataReader** Projekt, zeigen Sie auf **Debuggen**, und klicken Sie dann auf **neue Instanz starten**.  
  
     Stellen Sie sicher, dass die Anwendung meldet, dass das lokale Dataset 295 Zeilen verfügt.  
  
2.  Drücken Sie EINGABETASTE, um die Anwendung zu schließen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie können weitere Informationen zum Arbeiten mit zwischengespeicherten Daten in den folgenden Themen erfahren:  
  
-   Ändern die Daten in einem zwischengespeicherten Dataset, ohne Excel zu starten. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Ändern von zwischengespeicherten Daten in einer Arbeitsmappe auf einem Server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Einfügen von Daten in eine Arbeitsmappe auf einem Server](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)   
 [Exemplarische Vorgehensweise: Ändern zwischengespeicherter Daten in einer Arbeitsmappe auf einem Server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
 [Herstellen einer Verbindung mit Daten in Windows Forms-Anwendungen](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  