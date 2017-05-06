---
title: "Exemplarische Vorgehensweise: Einf&#252;gen von Daten in eine Arbeitsmappe auf einem Server"
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
  - "Daten [Office-Entwicklung in Visual Studio], Zugriff auf dem Server"
  - "Datasets [Office-Entwicklung in Visual Studio], Zugriff auf dem Server"
  - "Dokumente [Office-Entwicklung in Visual Studio], Serverseitiger Datenzugriff"
  - "Serverseitiger Datenzugriff [Office-Entwicklung in Visual Studio]"
  - "Arbeitsmappen [Office-Entwicklung in Visual Studio], Einfügen von Daten"
ms.assetid: e6481902-781c-4666-bc18-4d69368c9bb3
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Exemplarische Vorgehensweise: Einf&#252;gen von Daten in eine Arbeitsmappe auf einem Server
  Diese exemplarische Vorgehensweise veranschaulicht, wie Sie mit der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>\-Klasse Daten in ein Dataset im Cache einer Microsoft Office Excel\-Arbeitsmappe einfügen können, ohne Excel zu starten.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Definieren eines DataSets, das Daten aus der AdventureWorksLT\-Datenbank enthält  
  
-   Erstellen von Datasetinstanzen in einem Excel\-Arbeitsmappenprojekt und einem Konsolenanwendungsprojekt  
  
-   Erstellen eines <xref:Microsoft.Office.Tools.Excel.ListObject>, das an das Dataset in der Arbeitsmappe gebunden ist  
  
-   Hinzufügen des Datasets in der Arbeitsmappe zum Datencache  
  
