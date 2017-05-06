---
title: "Exemplarische Vorgehensweise: Erstellen einer Master/Detail-Beziehung mithilfe eines zwischengespeicherten Datasets"
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
  - "Zwischenspeichern von Daten [Office-Entwicklung in Visual Studio], Master-/Detail-Beziehung"
  - "Master-/Detail-Tabellen [Office-Entwicklung in Visual Studio], Exemplarische Vorgehensweisen"
ms.assetid: 419f4e07-c67f-4fc9-973a-bc794f349ac3
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Exemplarische Vorgehensweise: Erstellen einer Master/Detail-Beziehung mithilfe eines zwischengespeicherten Datasets
  Diese exemplarische Vorgehensweise erläutert, wie Sie in einem Arbeitsblatt eine Master\/Detail\-Beziehung erstellen und die Daten für die Offlineverwendung zwischenspeichern.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Hinzufügen von Steuerelementen zu einem Arbeitsblatt.  
  
-   Einrichten eines Datasets, das in einem Arbeitsblatt zwischengespeichert werden soll.  
  
-   Hinzufügen von Code, um Bildlauf durch die Datensätze zu ermöglichen.  
  
-   Testen des Projekts.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die von Ihnen verwendete Visual Studio\-Edition und die Einstellungen legen diese Elemente fest.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Zugriff auf die Northwind SQL Server\-Beispieldatenbank.  Die Datenbank kann sich auf dem Entwicklungscomputer oder einem Server befinden.  
  
-   Lese\- und Schreibberechtigungen für die SQL Server\-Datenbank.  
  
## Erstellen eines neuen Projekts  
 In diesem Schritt wird ein Excel\-Arbeitsmappenprojekt erstellt.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie mit Visual Basic oder C\# ein Excel\-Arbeitsmappenprojekt mit dem Namen **My Master\-Detail**.  Stellen Sie sicher, dass **Neues Dokument erstellen** ausgewählt ist.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio öffnet die neue Excel\-Arbeitsmappe im Designer und fügt dem **Projektmappen\-Explorer** das Projekt "My Master\-Detail" hinzu.  
  
## Erstellen der Datenquelle  
 Verwenden Sie das **Datenquellenfenster**, um dem Projekt ein typisiertes Dataset hinzuzufügen.  
  
#### So erstellen Sie die Datenquelle  
  
1.  Wenn das **Datenquellen** nicht sichtbar ist, zeigen Sie sie durch, auf der Menüleiste auf und **Ansicht** auswählen, **Weitere Fenster**, **Datenquellen**.  
  
2.  Wählen Sie **Neue Datenquelle hinzufügen**, um **Assistent zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Wählen Sie **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Wählen Sie eine Datenverbindung zur Northwind SQL Server\-Beispieldatenbank aus, oder fügen Sie mithilfe der Schaltfläche **Neue Verbindung** eine neue Verbindung hinzu.  
  
5.  Klicken Sie nach dem Auswählen oder Erstellen einer Verbindung auf **Weiter**.  
  
6.  Deaktivieren Sie ggf. die Option zum Speichern der Verbindung, und klicken Sie dann auf **Weiter**.  
  
7.  Erweitern Sie im Fenster **Datenbankobjekte** den Knoten **Tabellen**.  
  
8.  Wählen Sie die Tabelle **Orders** und die Tabelle **Order Details** aus.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
 Der Assistent fügt die beiden Tabellen dem **Datenquellenfenster** hinzu.  Außerdem wird dem Projekt ein typisiertes Dataset hinzugefügt, das im **Projektmappen\-Explorer** sichtbar ist.  
  
## Hinzufügen von Steuerelementen zum Arbeitsblatt  
 In diesem Schritt fügen Sie dem ersten Arbeitsblatt einen benannten Bereich, ein Listenobjekt und zwei Schaltflächen hinzu.  Fügen Sie zuerst den benannten Bereich und das Listenobjekt aus dem **Datenquellenfenster** hinzu, damit diese automatisch an die Datenquelle gebunden werden.  Fügen Sie dann die Schaltflächen aus der **Toolbox** hinzu.  
  
