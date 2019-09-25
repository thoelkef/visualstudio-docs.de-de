---
title: 'Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktionsbereich'
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1543f872961d556674dd5ad6b3f5b8071d2d404b
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253886"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktionsbereich
  Diese exemplarische Vorgehensweise veranschaulicht die Datenbindung an Steuerelemente in einem Aktionsbereich in Microsoft Office Excel. Die Steuerelemente zeigen eine Master/Detail-Beziehung zwischen Tabellen in einer SQL Server-Datenbank.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen von Steuerelementen zu einem Arbeitsblatt

- Erstellen eines Aktionsbereich-Steuer Elements.

- Hinzufügen von Daten gebundenen Windows Forms-Steuerelementen zu einem Aktionsbereich-Steuerelement.

- Hiermit wird der Aktionsbereich angezeigt, wenn die Anwendung geöffnet wird.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Erforderliche Komponenten
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Zugriff auf einen Server mit der Beispieldatenbank Northwind SQL Server.

- Lese-und Schreibberechtigungen für die SQL Server Datenbank.

## <a name="create-the-project"></a>Erstellen eines Projekts
 Zunächst müssen Sie ein Excel-Arbeitsmappenprojekt erstellen.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen " **Meine Excel-Aktionen**". Wählen Sie im Assistenten **Neues Dokument erstellen**aus. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie Office-Projekte in](../vsto/how-to-create-office-projects-in-visual-studio.md)Visual Studio.

     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt **Projektmappen-Explorer**das Projekt **Meine Excel-Aktions** Bereiche hinzu.

## <a name="add-a-new-data-source-to-the-project"></a>Fügen Sie dem Projekt eine neue Datenquelle hinzu.

### <a name="to-add-a-new-data-source-to-the-project"></a>So fügen Sie dem Projekt eine neue Datenquelle hinzu

1. Wenn das **Fenster Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie auf der Menüleiste **die Option** > **Weitere Windows** > -**Datenquellen**anzeigen auswählen.

2. Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.

3. Wählen Sie **Datenbank** aus, und klicken Sie dann auf **weiter**.

4. Wählen Sie eine Datenverbindung mit der Beispieldatenbank Northwind SQL Server aus, oder fügen Sie mithilfe der Schaltfläche **neue Verbindung** eine neue Verbindung hinzu.

5. Klicken Sie auf **Weiter**.

6. Deaktivieren Sie die Option zum Speichern der Verbindung, wenn Sie ausgewählt ist, und klicken Sie dann auf **weiter**.

7. Erweitern Sie den Knoten **Tabellen** im Fenster **Datenbankobjekte** .

8. Aktivieren Sie das Kontrollkästchen neben der Tabelle **Suppliers** .

9. Erweitern Sie die Tabelle **Products** , und wählen Sie **ProductName**, **SupplierID**, **QuantityPerUnit**und **UnitPrice**aus.

10. Klicken Sie auf **Fertig stellen**.

    Der Assistent fügt dem **Datenquellen** Fenster die Tabelle " **Suppliers** " und die Tabelle " **Products** " hinzu. Außerdem wird ein typisiertes DataSet zu Ihrem Projekt hinzugefügt, das in **Projektmappen-Explorer**sichtbar ist.

## <a name="add-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt
 Fügen Sie als nächstes <xref:Microsoft.Office.Tools.Excel.NamedRange> dem ersten Arbeits <xref:Microsoft.Office.Tools.Excel.ListObject> Blatt ein-Steuerelement und ein-Steuerelement hinzu.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>So fügen Sie ein Name Drange-Steuerelement und ein ListObject-Steuerelement hinzu

1. Überprüfen Sie, ob die Arbeitsmappe **Meine Excel-Aktionen Bereich. xlsx** im Visual Studio-Designer `Sheet1` geöffnet ist, und wird angezeigt.

2. Erweitern Sie im **Datenquellen** Fenster die Tabelle **Suppliers** .

3. Klicken Sie auf den Dropdown Pfeil im Knoten **Firmen Name** , und klicken Sie dann auf **NamedRange**.

4. Ziehen Sie **Company Name** aus dem **Datenquellen** Fenster in die Zelle `Sheet1` **a2** in.

     Ein <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement `CompanyNameNamedRange` mit dem Namen wird erstellt, \<und der Text CompanyName > in Zelle **a2**angezeigt. Gleichzeitig werden dem Projekt ein <xref:System.Windows.Forms.BindingSource> benannter `suppliersBindingSource`, ein Tabellen Adapter und <xref:System.Data.DataSet> ein hinzugefügt. Das-Steuerelement ist an <xref:System.Windows.Forms.BindingSource>das-Steuerelement gebunden, das wiederum <xref:System.Data.DataSet> an die-Instanz gebunden ist.

5. Scrollen Sie im Fenster **Datenquellen** nach unten zu den Spalten, die sich in der Tabelle **Suppliers** befinden. Am Ende der Liste befindet sich die Tabelle " **Products** ". Dies liegt daran, dass es sich um ein untergeordnetes Element der **Suppliers** -Tabelle handelt. Wählen Sie diese **Products** -Tabelle aus, nicht die, die sich auf derselben Ebene wie die **Suppliers** -Tabelle befindet, und klicken Sie dann auf den angezeigten Dropdown Pfeil.

