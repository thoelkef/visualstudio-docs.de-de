---
title: 'Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktionsbereich'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d450a9c52ae8558167bf4cb581ce2e36f44f4e9
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767909"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktionsbereich
  In dieser exemplarischen Vorgehensweise veranschaulicht das Binden von Daten an Steuerelemente in einem Aktionsbereich in Microsoft Office Excel. Die Steuerelemente zeigen eine Master/Detail-Beziehung zwischen Tabellen in einer SQL Server-Datenbank.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen von Steuerelementen zu einem Arbeitsblatt ein.  
  
-   Erstellen ein Aktionsbereich-Steuerelement.  
  
-   Hinzufügen von datengebundenen Windows Forms-Steuerelemente in einem Aktionsbereich-Steuerelement.  
  
-   Anzeigen des Aktionsbereichs, wenn die Anwendung geöffnet wird.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Zugriff auf einen Server mit der Beispieldatenbank Northwind-SQL Server.  
  
-   Berechtigungen zum Lesen und Schreiben in SQL Server-Datenbank.  
  
## <a name="create-the-project"></a>Erstellen eines Projekts  
 Zunächst müssen Sie ein Excel-Arbeitsmappenprojekt erstellen.  
  
### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **meine Excel-Aktionsbereich**. Wählen Sie im Assistenten **erstellen Sie ein neues Dokument**. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekte in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **meine Excel-Aktionsbereich** Projekt **Projektmappen-Explorer**.  
  
## <a name="add-a-new-data-source-to-the-project"></a>Fügen Sie dem Projekt eine neue Datenquelle  
  
### <a name="to-add-a-new-data-source-to-the-project"></a>Um dem Projekt eine neue Datenquelle hinzufügen  
  
1.  Wenn die **Datenquellen** Fenster nicht sichtbar ist, zeigen Sie es an, indem in der Menüleiste **Ansicht** > **Weitere Fenster**  >   **Datenquellen**.  
  
2.  Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.  
  
3.  Wählen Sie **Datenbank** , und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie eine Datenverbindung zur Northwind-Beispieldatenbank SQL Server, oder fügen Sie eine neue Verbindung mit der **neue Verbindung** Schaltfläche.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Deaktivieren Sie die Option aus, um die Verbindung zu speichern, wenn diese Option ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
7.  Erweitern Sie die **Tabellen** Knoten in der **-Datenbankobjekte** Fenster.  
  
8.  Aktivieren Sie das Kontrollkästchen neben den **Lieferanten** Tabelle.  
  
9. Erweitern Sie die **Produkte** Tabelle, und wählen Sie **ProductName**, **SupplierID**, **QuantityPerUnit**, und **UnitPrice**.  
  
10. Klicken Sie auf **Fertig stellen**.  
  
 Fügt der Assistent die **Lieferanten** Tabelle und **Produkte** Tabelle, auf die **Datenquellen** Fenster. Es auch ein typisiertes Dataset dem Projekt hinzugefügt, die in angezeigt wird **Projektmappen-Explorer**.  
  
## <a name="add-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt  
 Als Nächstes fügen Sie eine <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement und ein <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement auf das erste Arbeitsblatt.  
  
### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>So fügen Sie ein NamedRange-Steuerelement und ein ListObject-Steuerelement hinzu  
  
1.  Überprüfen Sie, ob die **meine Excel Aktionen Pane.xlsx** Arbeitsmappe geöffnet, in der Visual Studio-Designer ist mit `Sheet1` angezeigt.  
  
2.  In der **Datenquellen** Fenster, erweitern Sie die **Lieferanten** Tabelle.  
  
3.  Klicken Sie auf den Dropdown Pfeil auf der **Firmenname** Knoten, und klicken Sie dann auf **NamedRange**.  
  
4.  Ziehen Sie **Firmenname** aus der **Datenquellen** in Zelle **A2** in `Sheet1`.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement namens `CompanyNameNamedRange` wird erstellt, und der Text \<CompanyName > wird angezeigt, in die Zelle **A2**. Zur gleichen Zeit eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `suppliersBindingSource`, Tabellenadapters, und ein <xref:System.Data.DataSet> werden dem Projekt hinzugefügt. Das Steuerelement gebunden ist die <xref:System.Windows.Forms.BindingSource>, das wiederum gebunden ist, um die <xref:System.Data.DataSet> Instanz.  
  
5.  In der **Datenquellen** Fenster einen Bildlauf nach unten nach den Spalten, die unter der **Lieferanten** Tabelle. Wird am unteren Rand der Liste der **Produkte** Tabelle; ist hier, da es ein untergeordnetes Element eines ist die **Lieferanten** Tabelle. Wählen Sie diese Option **Produkte** Tabelle, nicht auf das Projekt, das auf der gleichen Ebene wie ist die **Lieferanten** Tabelle, und klicken Sie dann auf den Dropdown Pfeil, der angezeigt wird.  
  
