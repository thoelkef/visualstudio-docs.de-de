---
title: "Exemplarische Vorgehensweise: Bindung von Daten an Steuerelemente in einem Excel-Aktionsbereich | Microsoft Docs"
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
  - "Aktionsbereiche [Office-Entwicklung in Visual Studio], Binden von Steuerelementen"
  - "Aktionsbereiche [Office-Entwicklung in Visual Studio], Datenbindung"
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Datenbindung"
  - "Datenbindung [Office-Entwicklung in Visual Studio], Aktionsbereiche"
  - "Datenbindung [Office-Entwicklung in Visual Studio], SmartDocuments"
  - "SmartDocuments [Office-Entwicklung in Visual Studio], Datenbindung"
ms.assetid: 106c07bd-e931-4dc5-94dc-ca43900fe09d
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Exemplarische Vorgehensweise: Bindung von Daten an Steuerelemente in einem Excel-Aktionsbereich
  In dieser exemplarischen Vorgehensweise wird die Datenbindung an Steuerelemente in einem Aktionsbereich von Microsoft Office Excel veranschaulicht.  Die Steuerelemente veranschaulichen eine Master\/Detail\-Beziehung zwischen Tabellen in einer SQL Server\-Datenbank.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen von Steuerelementen zu einem Arbeitsblatt  
  
-   Erstellen eines Aktionsbereich\-Steuerelements  
  
-   Hinzufügen von datengebundenen Windows Forms\-Steuerelementen zu einem Aktionsbereich\-Steuerelement  
  
-   Anzeigen des Aktionsbereichs, wenn die Anwendung geöffnet wird  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die von Ihnen verwendete Visual Studio\-Edition und die Einstellungen legen diese Elemente fest.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Zugriff auf einen Server mit der SQL Server\-Beispieldatenbank **Northwind**.  
  
-   Lese\- und Schreibberechtigungen für die SQL Server\-Datenbank.  
  
## Erstellen des Projekts  
 Zunächst müssen Sie ein Excel\-Arbeitsmappenprojekt erstellen.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel\-Arbeitsmappenprojekt mit dem Namen My Excel Actions Pane.  Wählen Sie im Assistenten **Neues Dokument erstellen** aus.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die neue Excel\-Arbeitsmappe im Designer und fügt dem **Projektmappen\-Explorer** das **My Excel Actions Pane**\-Projekt hinzu.  
  
## Hinzufügen einer neuen Datenquelle zum Projekt  
  
#### So fügen Sie dem Projekt eine neue Datenquelle hinzu  
  
1.  Wenn das **Datenquellen** nicht sichtbar ist, zeigen Sie sie durch, auf der Menüleiste auf und **Ansicht** auswählen, **Weitere Fenster**, **Datenquellen**.  
  
2.  Wählen Sie **Neue Datenquelle hinzufügen**, um **Assistent zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Wählen Sie **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Wählen Sie eine Datenverbindung zur Northwind SQL Server\-Beispieldatenbank aus, oder fügen Sie mithilfe der Schaltfläche **Neue Verbindung** eine neue Verbindung hinzu.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Deaktivieren Sie ggf. die Option zum Speichern der Verbindung, und klicken Sie dann auf **Weiter**.  
  
7.  Erweitern Sie im Fenster **Datenbankobjekte** den Knoten **Tabellen**.  
  
8.  Aktivieren Sie das Kontrollkästchen neben der Tabelle **Suppliers**.  
  
9. Erweitern Sie die Tabelle **Products**, und wählen Sie **ProductName**, **SupplierID**, **QuantityPerUnit** und **UnitPrice** aus.  
  
10. Klicken Sie auf **Fertig stellen**.  
  
 Der Assistent fügt dem **Datenquellenfenster** die Tabelle **Suppliers** und die Tabelle **Products** hinzu.  Außerdem wird dem Projekt ein typisiertes Dataset hinzugefügt, das im **Projektmappen\-Explorer** sichtbar ist.  
  
## Hinzufügen von Steuerelementen zum Arbeitsblatt  
 Fügen Sie dem ersten Arbeitsblatt als Nächstes ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement und ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement hinzu.  
  
#### So fügen Sie ein NamedRange\-Steuerelement und ein ListObject\-Steuerelement hinzu  
  
1.  Überprüfen Sie, ob die **My Excel Actions Pane.xlsx** Arbeitsmappe im Visual Studio\-Designer geöffnet ist, mit `Sheet1` angezeigt.  
  
2.  Erweitern Sie im  **Datenquellenfenster** die Tabelle **Suppliers**.  
  
3.  Klicken Sie im Knoten **Company Name** auf den Dropdownpfeil, und klicken Sie dann auf **NamedRange**.  
  
4.  Ziehen Sie **Company Name** aus dem **Datenquellenfenster** in Zelle **A2** in `Sheet1`.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement mit dem Namen `CompanyNameNamedRange` wird erstellt, und der Text \<CompanyName\> wird in Zelle **A2** angezeigt.  Gleichzeitig werden dem Projekt eine <xref:System.Windows.Forms.BindingSource> mit Namen `suppliersBindingSource`, ein Tabellenadapter und <xref:System.Data.DataSet> hinzugefügt.  Das Steuerelement ist an die <xref:System.Windows.Forms.BindingSource> gebunden, die wiederum an die <xref:System.Data.DataSet>\-Instanz gebunden ist.  
  