-   Einfügen von Daten in das zwischengespeicherte Dataset durch Ausführen von Code in der Konsolenanwendung ohne Starten von Excel  
  
 Bei dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie den Code auf Ihrem Entwicklungscomputer ausführen. Sie können den hier demonstrierten Code jedoch auch auf einem Server verwenden, auf dem Excel nicht installiert ist.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die von Ihnen verwendete Visual Studio\-Edition und die Einstellungen legen diese Elemente fest.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Zugriff auf eine gegenwärtig ausgeführte Instanz von Microsoft SQL Server oder Microsoft SQL Server Express, die mit der AdventureWorksLT\-Beispieldatenbank verknüpft ist  Sie können die AdventureWorksLT\-Datenbank von der [CodePlex\-Website](http://go.microsoft.com/fwlink/?linkid=87843) herunterladen.  Weitere Informationen zum Anhängen von Datenbanken finden Sie unter den folgenden Themen:  
  
    -   Informationen zum Anfügen einer Datenbank mit SQL Server Management Studio oder SQL Server Management Studio Express finden Sie unter [Gewusst wie: Anfügen einer Datenbank \(SQL Server Management Studio\)](http://msdn.microsoft.com/de-de/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Informationen zum Anfügen einer Datenbank über die Befehlszeile finden Sie unter [Gewusst wie: Anfügen einer Datenbankdatei an SQL Server Express](http://msdn.microsoft.com/de-de/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## Erstellen eines Klassenbibliotheksprojekts zur Definition eines Datasets  
 Um dasselbe Dataset in einem Excel\-Arbeitsmappenprojekt und einem Konsolenanwendungsprojekt verwenden zu können, müssen Sie es in einer separaten Assembly definieren, auf die beide Projekte verweisen.  Definieren Sie für diese exemplarische Vorgehensweise das Dataset in einem Klassenbibliotheksprojekt.  
  
#### So erstellen Sie ein Klassenbibliotheks\-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Erweitern Sie im Vorlagenbereich **Visual C\#** oder **Visual Basic**, und klicken Sie dann auf **Windows**.  
  
4.  Wählen Sie in der Liste der Projektvorlagen **Klassenbibliothek** aus.  
  
5.  Geben Sie im Feld **Name** Folgendes ein: **AdventureWorksDataSet**.  
  
6.  Klicken Sie auf **Durchsuchen**, navigieren Sie zum Ordner %UserProfile%\\Eigene Dateien \(Windows XP und ältere Versionen\) bzw. %UserProfile%\\Dokumente \(Windows Vista\), und klicken Sie dann auf **Ordner auswählen**.  
  
7.  Im Dialogfeld **Neues Projekt** muss das Kontrollkästchen **Projektmappenverzeichnis erstellen** deaktiviert sein.  
  
8.  Klicken Sie auf **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **AdventureWorksDataSet** dem **Projektmappen\-Explorer** hinzu und öffnet die Codedatei **Class1.cs** oder **Class1.vb**.  
  
9. Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **Class1.cs** bzw. auf **Class1.vb**, und klicken Sie dann auf **Löschen**.  Diese Datei wird für diese exemplarische Vorgehensweise nicht benötigt.  
  
## Definieren eines Datasets im Klassenbibliotheksprojekt  
 Definieren Sie ein typisiertes DataSet, das Daten aus der AdventureWorksLT\-Datenbank für SQL Server 2005 enthält.  Zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise verweisen Sie von einem Excel\-Arbeitsmappenprojekt und einem Konsolenanwendungsprojekt auf dieses DataSet.  
  
 Das Dataset ist ein *typisiertes Dataset*, das die Daten in der Product\-Tabelle der AdventureWorksLT\-Datenbank darstellt.  Weitere Informationen zu typisierten Datasets finden Sie unter [Arbeiten mit Datasets in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### So definieren Sie ein typisiertes Dataset im Klassenbibliotheksprojekt  
  
1.  Klicken Sie im **Projektmappen\-Explorer** auf das Projekt **AdventureWorksDataSet**.  
  
2.  Wenn das **Datenquellen** nicht sichtbar ist, zeigen Sie sie durch, auf der Menüleiste auf und **Ansicht** auswählen, **Weitere Fenster**, **Datenquellen**.  
  
3.  Wählen Sie **Neue Datenquelle hinzufügen**, um **Assistent zum Konfigurieren von Datenquellen** zu starten.  
  
4.  Klicken Sie auf **Datenbank** und anschließend auf **Weiter**.  
  
5.  Wenn eine Verbindung mit der AdventureWorksLT\-Datenbank vorhanden ist, wählen Sie diese Verbindung aus, und klicken Sie auf **Weiter**.  
  
     Klicken Sie andernfalls auf **Neue Verbindung**, und erstellen Sie die neue Verbindung im Dialogfeld **Verbindung hinzufügen**.  Weitere Informationen hierzu finden Sie unter [How to: Connect to Data in a Database](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md).  
  
6.  Klicken Sie auf der Seite **Save the Connection String to the Application Configuration File** auf **Next**.  
  
7.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**, und wählen Sie **Product \(SalesLT\)**.  
  
8.  Klicken Sie auf **Fertig stellen**.  
  
     Die Datei **AdventureWorksLTDataSet.xsd** wird dem **AdventureWorksDataSet**\-Projekt hinzugefügt.  Diese Datei definiert die folgenden Elemente:  
  
    -   Ein typisiertes Dataset mit dem Namen `AdventureWorksLTDataSet`.  Dieses Dataset stellt den Inhalt der Product\-Tabelle in der AdventureWorksLT\-Datenbank dar.  
  
    -   Ein TableAdapter mit dem Namen `ProductTableAdapter`.  Dieser TableAdapter kann zum Lesen von Daten aus und zum Schreiben von Daten in `AdventureWorksLTDataSet` verwendet werden.  Weitere Informationen finden Sie unter [Übersicht über TableAdapters](/visual-studio/data-tools/tableadapter-overview).  
  
     Zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise verwenden Sie beide Objekte.  
  
9. Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **AdventureWorksDataSet**, und klicken Sie dann auf **Erstellen**.  
  
     Überprüfen Sie, ob sich das Projekt fehlerfrei erstellen lässt.  
  
## Erstellen eines Excel\-Arbeitsmappenprojekts  
 Erstellen Sie ein Excel\-Arbeitsmappenprojekt für die Datenschnittstelle.  Zu einem späteren Zeitpunkt der exemplarischen Vorgehensweise erstellen Sie ein <xref:Microsoft.Office.Tools.Excel.ListObject> zur Anzeige der Daten und fügen dem Datencache der Arbeitsmappe eine Instanz des Datasets hinzu.  
  
#### So erstellen Sie das Excel\-Arbeitsmappenprojekt  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **AdventureWorksDataSet**, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt**.  
  
2.  Erweitern Sie im Vorlagenbereich den **Visual C\#** oder  **Visual Basic**, und erweitern Sie dann **Office\/SharePoint**.  
  
3.  unter dem erweiterten Knoten **Office\/SharePoint** wählen Sie den Knoten **Office\-Add\-Ins** aus.  
  
4.  In der Liste der Projektvorlagen, aktivieren Sie das **Excel 2010\-Arbeitsmappe** oder **Excel 2013\-Arbeitsmappe** Projekt aus.  
  
5.  Geben Sie im Feld **Name** Folgendes ein: **AdventureWorksReport**.  Ändern Sie den Speicherort nicht.  
  
6.  Klicken Sie auf **OK**.  
  
     Der **Projekt\-Assistent aus Visual Studio Tools for Office** wird geöffnet.  
  
7.  Stellen Sie sicher, dass die Option **Neues Dokument erstellen** ausgewählt ist, und klicken Sie auf **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] öffnet die Arbeitsmappe **AdventureWorksReport** im Designer und fügt dem **Projektmappen\-Explorer** das Projekt **AdventureWorksReport** hinzu.  
  
## Hinzufügen des Datasets zu Datenquellen im Excel\-Arbeitsmappenprojekt  
 Bevor Sie das Dataset in der Excel\-Arbeitsmappe anzeigen können, müssen Sie es zunächst Datenquellen im Excel\-Arbeitsmappenprojekt hinzufügen.  
  
#### So fügen Sie das Dataset den Datenquellen im Excel\-Arbeitsmappenprojekt hinzu  
  
1.  Doppelklicken Sie im **Projektmappen\-Explorer** unter dem Projekt **AdventureWorksReport** auf **Sheet1.cs** bzw. auf **Sheet1.vb**.  
  
     Die Arbeitsmappe wird im Designer geöffnet.  
  
2.  Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.  
  
     Der **Assistent zum Konfigurieren von Datenquellen** wird geöffnet.  
  
3.  Klicken Sie auf **Objekt** und anschließend auf **Weiter**.  
  
4.  Klicken Sie auf der Seite **Objekt auswählen, an das Bindung hergestellt werden soll** auf **Verweis hinzufügen**.  
  
5.  Klicken Sie auf der Registerkarte **Projekte** auf **AdventureWorksDataSet**, und klicken Sie dann auf **OK**.  
  
6.  Klicken Sie unter dem **AdventureWorksDataSet**\-Namespace der **AdventureWorksDataSet**\-Assembly auf **AdventureWorksLTDataSet** und dann auf **Fertig stellen**.  
  
     Das Fenster **Datenquellen** wird geöffnet, und **AdventureWorksLTDataSet** wird der Liste der Datenquellen hinzugefügt.  
  
## Erstellen eines an eine Instanz des Datasets gebundenen ListObject\-Steuerelements  
 Um das Dataset in der Arbeitsmappe anzuzeigen, erstellen Sie ein <xref:Microsoft.Office.Tools.Excel.ListObject>, das an eine Instanz des Datasets gebunden ist.  Weitere Informationen zum Binden von Steuerelementen an Daten finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### So erstellen Sie ein ListObject, das an eine Instanz des Datasets gebunden ist  
  
1.  Erweitern Sie im Fenster **Datenquellen** unter **AdventureWorksDataSet** den Knoten **AdventureWorksLTDataSet**.  
  
2.  Wählen Sie den Knoten **Product**, klicken Sie auf den Dropdownpfeil, und wählen Sie dann **ListObject** aus der Dropdownliste.  
  
     Wenn der Dropdownpfeil nicht angezeigt wird, überprüfen Sie, ob die Arbeitsmappe im Designer geöffnet ist.  
  
3.  Ziehen Sie die Tabelle **Product** zur Zelle A1.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement mit dem Namen `productListObject` wird im Arbeitsblatt beginnend mit Zelle A1 erstellt.  Gleichzeitig werden dem Projekt ein Datasetobjekt mit dem Namen `adventureWorksLTDataSet` und eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `productBindingSource` hinzugefügt.  Das <xref:Microsoft.Office.Tools.Excel.ListObject> ist an die <xref:System.Windows.Forms.BindingSource> gebunden, die wiederum an das DataSet\-Objekt gebunden ist.  
  
## Hinzufügen des Datasets zum Datencache  
 Um Code außerhalb des Excel\-Arbeitsmappenprojekts für den Zugriff auf das Dataset in der Arbeitsmappe zu aktivieren, müssen Sie das Dataset zunächst dem Datencache hinzufügen.  Weitere Informationen über den Datencache finden Sie unter [Zwischengespeicherte Daten in Anpassungen auf Dokumentebene](../vsto/cached-data-in-document-level-customizations.md) und unter [Zwischenspeichern von Daten](../vsto/caching-data.md).  
  
#### So fügen Sie das Dataset dem Datencache hinzu  
  
1.  Klicken Sie im Designer auf **adventureWorksLTDataSet**.  
  
2.  Legen Sie im **Eigenschaftenfenster** die **Modifiers**\-Eigenschaft auf **Public** fest.  
  
3.  Legen Sie die **CacheInDocument**\-Eigenschaft auf **True** fest.  
  
## Checkpoint  
 Erstellen Sie das Excel\-Arbeitsmappenprojekt, und führen Sie es aus, um sicherzustellen, dass es fehlerfrei kompiliert und ausgeführt wird.  
  
#### So erstellen Sie das Projekt und führen es aus  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt **AdventureWorksReport**, wählen Sie **Debuggen**, und klicken Sie dann auf **Neue Instanz starten**.  
  
     Das Projekt wird erstellt, und die Arbeitsmappe wird in Excel geöffnet.  Das <xref:Microsoft.Office.Tools.Excel.ListObject> in Sheet1 ist leer, da das `adventureWorksLTDataSet`\-Objekt im Datencache bisher keine Daten enthält.  Im nächsten Abschnitt verwenden Sie eine Konsolenanwendung, um das `adventureWorksLTDataSet`\-Objekt mit Daten aufzufüllen.  
  
2.  Beenden Sie Excel.  Speichern Sie die Änderungen nicht.  
  
## Erstellen eines Konsolenanwendungsprojekts  
 Erstellen Sie ein Konsolenanwendungsprojekt, das verwendet werden soll, um Daten in das zwischengespeicherte Dataset in der Arbeitsmappe zu einzufügen.  
  
#### So erstellen Sie das Konsolenanwendungsprojekt  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **AdventureWorksDataSet**, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt**.  
  
2.  Erweitern Sie im Bereich **Projekttypen** den Knoten **Visual C\#** oder **Visual Basic**, und klicken Sie dann auf **Windows**.  
  
3.  Wählen Sie im Bereich **Vorlagen** die Option **Konsolenanwendung** aus.  
  
4.  Geben Sie im Feld **Name** die Zeichenfolge **DataWriter** ein.  Ändern Sie den Speicherort nicht.  
  
5.  Klicken Sie auf **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **DataWriter** dem **Projektmappen\-Explorer** hinzu und öffnet die Codedatei **Program.cs** bzw. **Module1.vb**.  
  
## Hinzufügen von Daten mit der Konsolenanwendung zum zwischengespeicherten Dataset  
 Verwenden Sie die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>\-Klasse in der Konsolenanwendung, um das zwischengespeicherte Dataset in der Arbeitsmappe mit Daten aufzufüllen.  
  
#### So fügen Sie Daten zum zwischengespeicherten Dataset hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt **DataWriter**, und klicken Sie dann auf **Verweis hinzufügen**.  
  
2.  Klicken Sie auf der Registerkarte **.NET** ausgewähltes **Microsoft.VisualStudio.Tools.Applications.ServerDocument**.  
  
3.  Klicken Sie auf **OK**.  
  
4.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt **DataWriter**, und klicken Sie dann auf **Verweis hinzufügen**.  
  
5.  Wählen Sie auf der Registerkarte **Projekte** die Option **AdventureWorksDataSet**, und klicken Sie auf **OK**.  
  
6.  Öffnen Sie die Datei **Program.cs** oder die Datei **Module1.vb** im Code\-Editor.  
  
7.  Fügen Sie die folgende **using**\-Anweisung \(für C\#\) bzw. die **Imports**\-Anweisung \(für Visual Basic\) am Anfang der Codedatei hinzu.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#1)]  
  
8.  Fügen Sie der `Main`\-Methode folgenden Code hinzu:  Mit diesem Code werden die folgenden Objekte deklariert:  
  
    -   Instanzen vom `AdventureWorksLTDataSet`\-Typ und Instanzen vom `ProductTableAdapter`\-Typ, die im **AdventureWorksDataSet**\-Projekt definiert sind.  
  
    -   Der Pfad zur AdventureWorksReport\-Arbeitsmappe im build\-Ordner des **AdventureWorksReport**\-Projekts.  
  
    -   Ein <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>\-Objekt für den Zugriff auf den Datencache der Arbeitsmappe.  
  
        > [!NOTE]  
        >  Im folgenden Code wird davon ausgegangen, dass Sie eine Arbeitsmappe mit der Erweiterung .xlsx verwenden.  Wenn die Arbeitsmappe im Projekt eine andere Dateinamenerweiterung hat, ändern Sie den Pfad wie erforderlich.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#3)]
     [!code-vb[Trin_CachedDataWalkthroughs#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#3)]  
  
9. Fügen Sie der `Main`\-Methode den folgenden Code nach dem im vorherigen Schritt hinzugefügten Code hinzu.  Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Das typisierte Datasetobjekt wird mit dem Tabellenadapter aufgefüllt.  
  
    -   Er verwendet die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>\-Eigenschaft der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>\-Klasse, um auf das zwischengespeicherte Dataset in der Arbeitsmappe zuzugreifen.  
  
    -   Er verwendet die <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>\-Methode, um das zwischengespeicherte Dataset mit Daten aus dem lokalen typisierten Dataset aufzufüllen.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#4)]
     [!code-vb[Trin_CachedDataWalkthroughs#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#4)]  
  
10. Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt **DataWriter**, zeigen Sie auf **Debuggen**, und klicken Sie dann auf **Neue Instanz starten**.  
  
     Das Projekt wird erstellt, und die Konsolenanwendung zeigt mehrere Statusmeldungen an, wenn das lokale Dataset aufgefüllt wird und wenn die Anwendung die Daten in das zwischengespeicherte Dataset im Workbook speichert.  Drücken Sie die Eingabetaste, um die Anwendung zu schließen.  
  
## Testen der Arbeitsmappe  
 Wenn Sie die Arbeitsmappe öffnen, zeigt das <xref:Microsoft.Office.Tools.Excel.ListObject> nun Daten an, die mit der Konsolenanwendung dem zwischengespeicherten Dataset hinzugefügt wurden.  
  
#### So testen Sie die Arbeitsmappe  
  
1.  Schließen Sie die AdventureWorksReport\-Arbeitsmappe im Visual Studio\-Designer, wenn sie immer noch geöffnet ist.  
  
2.  Im Datei\-Explorer öffnen Sie die AdventureWorksReport\-Arbeitsmappe, die im Buildordner des **AdventureWorksReport** Projekts ist.  Standardmäßig befindet sich der Buildordner an einem der folgenden Speicherorte:  
  
    -   %UserProfile%\\Eigene Dateien\\AdventureWorksReport\\bin\\Debug \(Windows XP und früher\)  
  
    -   %UserProfile%\\Dokumente\\AdventureWorksReport\\bin\\Debug \(Windows Vista\)  
  
3.  Überprüfen Sie, dass das <xref:Microsoft.Office.Tools.Excel.ListObject> mit Daten aufgefüllt ist, nachdem Sie die Arbeitsmappe geöffnet haben.  
  
## Nächste Schritte  
 Mehr über das Arbeiten mit zwischengespeicherten Daten erfahren Sie in den folgenden Themen:  
  
-   Ändern der Daten in einem zwischengespeicherten Dataset ohne Starten von Excel.  Weitere Informationen hierzu finden Sie unter [Exemplarische Vorgehensweise: Ändern zwischengespeicherter Daten in einer Arbeitsmappe auf einem Server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Ändern zwischengespeicherter Daten in einer Arbeitsmappe auf einem Server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
 [Herstellen einer Verbindung mit Daten in Windows Forms-Anwendungen](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  