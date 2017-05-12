---
title: "Aktualisieren von Excel- und Word-Projekten, die zu .NET Framework&#160;4 oder .NET Framework 4.5 migriert werden | Microsoft Docs"
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
  - "Office-Projekte [Office-Entwicklung in Visual Studio], Migrieren zu .NET Framework 4"
ms.assetid: 282c8876-fd49-462e-875b-4a0a79ad951c
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Aktualisieren von Excel- und Word-Projekten, die zu .NET Framework&#160;4 oder .NET Framework 4.5 migriert werden
  Wenn Sie über ein Excel\- oder Word\-Projekt verfügen, das eine der folgenden Funktionen verwendet, müssen Sie den Code ändern, wenn das Zielframework in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird:  
  
-   [GetVstoObject\-Methode und HasVstoObject\-Methode](#GetVstoObject)  
  
-   [Generierte Klassen in Projekten auf Dokumentebene](#generatedclasses)  
  
-   [Windows Forms\-Steuerelemente in Dokumenten](#winforms)  
  
-   [Ereignisse für Inhaltssteuerelemente in Word](#ccevents)  
  
-   [OLEObject\-Klasse und OLEControl\-Klasse](#ole)  
  
-   [Controls.Item\(Object\)\-Eigenschaft](#itemproperty)  
  
-   [Von CollectionBase abgeleitete Auflistungen](#collections)  
  
 Außerdem müssen Sie das Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute und Verweise auf die Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy\-Klasse aus Excel\-Projekten entfernen, die neu auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet werden. Dieses Attribut oder der Klassenverweis wird von Visual Studio nicht für Sie entfernt.  
  
## Entfernen des ExcelLocale1033\-Attributs aus Excel\-Projekten  
 Das Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute wurde aus der Komponente der Visual Studio 2010\-Tools für Office\-Laufzeit entfernt, die für Projektmappen verwendet wird, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind. Die Common Language Runtime \(CLR\) in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und höher übergibt immer die Gebietsschema\-ID 1033 an das Excel\-Objektmodell. Sie können dieses Attribut nicht mehr zum Deaktivieren dieses Verhaltens verwenden. Weitere Informationen finden Sie unter [Globalisierung und Lokalisierung von Excel-Lösungen](../vsto/globalization-and-localization-of-excel-solutions.md).  
  
#### So entfernen Sie das ExcelLocale1033Attribute  
  
1.  Öffnen Sie den **Projektmappen\-Explorer**, während das Projekt in Visual Studio geöffnet ist.  
  
2.  Doppelklicken Sie unter dem Knoten **Eigenschaften** \(für C\#\) oder dem Knoten **Mein Projekt** \(für Visual Basic\) auf die Codedatei "AssemblyInfo", um diese im Code\-Editor zu öffnen.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten müssen Sie im **Projektmappen\-Explorer** auf die Schaltfläche **Alle Dateien anzeigen** klicken, um die Codedatei "AssemblyInfo" anzuzeigen.  
  
3.  Suchen Sie nach Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute, und entfernen Sie das Attribut aus der Datei, oder kommentieren Sie es aus.  
  
    ```vb  
    <Assembly: ExcelLocale1033Proxy(True)>  
    ```  
  
    ```csharp  
    [assembly: ExcelLocale1033Proxy(true)]  
    ```  
  
## Entfernen eines Verweises auf die ExcelLocal1033Proxy\-Klasse  
 Projekte, die mithilfe von Microsoft Visual Studio 2005\-Tools für Microsoft Office System erstellt wurden, instanziieren das <xref:Microsoft.Office.Interop.Excel.Application>\-Objekt von Excel mithilfe der Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy\-Klasse. Diese Klasse wurde aus der Komponente der Visual Studio 2010\-Tools für Office\-Laufzeit entfernt, die für Projektmappen verwendet wird, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind. Sie müssen die Codezeilen, die auf diese Klasse verweist, daher entfernen oder auskommentieren.  
  
#### So entfernen Sie den Verweis auf die ExcelLocal1033Proxy\-Klasse  
  
1.  Öffnen Sie das Projekt in Visual Studio und dann den **Projektmappen\-Explorer**.  
  
2.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für ThisAddin.cs \(C\#\) oder ThisAddin.vb \(Visual Basic\), und wählen Sie dann **Code anzeigen** aus.  
  
3.  Entfernen Sie im Code\-Editor in der `VSTO generated code`\-Region die folgende Codezeile, oder kommentieren Sie sie aus.  
  
    ```vb  
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)  
  
    ```  
  
    ```csharp  
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);  
  
    ```  
  
##  <a name="GetVstoObject"></a> Aktualisieren von Code, der die GetVstoObject\-Methode und HasVstoObject\-Methode verwendet  
 In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, sind die Methoden GetVstoObject oder HasVstoObject als Erweiterungsmethoden in einem der folgenden systemeigenen Objekte Ihres Projekts verfügbar: <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet> oder <xref:Microsoft.Office.Interop.Excel.ListObject>. Wenn Sie diese Methoden aufrufen, müssen Sie keinen Parameter übergeben. Im folgenden Codebeispiel wird veranschaulicht, wie Sie die GetVstoObject\-Methode in einem Word VSTO\-Add\-In verwenden, das auf .NET Framework 3.5 ausgerichtet ist.  
  
```vb  
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _ Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()  
```  
  
```csharp  
Microsoft.Office.Tools.Word.Document vstoDocument = Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();  
```  
  
 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, müssen Sie den Code für den Zugriff auf diese Methoden auf eine der folgenden Weisen ändern:  
  
-   In den Objekten <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet> oder <xref:Microsoft.Office.Interop.Excel.ListObject> können Sie weiterhin auf diese Methoden als Erweiterungsmethoden zugreifen. Allerdings müssen Sie jetzt das von der der Globals.Factory\-Eigenschaft zurückgegebene Objekt an diese Methoden übergeben.  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _ Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument = Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);  
    ```  
  
-   Alternativ können Sie auch in dem von der Globals.Factory\-Eigenschaft zurückgegebenen Objekt auf diese Methoden zugreifen. Wenn Sie auf diese Weise auf die Methoden zugreifen, müssen Sie das systemeigene Objekt, das Sie erweitern möchten, an die Methode übergeben.  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _ Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument = Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);  
    ```  
  
 Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
##  <a name="generatedclasses"></a> Aktualisieren von Code, der Instanzen der generierten Klassen in Projekten auf Dokumentebene verwendet  
 In Projekten auf Dokumentebene, die auf .NET Framework 3.5 ausgerichtet sind, werden die generierten Klassen in Projekten von den folgenden Klassen in der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] abgeleitet:  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, sind die oben unter [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] aufgeführten Typen Schnittstellen und keine Klassen. Generierte Klassen in Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, sind von den folgenden neuen Klassen in der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] abgeleitet:  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>  
  
 Wenn der Code im Projekt auf eine Instanz einer der generierten Klassen als Basisklasse verweist, von der sie abgeleitet ist, müssen Sie den Code ändern.  
  
 In einem Excel\-Arbeitsmappenprojekt, das auf .NET Framework 3.5 ausgerichtet ist, verfügen Sie z. B. möglicherweise über eine Hilfsmethode, die einen Teil der Arbeitsvorgänge für Instanzen der generierten `Sheet`*n*\-Klassen im Projekt ausführt.  
  
```vb  
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet) ' Do something to the worksheet object. End Sub  
```  
  
```csharp  
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet) { // Do something to the worksheet object. }  
```  
  
 Wenn Sie das Projekt neu auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausrichten, müssen Sie eine der folgenden Änderungen am Code vornehmen:  
  
-   Ändern Sie den Code, durch den die `DoSomethingToSheet`\-Methode zum Übergeben der <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A>\-Eigenschaft eines <xref:Microsoft.Office.Tools.Excel.WorksheetBase>\-Objekts im Projekt aufgerufen wird. Diese Eigenschaft gibt ein <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Objekt zurück.  
  
    ```vb  
    DoSomethingToSheet(Globals.Sheet1.Base)  
    ```  
  
    ```csharp  
    DoSomethingToSheet(Globals.Sheet1.Base);  
    ```  
  
-   Ändern Sie den `DoSomethingToSheet`\-Methodenparameter, damit er stattdessen ein <xref:Microsoft.Office.Tools.Excel.WorksheetBase>\-Objekt erwartet.  
  
    ```vb  
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase) ' Do something to the worksheet object. End Sub  
    ```  
  
    ```csharp  
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet) { // Do something to the worksheet object. }  
    ```  
  
##  <a name="winforms"></a> Aktualisieren von Code, der Windows Forms\-Steuerelemente in Dokumenten verwendet  
 Sie müssen eine **using**\- \(C\#\) oder **Imports**\-Anweisung \(Visual Basic\) für den <xref:Microsoft.Office.Tools.Excel>\-Namespace oder <xref:Microsoft.Office.Tools.Word>\-Namespace am Anfang jeder Codedatei hinzufügen, die die Controls\-Eigenschaft verwendet, um dem Dokument oder Arbeitsblatt Windows Forms\-Steuerelemente programmgesteuert hinzuzufügen.  
  
 In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, werden die Methoden, durch die Windows Forms\-Steuerelemente \(z. B. die AddButton\-Methode\) hinzugefügt werden, in den der <xref:Microsoft.Office.Tools.Excel.ControlCollection>\-Klasse und <xref:Microsoft.Office.Tools.Word.ControlCollection>\-Klasse definiert.  
  
 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, sind diese Methoden Erweiterungsmethoden, die für die Controls\-Eigenschaft verfügbar sind. Um diese Erweiterungsmethoden verwenden zu können, muss die Codedatei, in der Sie die Methoden verwenden, über die Anweisung **using** oder **Imports** für den Namespace <xref:Microsoft.Office.Tools.Excel> oder <xref:Microsoft.Office.Tools.Word> verfügen. Diese Anweisung wird automatisch in neuen Projekten generiert, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind. Allerdings wird die Anweisung in Projekten, die auf .NET Framework 3.5 ausgerichtet sind, nicht automatisch hinzugefügt. Sie müssen sie bei der Neuausrichtung des Projekts hinzufügen.  
  
 Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="ccevents"></a> Aktualisieren von Code für die Ereignisbehandlung von Inhaltssteuerelementen in Word  
 In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, werden diese Ereignisse vom generischen <xref:System.EventHandler%601>\-Delegaten behandelt. In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, werden diese Ereignisse von anderen Delegaten behandelt.  
  
 In der folgenden Tabelle sind die Ereignisse für Inhaltssteuerelemente in Word und die Delegaten aufgeführt, die in Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, mit den Ereignissen verknüpft sind.  
  
|Ereignis|Delegat für Projekte unter [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und höher|  
|--------------|--------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|  
  
##  <a name="ole"></a> Aktualisieren von Code, der die OLEObject\- Klasse und die OLEControl\-Klasse verwendet.  
 In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, können Sie einem Dokument oder Arbeitsblatt benutzerdefinierte Steuerelemente \(z. B. Windows Forms\-Steuerelemente\) mithilfe der Klassen Microsoft.Office.Tools.Excel.OLEObject und Microsoft.Office.Tools.Word.OLEControl hinzufügen.  
  
 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, wurden diese Klassen durch die Schnittstellen <xref:Microsoft.Office.Tools.Excel.ControlSite> und <xref:Microsoft.Office.Tools.Word.ControlSite> ersetzt. Sie müssen den Code ändern, der auf Microsoft.Office.Tools.Excel.OLEObject und Microsoft.Office.Tools.Word.OLEControl verweist, damit er stattdessen auf <xref:Microsoft.Office.Tools.Excel.ControlSite> und <xref:Microsoft.Office.Tools.Word.ControlSite> verweist. Abgesehen von den neuen Namen verhalten sich diese Steuerelemente auf die gleiche Weise wie in Projekten, die auf .NET Framework 3.5 ausgerichtet sind.  
  
 Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="itemproperty"></a> Aktualisieren von Code, der die Controls.Item\(Object\)\-Eigenschaft verwendet  
 In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, können Sie mithilfe der Item\(Object\)\-Eigenschaft der Auflistungen Microsoft.Office.Tools.Word.Document.Controls oder Microsoft.Office.Tools.Excel.Worksheet.Controls festlegen, ob ein Dokument oder Arbeitsblatt über ein angegebenes Steuerelement verfügt.  
  
 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, wurde die Item\(Object\)\-Eigenschaft aus diesen Auflistungen entfernt. Um zu bestimmen, ob ein Dokument oder Arbeitsblatt ein angegebenes Steuerelement enthält, verwenden Sie stattdessen die Contains\(System.Object\)\-Methode der Auflistung <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> oder <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A>.  
  
 Weitere Informationen zur Controls\-Auflistung von Dokumenten und Arbeitsblättern finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="collections"></a> Aktualisieren von Code, der von CollectionBase abgeleitete Auflistungen verwendet  
 In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, sind mehrere Auflistungstypen in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] von der <xref:System.Collections.CollectionBase>\-Klasse abgeleitet, z. B. Microsoft.Office.Tools.SmartTagCollection, Microsoft.Office.Tools.Excel.ControlCollection und Microsoft.Office.Tools.Word.ControlCollection.  
  
 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, sind diese Auflistungstypen jetzt Schnittstellen, die nicht von <xref:System.Collections.CollectionBase> abgeleitet sind. Einige Member sind für diese Auflistungstypen nicht mehr verfügbar, z. B. <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A> und <xref:System.Collections.CollectionBase.InnerList%2A>.  
  
## Siehe auch  
 [Migrieren von Office-Projektmappen in .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Inhaltssteuerelemente](../vsto/content-controls.md)   
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)  
  
  