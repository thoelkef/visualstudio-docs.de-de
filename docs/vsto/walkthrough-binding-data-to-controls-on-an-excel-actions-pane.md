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
ms.openlocfilehash: de51ead9b3395df1c48f1340e27bd8c891a87fa4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56647006"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktionsbereich
  Diese exemplarische Vorgehensweise veranschaulicht die Datenbindung an Steuerelemente in einem Aktionsbereich in Microsoft Office Excel. Die Steuerelemente zeigen eine Master/Detail-Beziehung zwischen Tabellen in einer SQL Server-Datenbank.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

-   Hinzufügen von Steuerelementen zu einem Arbeitsblatt ein.

-   Erstellen eines Aktionsbereich-Steuerelements.

-   Hinzufügen von datengebundenen Windows Forms-Steuerelementen in einem Aktionsbereich-Steuerelement.

-   Der Bereich "Aktionen" angezeigt, wenn die Anwendung wird geöffnet.

> [!NOTE]
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

-   Zugriff auf einen Server mit der Beispieldatenbank Northwind-SQL Server.

-   Berechtigungen zum Lesen und Schreiben in SQL Server-Datenbank.

## <a name="create-the-project"></a>Erstellen eines Projekts
 Zunächst müssen Sie ein Excel-Arbeitsmappenprojekt erstellen.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1.  Erstellen Sie ein Excel-Workbook-Projekt mit dem Namen **meine Excel-Aktionsbereich**. Wählen Sie im Assistenten **ein neues Dokument erstellen**. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **meine Excel-Aktionsbereich** Projekt **Projektmappen-Explorer**.

## <a name="add-a-new-data-source-to-the-project"></a>Fügen Sie eine neue Datenquelle zum Projekt hinzu.

### <a name="to-add-a-new-data-source-to-the-project"></a>Das Projekt eine neue Datenquelle hinzu

1. Wenn die **Datenquellen** Fenster nicht angezeigt wird, zeigt es an, indem auf der Menüleiste die Optionen **Ansicht** > **Other Windows**  >   **Datenquellen**.

2. Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.

3. Wählen Sie **Datenbank** , und klicken Sie dann auf **Weiter**.

4. Wählen Sie eine Datenverbindung zur Northwind-Beispieldatenbank SQL Server, oder fügen Sie eine neue Verbindung mit der **neue Verbindung** Schaltfläche.

5. Klicken Sie auf **Weiter**.

6. Deaktivieren Sie die Option zum Speichern der Verbindung, wenn diese Option ausgewählt ist, und klicken Sie dann auf **Weiter**.

7. Erweitern Sie die **Tabellen** Knoten in der **Datenbankobjekte** Fenster.

8. Aktivieren Sie das Kontrollkästchen neben den **Lieferanten** Tabelle.

9. Erweitern Sie die **Produkte** Tabelle, und wählen Sie **ProductName**, **SupplierID**, **QuantityPerUnit**, und **UnitPrice**.

10. Klicken Sie auf **Fertig stellen**.

    Der Assistent fügt die **Lieferanten** Tabelle und **Produkte** Tabelle, auf die **Datenquellen** Fenster. Es auch ein typisiertes Dataset dem Projekt hinzugefügt, die in angezeigt wird **Projektmappen-Explorer**.

## <a name="add-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt
 Fügen Sie als Nächstes eine <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement und ein <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement, das erste Arbeitsblatt.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Zum Hinzufügen eines NamedRange-Steuerelements und einem ListObject-Steuerelement

1.  Überprüfen Sie, ob die **Mein Excel Aktionen Pane.xlsx** Arbeitsmappe geöffnet, in der Visual Studio-Designer ist mit `Sheet1` angezeigt.

2.  In der **Datenquellen** Fenster, erweitern Sie die **Lieferanten** Tabelle.

3.  Klicken Sie auf die Dropdown-Pfeil der **Firmenname** Knoten, und klicken Sie dann auf **NamedRange**.

4.  Ziehen Sie **Firmenname** aus der **Datenquellen** Fenster aus, um die Zelle **A2** in `Sheet1`.

     Ein <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement mit dem Namen `CompanyNameNamedRange` erstellt wird, und der Text \<CompanyName > wird angezeigt, in die Zelle **A2**. Zur gleichen Zeit eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `suppliersBindingSource`, ein Tabellenadapter und eine <xref:System.Data.DataSet> werden dem Projekt hinzugefügt. Das Steuerelement gebunden ist, um die <xref:System.Windows.Forms.BindingSource>, das wiederum gebunden ist die <xref:System.Data.DataSet> Instanz.

5.  In der **Datenquellen** Fenster: Bildlauf nach unten nach den Spalten, die unter der **Lieferanten** Tabelle. Wird am unteren Rand der Liste der **Produkte** Tabelle; es ist hier, da es sich um ein untergeordnetes Element des ist der **Lieferanten** Tabelle. Wählen Sie diese **Produkte** -Tabelle nicht zu derjenigen, die auf der gleichen Ebene wie die **Lieferanten** Tabelle, und klicken Sie dann auf den Dropdown-Pfeil, der angezeigt wird.

