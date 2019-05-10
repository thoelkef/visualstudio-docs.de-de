---
title: Aktualisieren von Excel- und Word-Projekte, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fd80f4a72151fdebb3f0445024963a65db981e63
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436472"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aktualisieren von Excel- und Word-Projekte, die zu .NET Framework 4 oder .NET Framework 4.5 migriert werden
  Wenn Sie über ein Excel- oder Word-Projekt verfügen, das eine der folgenden Funktionen verwendet, müssen Sie den Code ändern, wenn das Zielframework in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird:

- [GetVstoObject-Methode und HasVstoObject-Methode](#GetVstoObject)

- [Generierte Klassen in Projekten auf Dokumentebene](#generatedclasses)

- [Windows Forms-Steuerelemente in Dokumenten](#winforms)

- [Ereignisse für Inhaltssteuerelemente in Word](#ccevents)

- [OLEObject-Klasse und OLEControl-Klasse](#ole)

- [Controls.Item(Object)-Eigenschaft](#itemproperty)

- [Von CollectionBase abgeleitete Auflistungen](#collections)

  Sie müssen auch entfernen, der `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` und Verweise auf die `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` Klasse aus Excel-Projekten, die zum als Zielversion neu zugewiesen werden der [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher. Visual Studio nicht für Sie dieses Attribut oder der Klassenverweis entfernt werden.

## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Entfernen des ExcelLocale1033-Attributs aus Excel-Projekten
 Die `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` wurde aus dem Bereich der Visual Studio 2010-Tools für Office-Laufzeit, die für Lösungen verwendet wird, die als Ziel entfernt die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher. Die Common Language Runtime (CLR) in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und höher übergibt immer die Gebietsschema-ID 1033 an das Excel-Objektmodell. Sie können dieses Attribut nicht mehr zum Deaktivieren dieses Verhaltens verwenden. Weitere Informationen finden Sie unter [Globalisierung und Lokalisierung von Excel-Projektmappen](../vsto/globalization-and-localization-of-excel-solutions.md).

### <a name="to-remove-the-excellocale1033attribute"></a>So entfernen Sie das ExcelLocale1033Attribute

1. Öffnen Sie den **Projektmappen-Explorer**, während das Projekt in Visual Studio geöffnet ist.

2. Doppelklicken Sie unter dem Knoten **Eigenschaften** (für C#) oder dem Knoten **Mein Projekt** (für Visual Basic) auf die Codedatei "AssemblyInfo", um diese im Code-Editor zu öffnen.

    > [!NOTE]
    > In Visual Basic-Projekten müssen Sie im **Projektmappen-Explorer** auf die Schaltfläche **Alle Dateien anzeigen** klicken, um die Codedatei "AssemblyInfo" anzuzeigen.

3. Suchen Sie nach `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute`, und entfernen Sie das Attribut aus der Datei, oder kommentieren Sie es aus.

    ```vb
    <Assembly: ExcelLocale1033Proxy(True)>
    ```

    ```csharp
    [assembly: ExcelLocale1033Proxy(true)]
    ```

## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>Entfernen eines Verweises auf die ExcelLocal1033Proxy-Klasse
 Projekte, die mithilfe von Microsoft Visual Studio 2005-Tools für Microsoft Office System erstellt wurden, instanziieren das <xref:Microsoft.Office.Interop.Excel.Application>-Objekt von Excel mithilfe der `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy`-Klasse. Diese Klasse wurde aus dem Bereich der Visual Studio 2010-Tools für Office-Laufzeit, die für Lösungen, die auf verwendet wurde entfernt die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher. Sie müssen die Codezeilen, die auf diese Klasse verweist, daher entfernen oder auskommentieren.

### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>So entfernen Sie den Verweis auf die ExcelLocal1033Proxy-Klasse

1. Öffnen Sie das Projekt in Visual Studio und dann den **Projektmappen-Explorer**.

2. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für *"ThisAddIn.cs"* (für C#) oder *"ThisAddIn.vb"* (für Visual Basic), und wählen Sie dann **Anzeigecode** .

3. Entfernen Sie im Code-Editor in der `VSTO generated code` -Region die folgende Codezeile, oder kommentieren Sie sie aus.

    ```vb
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)

    ```

    ```csharp
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);

    ```

## <a name="GetVstoObject"></a> Aktualisieren von Code, der die GetVstoObject und HasVstoObject-Methode verwendet.
 In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, sind die Methoden `GetVstoObject` oder `HasVstoObject` als Erweiterungsmethoden in einem der folgenden systemeigenen Objekte Ihres Projekts verfügbar: <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet> oder <xref:Microsoft.Office.Interop.Excel.ListObject>. Wenn Sie diese Methoden aufrufen, müssen Sie keinen Parameter übergeben. Im folgenden Codebeispiel wird veranschaulicht, der die GetVstoObject-Methode in einem Word-VSTO-Add-in zu verwenden, das .NET Framework 3.5 abzielt.

```vb
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()
```

```csharp
Microsoft.Office.Tools.Word.Document vstoDocument =
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();
```

 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, müssen Sie den Code für den Zugriff auf diese Methoden auf eine der folgenden Weisen ändern:

- In den Objekten <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>oder <xref:Microsoft.Office.Interop.Excel.ListObject> können Sie weiterhin auf diese Methoden als Erweiterungsmethoden zugreifen. Allerdings müssen Sie jetzt das von der der `Globals.Factory`-Eigenschaft zurückgegebene Objekt an diese Methoden übergeben.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);
  ```

- Alternativ können Sie auch in dem von der `Globals.Factory`-Eigenschaft zurückgegebenen Objekt auf diese Methoden zugreifen. Wenn Sie auf diese Weise auf die Methoden zugreifen, müssen Sie das systemeigene Objekt, das Sie erweitern möchten, an die Methode übergeben.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);
  ```

  Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="generatedclasses"></a> Aktualisieren von Code, der Instanzen der generierten Klassen in Projekten auf Dokumentebene verwendet
 In Projekten auf Dokumentebene, die auf .NET Framework 3.5 ausgerichtet sind, werden die generierten Klassen in Projekten von den folgenden Klassen in der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]abgeleitet:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>

- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>

- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>

  In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, sind die oben unter [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] aufgeführten Typen Schnittstellen und keine Klassen. Generierte Klassen in Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, sind von den folgenden neuen Klassen in der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]abgeleitet:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>

- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>

- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>

  Wenn der Code im Projekt auf eine Instanz einer der generierten Klassen als Basisklasse verweist, von der sie abgeleitet ist, müssen Sie den Code ändern.

  In einem Excel-Arbeitsmappenprojekt, das auf .NET Framework 3.5 ausgerichtet ist, verfügen Sie z. B. möglicherweise über eine Hilfsmethode, die einen Teil der Arbeitsvorgänge für Instanzen der generierten `Sheet`*n* -Klassen im Projekt ausführt.

```vb
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)
    ' Do something to the worksheet object.
End Sub
```

```csharp
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)
{
    // Do something to the worksheet object.
}
```

 Wenn Sie das Projekt neu auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausrichten, müssen Sie eine der folgenden Änderungen am Code vornehmen:

- Ändern Sie den Code, durch den die `DoSomethingToSheet` -Methode zum Übergeben der <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> -Eigenschaft eines <xref:Microsoft.Office.Tools.Excel.WorksheetBase> -Objekts im Projekt aufgerufen wird. Diese Eigenschaft gibt ein <xref:Microsoft.Office.Tools.Excel.Worksheet> -Objekt zurück.

    ```vb
    DoSomethingToSheet(Globals.Sheet1.Base)
    ```

    ```csharp
    DoSomethingToSheet(Globals.Sheet1.Base);
    ```

- Ändern Sie den `DoSomethingToSheet` -Methodenparameter, damit er stattdessen ein <xref:Microsoft.Office.Tools.Excel.WorksheetBase> -Objekt erwartet.

    ```vb
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)
        ' Do something to the worksheet object.
    End Sub
    ```

    ```csharp
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)
    {
        // Do something to the worksheet object.
    }
    ```

## <a name="winforms"></a> Aktualisieren von Code, der Windows Forms-Steuerelemente in Dokumenten verwendet.
 Müssen Sie hinzufügen, eine **mit** (C#) oder **Importe** -Anweisung (Visual Basic) für die <xref:Microsoft.Office.Tools.Excel> oder <xref:Microsoft.Office.Tools.Word> Namespace am Anfang jeder Codedatei, die die Steuerelemente-Eigenschaft verwendet wird, um Windows hinzufügen Forms-Steuerelemente in das Dokument oder Arbeitsblatt programmgesteuert.

 In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, werden die Methoden, durch die Windows Forms-Steuerelemente (z. B. die `AddButton`-Methode) hinzugefügt werden, in den der <xref:Microsoft.Office.Tools.Excel.ControlCollection>-Klasse und <xref:Microsoft.Office.Tools.Word.ControlCollection>-Klasse definiert.

 In Projekten der [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher, sind diese Methoden Erweiterungsmethoden, die für die Eigenschaft Steuerelemente verfügbar sind. Um diese Erweiterungsmethoden verwenden zu können, muss die Codedatei, in der Sie die Methoden verwenden, über die Anweisung **using** oder **Imports** für den Namespace <xref:Microsoft.Office.Tools.Excel> oder <xref:Microsoft.Office.Tools.Word> verfügen. Diese Anweisung wird automatisch in neuen Projekten generiert, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind. Allerdings wird die Anweisung in Projekten, die auf .NET Framework 3.5 ausgerichtet sind, nicht automatisch hinzugefügt. Sie müssen sie bei der Neuausrichtung des Projekts hinzufügen.

 Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="ccevents"></a> Aktualisieren von Code, der Word-Inhaltssteuerelementen behandelt.
 In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, werden diese Ereignisse vom generischen <xref:System.EventHandler%601> -Delegaten behandelt. In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, werden diese Ereignisse von anderen Delegaten behandelt.

 In der folgenden Tabelle sind die Ereignisse für Inhaltssteuerelemente in Word und die Delegaten aufgeführt, die in Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, mit den Ereignissen verknüpft sind.

|event|Delegat für Projekte unter [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und höher|
|-----------| - |
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|

## <a name="ole"></a> Aktualisieren von Code, der die OLEObject-Klasse und OLEControl-Klasse verwendet.
 In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, können Sie einem Dokument oder Arbeitsblatt benutzerdefinierte Steuerelemente (z. B. Windows Forms-Steuerelemente) mithilfe der Klassen `Microsoft.Office.Tools.Excel.OLEObject` und `Microsoft.Office.Tools.Word.OLEControl` hinzufügen.

 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, wurden diese Klassen durch die Schnittstellen <xref:Microsoft.Office.Tools.Excel.ControlSite> und <xref:Microsoft.Office.Tools.Word.ControlSite> ersetzt. Sie müssen den Code ändern, der auf `Microsoft.Office.Tools.Excel.OLEObject` und `Microsoft.Office.Tools.Word.OLEControl` verweist, damit er stattdessen auf <xref:Microsoft.Office.Tools.Excel.ControlSite> und <xref:Microsoft.Office.Tools.Word.ControlSite> verweist. Abgesehen von den neuen Namen verhalten sich diese Steuerelemente auf die gleiche Weise wie in Projekten, die auf .NET Framework 3.5 ausgerichtet sind.

 Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="itemproperty"></a> Aktualisieren von Code, der die Controls.Item(Object)-Eigenschaft verwendet
 In Projekten, die auf .NET Framework 3.5 abzielen, können Sie die Eigenschaft Item(Object) der Microsoft.Office.Tools.Word.Document.Controls oder `Microsoft.Office.Tools.Excel.Worksheet.Controls` -Auflistung, um zu bestimmen, ob ein Dokument oder Arbeitsblatt ein angegebenes Steuerelement verfügt.

 In Projekten der [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher, die Eigenschaft Item(Object) aus diesen Auflistungen entfernt wurde. Um zu bestimmen, ob ein Dokument oder Arbeitsblatt ein angegebenes Steuerelement enthält, verwenden Sie die Contains(System.Object)-Methode, der die <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> oder <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> Sammlung stattdessen.

 Weitere Informationen zu der Controls-Auflistung von Dokumenten und Arbeitsblättern, finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="collections"></a> Aktualisieren Sie Code, der Auflistungen verwendet, der von CollectionBase abgeleitete
 In Projekten, die auf .NET Framework 3.5 abzielen, sind mehrere Auflistungstypen der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] leiten Sie von der <xref:System.Collections.CollectionBase> Klasse, z. B. `Microsoft.Office.Tools.SmartTagCollection`, `Microsoft.Office.Tools.Excel.ControlCollection`, und `Microsoft.Office.Tools.Word.ControlCollection`.

 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, sind diese Auflistungstypen jetzt Schnittstellen, die nicht von <xref:System.Collections.CollectionBase>abgeleitet sind. Einige Member sind für diese Auflistungstypen nicht mehr verfügbar, z. B. <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A>und <xref:System.Collections.CollectionBase.InnerList%2A>.

## <a name="see-also"></a>Siehe auch
- [Migrieren von Office-Projektmappen zu .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [ContentControl-Elemente](../vsto/content-controls.md)
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