6.  Klicken Sie auf **ListObject** in der Dropdownliste aus, und ziehen Sie dann die **Produkte** Tabelle Zelle **A6** in `Sheet1`.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement namens `ProductNameListObject` ist in der Zelle erstellt **A6**. Zur gleichen Zeit eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `productsBindingSource` und Tabellenadapters werden dem Projekt hinzugefügt. Das Steuerelement gebunden ist die <xref:System.Windows.Forms.BindingSource>, das wiederum gebunden ist, um die <xref:System.Data.DataSet> Instanz.  
  
7.  Wählen Sie nur für c#, **SuppliersBindingSource** auf der Komponentenleiste, und ändern Sie die **Modifizierer** Eigenschaft **intern** in der **Eigenschaften** Fenster.  
  
## <a name="add-controls-to-the-actions-pane"></a>Hinzufügen von Steuerelementen zum Aktionsbereich  
 Als Nächstes benötigen Sie ein Aktionsbereich-Steuerelement, das ein Kombinationsfeld hat.  
  
### <a name="to-add-an-actions-pane-control"></a>So fügen Sie einem Aktionsbereich-Steuerelement hinzu  
  
1.  Wählen Sie die **meine Excel-Aktionsbereich** Projekt **Projektmappen-Explorer**.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  In der **neues Element hinzufügen** wählen Sie im Dialogfeld **Aktionsbereich-Steuerelement**, nennen Sie sie **ActionsControl**, und klicken Sie auf **hinzufügen**.  
  
### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Hinzufügen von datengebundenen Windows Forms-Steuerelementen zu einem Aktionsbereich-Steuerelement  
  
1.  Aus der **Standardsteuerelementen** Registerkarten für die **Toolbox**, ziehen Sie ein <xref:System.Windows.Forms.ComboBox> Steuerelement, um den Aktionsbereich-Steuerelement.  
  
2.  Ändern der **Größe** Eigenschaft **171, 21**.  
  
3.  Ändern Sie die Größe des Benutzersteuerelements im Kombinationsfeld entsprechen.  
  
## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Binden des Steuerelements in einem Aktionsbereich an Daten  
 In diesem Abschnitt legen Sie die Datenquelle der <xref:System.Windows.Forms.ComboBox> auf derselben Datenquelle wie die <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement auf das Arbeitsblatt.  
  
### <a name="to-set-data-binding-properties-of-the-control"></a>Um die Datenbindungseigenschaften des Steuerelements festlegen  
  
1.  Mit der rechten Maustaste in den Aktionsbereich-Steuerelement, und klicken Sie dann auf **Code anzeigen**.  
  
2.  Fügen Sie folgenden Code, der <xref:System.Windows.Forms.UserControl.Load> -Ereignis für den Aktionsbereich-Steuerelement.  
  
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]  
  
3.  In c#, erstellen Sie einen Ereignishandler für das `ActionsControl`. Sie können diesen Code im Platzieren der `ActionsControl` Konstruktor. Weitere Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]  
  
## <a name="show-the-actions-pane"></a>Anzeigen des Aktionsbereichs  
 Der Aktionsbereich ist nicht sichtbar, bis Sie das Steuerelement zur Laufzeit hinzufügen.  
  
#### <a name="to-show-the-actions-pane"></a>Um den Aktionsbereich anzuzeigen  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste *ThisWorkbook.vb* oder *ThisWorkbook.cs*, und klicken Sie dann auf **Code anzeigen**.  
  
2.  Erstellen Sie eine neue Instanz des Benutzersteuerelements in die `ThisWorkbook` Klasse.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]  
  
3.  In der <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> -Ereignishandler des `ThisWorkbook`, im Aktionsbereich-Steuerelement hinzufügen.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]  
  
## <a name="test-the-application"></a>Testen der Anwendung  
 Sie können jetzt testen, dass das Dokument, um sicherzustellen, dass der Aktionsbereich wird geöffnet, wenn das Dokument geöffnet wird und die Steuerelemente eine Master/Detail-Beziehung enthalten.  
  
### <a name="to-test-your-document"></a>So testen Sie das Dokument  
  
1.  Drücken Sie **F5** um das Projekt auszuführen.  
  
2.  Vergewissern Sie sich, dass der Aktionsbereich sichtbar ist.  
  
3.  Wählen Sie im Listenfeld ein Unternehmen ein. Stellen Sie sicher, dass der Unternehmensname in aufgeführt ist die <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement und, dass die Produktdetails, in aufgeführt sind der <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement.  
  
4.  Wählen Sie verschiedene Unternehmen, um zu überprüfen, ob der Firmenname und Produktdetails je nach Bedarf ändern.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Binden von Daten an Steuerelemente in Word. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
-   Beim Bereitstellen des Projekts. Weitere Informationen finden Sie unter [bereitstellen eine Office-Projektmappe mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md)   
 [Vorgehensweise: Verwalten des Steuerelementlayouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  