6.  Klicken Sie auf **ListObject** in der Dropdown-Liste, und ziehen Sie dann die **Produkte** Tabelle in Zelle **A6** in `Sheet1`.

     Ein <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement mit dem Namen `ProductNameListObject` ist in der Zelle erstellt **A6**. Zur gleichen Zeit eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `productsBindingSource` und Tabellenadapters zum Projekt hinzugefügt werden. Das Steuerelement gebunden ist, um die <xref:System.Windows.Forms.BindingSource>, das wiederum gebunden ist die <xref:System.Data.DataSet> Instanz.

7.  Für C# wählen Sie nur **SuppliersBindingSource** auf der Komponentenleiste, und Ändern der **Modifizierer** Eigenschaft **intern** in die **Eigenschaften**  Fenster.

## <a name="add-controls-to-the-actions-pane"></a>Hinzufügen von Steuerelementen im Aktionsbereich
 Als Nächstes benötigen Sie ein Aktionsbereich-Steuerelement, das ein Kombinationsfeld hat.

### <a name="to-add-an-actions-pane-control"></a>Hinzufügen ein Aktionsbereich-Steuerelements

1.  Wählen Sie die **meine Excel-Aktionsbereich** Projekt **Projektmappen-Explorer**.

2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

3.  In der **neues Element hinzufügen** wählen Sie im Dialogfeld **Aktionsbereich-Steuerelements**, nennen Sie sie **ActionsControl**, und klicken Sie auf **hinzufügen**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Datengebundene Windows Forms-Steuerelemente einem Aktionsbereich-Steuerelement hinzu

1.  Aus der **Standardsteuerelementen** Registerkarten der **Toolbox**, ziehen Sie eine <xref:System.Windows.Forms.ComboBox> Steuerelement, das Aktionsbereich-Steuerelement.

2.  Ändern der **Größe** Eigenschaft **171, 21**.

3.  Ändern Sie das Benutzersteuerelement im Kombinationsfeld passt die Größe.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Binden Sie das Steuerelement im Aktionsbereich an Daten
 In diesem Abschnitt legen Sie die Datenquelle die <xref:System.Windows.Forms.ComboBox> auf die gleiche Datenquelle wie die <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement auf dem Arbeitsblatt.

### <a name="to-set-data-binding-properties-of-the-control"></a>Datenbindungseigenschaften des Steuerelements festlegen

1.  Mit der rechten Maustaste in des Aktionsbereich-Steuerelements, und klicken Sie dann auf **Ansichtscode**.

2.  Fügen Sie den folgenden Code der <xref:System.Windows.Forms.UserControl.Load> Ereignis des Aktionsbereich-Steuerelements.

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3.  In C#, müssen Sie einen Ereignishandler für erstellen die `ActionsControl`. Sie können diesen Code in Platzieren der `ActionsControl` Konstruktor. Weitere Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>Zeigen Sie den Bereich "Aktionen"
 Der Bereich "Aktionen" ist nicht sichtbar, bis Sie das Steuerelement zur Laufzeit hinzufügen.

#### <a name="to-show-the-actions-pane"></a>Der Bereich "Aktionen" angezeigt.

1.  In **Projektmappen-Explorer**, mit der rechten Maustaste *ThisWorkbook.vb* oder *ThisWorkbook.cs*, und klicken Sie dann auf **Ansichtscode**.

2.  Erstellen Sie eine neue Instanz des Benutzersteuerelements in der `ThisWorkbook` Klasse.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3.  In der <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> -Ereignishandler des `ThisWorkbook`, fügen Sie das Steuerelement an den Aktionsbereich.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>Testen der Anwendung
 Jetzt können Sie das Dokument, um sicherzustellen, dass der Bereich "Aktionen", das geöffnet wird, wenn das Dokument geöffnet wird, und dass die Steuerelemente eine Master/Detail-Beziehung testen.

### <a name="to-test-your-document"></a>So testen Sie das Dokument

1.  Drücken Sie **F5** um Ihr Projekt auszuführen.

2.  Vergewissern Sie sich, dass der Bereich "Aktionen" angezeigt wird.

3.  Wählen Sie im Listenfeld ein Unternehmen ein. Stellen Sie sicher, dass der Name des Unternehmens aufgeführt ist, in der <xref:Microsoft.Office.Tools.Excel.NamedRange> Kontrolle und, dass die Produktdetails, in aufgeführt sind der <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement.

4.  Wählen Sie verschiedene Unternehmen, um zu überprüfen, ob der Firmenname und Produktdetails je nach Bedarf ändern.

## <a name="next-steps"></a>Nächste Schritte
 Die folgenden Aufgaben könnten sich daran anschließen:

-   Binden von Daten an Steuerelemente in Word. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

-   Bereitstellen des Projekts an. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Siehe auch
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
- [Vorgehensweise: Verwalten des Steuerelementlayouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