#### So fügen Sie einen benannten Bereich und ein Listenobjekt hinzu  
  
1.  Überprüfen Sie, ob die **My Master\-Detail.xlsx** Arbeitsmappe im Visual Studio\-Designer geöffnet ist, mit **Blatt1** angezeigt.  
  
2.  Öffnen Sie das **Datenquellenfenster**, und erweitern Sie den Knoten **Orders**.  
  
3.  Wählen Sie die Spalte **OrderID**, und klicken Sie anschließend auf den angezeigten Dropdownpfeil.  
  
4.  Klicken Sie in der Dropdownliste auf **NamedRange**, und ziehen Sie die Spalte **OrderID** auf die Zelle **A2**.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement mit Namen `OrderIDNamedRange` wird in der Zelle **A2** erstellt.  Gleichzeitig werden dem Projekt eine <xref:System.Windows.Forms.BindingSource> mit Namen `OrdersBindingSource`, ein Tabellenadapter und eine <xref:System.Data.DataSet>\-Instanz hinzugefügt.  Das Steuerelement ist an die <xref:System.Windows.Forms.BindingSource> gebunden, die wiederum an die <xref:System.Data.DataSet>\-Instanz gebunden ist.  
  
5.  Führen Sie einen Bildlauf nach unten durch, an den Spalten unterhalb der Tabelle **Orders** vorbei.  Am unteren Rand der Liste befindet sich die Tabelle **Order Details**, die ihren Platz an dieser Stelle einnimmt, weil sie ein untergeordnetes Element der Tabelle **Orders** ist.  Wählen Sie genau diese **Order Details**\-Tabelle aus und nicht die Tabelle, die mit der Tabelle **Orders** auf einer Ebene liegt. Klicken Sie anschließend auf den angezeigten Dropdownpfeil.  
  
6.  Klicken Sie in der Dropdownliste auf **ListObject**, und ziehen Sie die Tabelle **Order Details** auf die Zelle **A6**.  
  
7.  Ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement mit dem Namen **Order\_DetailsListObject** wird in der Zelle **A6** erstellt und an <xref:System.Windows.Forms.BindingSource> gebunden.  
  
#### So fügen Sie zwei Schaltflächen hinzu  
  
1.  Klicken Sie in der **Toolbox** auf die Registerkarte **Allgemeine Steuerelemente**, und fügen Sie von dort ein <xref:System.Windows.Forms.Button>\-Steuerelement zur Zelle **A3** des Arbeitsblattes hinzu.  
  
     Diese Schaltfläche erhält den Namen `Button1`.  
  
2.  Fügen Sie auch der Zelle **B3** des Arbeitsblatts ein <xref:System.Windows.Forms.Button>\-Steuerelement hinzu.  
  
     Diese Schaltfläche erhält den Namen `Button2`.  
  
 Markieren Sie anschließend das Dataset, das im Dokument zwischengespeichert werden soll.  
  
## Zwischenspeichern des Datasets  
 Markieren Sie das Dataset, das im Dokument zwischengespeichert werden soll, indem Sie das Dataset veröffentlichen und die **CacheInDocument**\-Eigenschaft festlegen.  
  
#### So wird das Dataset zwischengespeichert  
  
1.  Wählen Sie auf der Komponentenleiste **NorthwindDataset** aus.  
  
2.  Ändern Sie im **Eigenschaftenfenster** die **Modifiers**\-Eigenschaft in **Public**.  
  
     Datasets müssen vor dem Zwischenspeichern veröffentlicht werden.  
  
3.  Ändern Sie die **CacheInDocument**\-Eigenschaft in **True**.  
  
 Der nächsten Schritt besteht darin, den Schaltflächen Text hinzuzufügen. In C\# müssen Sie Code hinzufügen, um die Ereignishandler einzubinden.  
  
## Initialisieren der Steuerelemente  
 Legen Sie den Schaltflächentext fest, und fügen Sie Ereignishandler während des <xref:Microsoft.Office.Tools.Excel.Workbook.Startup>\-Ereignisses hinzu.  
  