5.  Führen Sie im **Datenquellenfenster** einen Bildlauf nach unten durch, an den Spalten unter der Tabelle **Suppliers** vorbei.  Am unteren Rand der Liste befindet sich die Tabelle **Products**, die sich an dieser Stelle befindet, weil sie ein untergeordnetes Element der Tabelle **Suppliers** ist.  Wählen Sie genau diese **Products**\-Tabelle aus und nicht die Tabelle, die mit der **Suppliers**\-Tabelle auf einer Ebene liegt. Klicken Sie anschließend auf den angezeigten Dropdownpfeil.  
  
6.  Wählen Sie in der Dropdownliste **ListObject** aus, und ziehen Sie die Tabelle **Products** auf die Zelle **A6** in `Sheet1`.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement mit dem Namen `ProductNameListObject` wird in der Zelle **A6** erstellt.  Gleichzeitig werden dem Projekt eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `productsBindingSource` und ein Tabellenadapter hinzugefügt.  Das Steuerelement ist an die <xref:System.Windows.Forms.BindingSource> gebunden, die wiederum an die <xref:System.Data.DataSet>\-Instanz gebunden ist.  
  
7.  Nur bei C\#: Wählen Sie **suppliersBindingSource** auf der Komponentenleiste, und ändern Sie die **Modifiers**\-Eigenschaft im Eigenschaftenfenster auf **Internal**.  
  
## Hinzufügen von Steuerelementen zum Aktionsbereich  
 Sie benötigen nun ein Aktionsbereich\-Steuerelement, das ein Kombinationsfeld enthält.  
  
#### So fügen Sie ein Aktionsbereich\-Steuerelement hinzu  
  
1.  Wählen Sie im **Projektmappen\-Explorer** das Projekt **My Excel Actions Pane** aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Aktionsbereich\-Steuerelement** aus. Nennen Sie das Steuerelement **ActionsControl**, und klicken Sie auf **Hinzufügen**.  
  
#### So fügen Sie datengebundene Windows Forms\-Steuerelemente zu einem Aktionsbereich\-Steuerelement hinzu  
  
1.  Ziehen Sie aus der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** ein <xref:System.Windows.Forms.ComboBox>\-Steuerelement in das Aktionsbereich\-Steuerelement.  
  
2.  Ändern Sie die **Size**\-Eigenschaft auf 171, 21.  
  
3.  Passen Sie die Größe des Benutzersteuerelements dem Kombinationsfeld entsprechend an.  
  
## Binden des Steuerelements im Aktionsbereich an Daten  
 In diesem Abschnitt legen Sie die Datenquelle von <xref:System.Windows.Forms.ComboBox> auf dieselbe Datenquelle wie das <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement im Arbeitsblatt fest.  
  
#### So legen Sie die Datenbindungseigenschaften des Steuerelements fest  
  
1.  Klicken Sie mit der rechten Maustaste auf das Aktionsbereich\-Steuerelement, und klicken Sie dann auf **Code anzeigen**.  
  
2.  Fügen Sie dem <xref:System.Windows.Forms.UserControl.Load>\-Ereignis des Aktionsbereich\-Steuerelements den folgenden Code hinzu.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ActionsControl.vb#1)]  
  
3.  In C\# müssen Sie einen Ereignishandler für `ActionsControl` erstellen.  Sie können diesen Code im `ActionsControl`\-Konstruktor einfügen.  Weitere Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ActionsControl.cs#2)]  
  
## Anzeigen des Aktionsbereichs  
 Der Aktionsbereich wird erst sichtbar, wenn Sie das Steuerelement zur Laufzeit hinzufügen.  
  
#### So zeigen Sie den Aktionsbereich an  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf ThisWorkbook.vb bzw. ThisWorkbook.cs, und klicken Sie dann auf **Code anzeigen**.  
  
2.  Erstellen Sie in der `ThisWorkbook`\-Klasse eine neue Instanz des Benutzersteuerelements.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#3)]  
  
3.  Fügen Sie im <xref:Microsoft.Office.Tools.Excel.Workbook.Startup>\-Ereignishandler von `ThisWorkbook` dem Aktionsbereich das Steuerelement hinzu.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#4)]  
  
## Testen der Anwendung  
 Nun können Sie das Dokument testen, um zu überprüfen, ob der Aktionsbereich beim Öffnen des Dokuments geöffnet wird und ob die Steuerelemente eine Master\/Detail\-Beziehung aufweisen.  
  
#### So testen Sie das Dokument  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Bestätigen Sie, dass der Aktionsbereich angezeigt wird.  
  
3.  Wählen Sie im Listenfeld eine Firma aus.  Überprüfen Sie, ob der Firmenname im <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement aufgeführt ist und ob die Produktdetails im <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement aufgeführt sind.  
  
4.  Wählen Sie verschiedene Firmen aus, um zu überprüfen, ob sich Firmenname und Produktdetails entsprechend ändern.  
  
## Nächste Schritte  
 Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Datenbindung an Steuerelemente in Word.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
-   Bereitstellen des Projekts.  Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## Siehe auch  
 [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md)   
 [Gewusst wie: Verwalten des Steuerelementlayouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  