6. Klicken Sie in der Dropdown Liste auf **ListObject** , und ziehen Sie dann die Tabelle **Products** in die `Sheet1`Zelle **a6** in.

     In <xref:Microsoft.Office.Tools.Excel.ListObject> der Zelle `ProductNameListObject` **a6**wird ein Steuerelement mit dem Namen erstellt. Gleichzeitig werden dem Projekt ein <xref:System.Windows.Forms.BindingSource> benannter `productsBindingSource` und ein Tabellen Adapter hinzugefügt. Das-Steuerelement ist an <xref:System.Windows.Forms.BindingSource>das-Steuerelement gebunden, das wiederum <xref:System.Data.DataSet> an die-Instanz gebunden ist.

7. Wählen C# Sie für nur in der Komponenten Leiste **SuppliersBindingSource** aus, und ändern Sie im **Eigenschaften** Fenster die Eigenschaft **modifiers** in **intern** .

## <a name="add-controls-to-the-actions-pane"></a>Hinzufügen von Steuerelementen zum Aktionsbereich
 Als nächstes benötigen Sie ein Aktionsbereich-Steuerelement mit einem Kombinations Feld.

### <a name="to-add-an-actions-pane-control"></a>So fügen Sie ein Aktionsbereich-Steuerelement hinzu

1. Wählen Sie in **Projektmappen-Explorer**das Projekt **Meine Excel-Aktions** Bereiche aus.

2. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

3. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option Aktionsbereich- **Steuer**Element aus, benennen Sie es mit " **aktionscontrol**", **und klicken Sie**auf

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>So fügen Sie einem Aktionsbereich-Steuerelement Daten gebundene Windows Forms Steuerelemente hinzu

1. Ziehen Sie ein <xref:System.Windows.Forms.ComboBox> -Steuerelement auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox**auf das Steuerelement Aktionsbereich.

2. Ändern Sie die **size** -Eigenschaft in **171, 21**.

3. Passen Sie die Größe des Benutzer Steuer Elements an das Kombinations Feld an.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Binden des Steuer Elements im Aktionsbereich an Daten
 In diesem Abschnitt legen Sie die Datenquelle von <xref:System.Windows.Forms.ComboBox> auf die gleiche Datenquelle fest wie das <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement auf dem Arbeitsblatt.

### <a name="to-set-data-binding-properties-of-the-control"></a>So legen Sie Daten Bindungseigenschaften für das Steuerelement fest

1. Klicken Sie mit der rechten Maustaste auf das Steuerelement Aktionsbereich, und klicken Sie dann auf **Code anzeigen**

2. Fügen Sie dem- <xref:System.Windows.Forms.UserControl.Load> Ereignis des Aktionsbereich-Steuer Elements den folgenden Code hinzu.

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3. In C#müssen Sie einen Ereignishandler für den `ActionsControl`erstellen. Sie können diesen Code im `ActionsControl` Konstruktor platzieren. Weitere Informationen zum Erstellen von Ereignis Handlern finden [Sie unter Gewusst wie: Erstellen von Ereignis Handlern in Office](../vsto/how-to-create-event-handlers-in-office-projects.md)-Projekten.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>Aktionsbereich anzeigen
 Der Aktionsbereich ist erst sichtbar, wenn Sie das Steuerelement zur Laufzeit hinzufügen.

#### <a name="to-show-the-actions-pane"></a>So zeigen Sie den Aktionsbereich an

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf *ThisWorkbook. vb* oder *ThisWorkbook.cs*, und klicken Sie dann auf **Code anzeigen**.

2. Erstellen Sie eine neue Instanz des Benutzer Steuer Elements in `ThisWorkbook` der-Klasse.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3. Fügen Sie im- `ThisWorkbook` EreignishandlervondemAktionsbereichdas-Steuerelementhinzu.<xref:Microsoft.Office.Tools.Excel.Workbook.Startup>

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>Testen der Anwendung
 Nun können Sie Ihr Dokument testen, um zu überprüfen, ob der Aktionsbereich geöffnet wird, wenn das Dokument geöffnet wird, und dass die Steuerelemente eine Master-/Detail-Beziehung aufweisen.

### <a name="to-test-your-document"></a>So testen Sie das Dokument

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Vergewissern Sie sich, dass der Aktionsbereich angezeigt wird.

3. Wählen Sie im Listenfeld ein Unternehmen aus. Vergewissern Sie sich, dass der Name des unter <xref:Microsoft.Office.Tools.Excel.NamedRange> nehmens im-Steuerelement aufgeführt ist und die Produkt <xref:Microsoft.Office.Tools.Excel.ListObject> Details im-Steuerelement aufgelistet sind.

4. Wählen Sie verschiedene Unternehmen aus, um die Änderung von Firmenname und Produktdetails nach Bedarf zu überprüfen.

## <a name="next-steps"></a>Nächste Schritte
 Die folgenden Aufgaben könnten sich daran anschließen:

- Binden von Daten an Steuerelemente in Word. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)-Aktionsbereich.

- Bereitstellen des Projekts. Weitere Informationen finden Sie unter Bereitstellen einer Office-Projekt Mappe [mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Siehe auch
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
- [Vorgehensweise: Verwalten des Steuerelement Layouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