#### So initialisieren Sie die Daten und die Steuerelemente  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **Sheet1.vb** oder **Sheet1.cs**, und klicken Sie dann im Kontextmenü auf **Code anzeigen**.  
  
2.  Fügen Sie der `Sheet1_Startup`\-Methode den folgenden Code hinzu, um den Text für die Schaltflächen festzulegen.  
  
     [!code-csharp[Trin_VstcoreDataExcel#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#15)]
     [!code-vb[Trin_VstcoreDataExcel#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#15)]  
  
3.  Nur in C\#: Fügen Sie der `Sheet1_Startup`\-Methode Ereignishandler für die Klickereignisse der Schaltflächen hinzu.  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#16)]  
  
## Hinzufügen von Code, um das Durchführen des Bildlaufs durch die Datensätze zu ermöglichen  
 Fügen Sie den <xref:System.Windows.Forms.Control.Click>\-Ereignishandlern der einzelnen Schaltflächen Code hinzu, um durch die Datensätze zu navigieren.  
  
#### So führen Sie den Bildlauf durch die Datensätze aus  
  
1.  Fügen Sie dem <xref:System.Windows.Forms.Control.Click>\-Ereignis von `Button1` einen Ereignishandler mit folgendem Code hinzu, um sich rückwärts durch die Datensätze zu bewegen:  
  
     [!code-csharp[Trin_VstcoreDataExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#17)]
     [!code-vb[Trin_VstcoreDataExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#17)]  
  
2.  Fügen Sie dem <xref:System.Windows.Forms.Control.Click>\-Ereignis von `Button2` einen Ereignishandler mit folgendem Code hinzu, um sich vorwärts durch die Datensätze zu bewegen:  
  
     [!code-csharp[Trin_VstcoreDataExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#18)]
     [!code-vb[Trin_VstcoreDataExcel#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#18)]  
  
## Testen der Anwendung  
 Sie können die Arbeitsmappe jetzt testen, um zu überprüfen, ob die Daten wie erwartet angezeigt werden und Sie die Projektmappe offline verwenden können.  
  
#### So testen Sie das Zwischenspeichern von Daten  
  
1.  Drücken Sie **F5**.  
  
2.  Stellen Sie sicher, dass der benannte Bereich und das Listenobjekt mit Daten aus der Datenquelle gefüllt werden.  
  
3.  Führen Sie einen Bildlauf durch die Datensätze aus, indem Sie auf die Schaltflächen klicken.  
  
4.  Speichern Sie die Arbeitsmappe, und schließen Sie anschließend die Arbeitsmappe und Visual Studio.  
  
5.  Deaktivieren Sie die Datenbankverbindung.  Ziehen Sie das Netzwerkkabel vom Computer ab, wenn sich die Datenbank auf einem Server befindet, oder beenden Sie den SQL Server\-Dienst, wenn sich die Datenbank auf dem Entwicklungscomputer befindet.  
  
6.  Öffnen Sie Excel und öffnen Sie dann **My Master\-Detail.xlsx** im Verzeichnis \\bin \(\\My Master\-Detail\\bin in Visual Basic oder \\My Master\-Detail\\bin\\debug in C\#\).  
  
7.  Führen Sie einen Bildlauf durch einige der Datensätze aus, um sicherzustellen, dass das Arbeitsblatt auch offline normal verwendet werden kann.  
  
8.  Stellen Sie die Datenbankverbindung wieder her.  Verbinden Sie den Computer wieder mit dem Netzwerk, wenn sich die Datenbank auf einem Server befindet, oder starten Sie den SQL Server\-Dienst, wenn sich die Datenbank auf dem Entwicklungscomputer befindet.  
  
## Nächste Schritte  
 Diese exemplarische Vorgehensweise vermittelt die Grundlagen für das Erstellen einer Master\/Detail\-Beziehung in einem Arbeitsblatt und für das Zwischenspeichern eines Datasets.  Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Bereitstellen der Projektmappe.  Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
## Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Daten in Office-Lösungen](../vsto/data-in-office-solutions.md)   
 [Zwischenspeichern von Daten](../vsto/caching-data.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
  