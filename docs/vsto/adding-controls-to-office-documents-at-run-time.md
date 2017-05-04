---
title: "Hinzuf&#252;gen von Steuerelementen zu Office-Dokumenten zur Laufzeit | Microsoft Docs"
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
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Windows Forms-Steuerelemente"
  - "Hoststeuerelemente [Office-Entwicklung in Visual Studio], hinzufügen"
  - "Windows Forms-Steuerelemente [Office-Entwicklung in Visual Studio], Hinzufügen"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Hoststeuerelemente"
  - "Benutzerelemente [Office-Entwicklung in Visual Studio], Hinzufügen zur Laufzeit"
  - "Dokumente [Office-Entwicklung in Visual Studio], Windows Forms-Steuerelemente"
  - "Anpassungen auf Dokumentebene [Office-Entwicklung in Visual Studio], Hoststeuerelemente"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Hoststeuerelemente"
  - "Anpassungen auf Dokumentebene [Office-Entwicklung in Visual Studio], Windows Forms-Steuerelemente"
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Hinzufügen zur Laufzeit"
  - "Hilfsmethoden [Office-Entwicklung in Visual Studio]"
ms.assetid: 4f43b3eb-f0ec-44e2-9885-6ede327c6913
caps.latest.revision: 102
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 101
---
# Hinzuf&#252;gen von Steuerelementen zu Office-Dokumenten zur Laufzeit
  Sie können einem Microsoft Office Word\-Dokument und einer Microsoft Office Excel\-Arbeitsmappe Steuerelemente zur Laufzeit hinzufügen. Sie können sie auch zur Laufzeit entfernen. Steuerelemente, die Sie zur Laufzeit hinzufügen oder entfernen, heißen *dynamische Steuerelemente*.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 In diesem Thema wird Folgendes beschrieben:  
  
-   [Verwalten von Steuerelementen zur Laufzeit mithilfe der Steuerelementauflistungen](#ControlsCollection).  
  
-   [Hinzufügen von Hoststeuerelementen zu Dokumenten](#HostControls).  
  
-   [Hinzufügen von Windows Forms\-Steuerelementen zu Dokumenten](#WindowsForms).  
  
 ![Link zu Video](../vsto/media/playvideo.png "Link zu Video") Eine entsprechende Videodemo finden Sie unter [Gewusst wie: Hinzufügen von Steuerelementen zu einer Dokumentoberfläche zur Laufzeit](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="ControlsCollection"></a> Verwalten von Steuerelementen zur Laufzeit mithilfe der Steuerelementauflistungen  
 Verwenden Sie zum Hinzufügen, Abrufen oder Entfernen von Steuerelementen zur Laufzeit Hilfsmethoden der Objekte <xref:Microsoft.Office.Tools.Excel.ControlCollection> und <xref:Microsoft.Office.Tools.Word.ControlCollection>.  
  
 Wie Sie auf diese Objekte zugreifen, hängt vom Typ des Projekts ab, das Sie entwickeln:  
  
-   In einem Projekt auf Dokumentebene für Excel verwenden Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A>\-Eigenschaft der Klassen `Sheet1`, `Sheet2` und `Sheet3`. Weitere Informationen zu diesen Klassen finden Sie unter [Arbeitsblatthostelement](../vsto/worksheet-host-item.md).  
  
-   In einem Projekt auf Dokumentebene für Word verwenden Sie die <xref:Microsoft.Office.Tools.Word.Document.Controls%2A>\-Eigenschaft der `ThisDocument`\-Klasse. Weitere Information zu dieser Klasse finden Sie unter [Dokumenthostelement](../vsto/document-host-item.md).  
  
-   In einem VSTO\-Add\-In\-Projekt für Excel oder Word verwenden Sie die Controls\-Eigenschaft eines <xref:Microsoft.Office.Tools.Excel.Worksheet> oder <xref:Microsoft.Office.Tools.Word.Document> das Sie zur Laufzeit generieren. Weitere Informationen zum Generieren dieser Objekte zur Laufzeit finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### Hinzufügen von Steuerelementen  
 Die Typen <xref:Microsoft.Office.Tools.Excel.ControlCollection> und <xref:Microsoft.Office.Tools.Word.ControlCollection> enthalten Hilfsmethoden, mit denen Sie Dokumenten und Arbeitsblättern Hoststeuerelemente und allgemeine Windows Forms\-Steuerelemente hinzufügen können. Jeder Methodenname weist folgendes Format auf `Add` *Steuerelementklasse*. Dabei ist *Steuerelementklasse* der Klassenname des Steuerelements, das Sie hinzufügen möchten. Verwenden Sie beispielsweise zum Hinzufügen eines <xref:Microsoft.Office.Tools.Excel.NamedRange>Steuerelements zu Ihrem Dokument die <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A>\-Methode.  
  
 Im folgenden Codebeispiel wird in einem Projekt auf Dokumentebene für Excel ein <xref:Microsoft.Office.Tools.Excel.NamedRange> zu `Sheet1` hinzugefügt.  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/CS/ThisWorkbook.cs#3)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/VB/ThisWorkbook.vb#3)]  
  
### Zugreifen auf und Löschen von Steuerelementen  
 Sie können Sie Controls\-Eigenschaft eines <xref:Microsoft.Office.Tools.Excel.Worksheet> oder <xref:Microsoft.Office.Tools.Word.Document> verwenden, um alle Steuerelemente in Ihrem Dokument zu durchlaufen, auch die zur Entwurfszeit hinzugefügten. Steuerelemente, die zur Entwurfszeit hinzufügt werden, werden auch als *statische Steuerelemente* bezeichnet.  
  
 Sie können dynamische Steuerelemente durch Aufrufen der Delete\-Methode des Steuerelements oder durch Aufrufen der Remove\-Methode jeder Controls\-Auflistung entfernen. Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A>\-Methode verwendet, um in einem Projekt auf Dokumentebene für Excel ein <xref:Microsoft.Office.Tools.Excel.NamedRange> aus `Sheet1` zu entfernen.  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/CS/ThisWorkbook.cs#4)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/VB/ThisWorkbook.vb#4)]  
  
 Statische Steuerelemente können nicht zur Laufzeit entfernt werden. Wenn Sie versuchen, ein statisches Steuerelement mit der Delete\- oder der Remove\-Methode zu entfernen, wird eine <xref:Microsoft.Office.Tools.CannotRemoveControlException> ausgelöst.  
  
> [!NOTE]  
>  Vermeiden Sie es, Steuerelemente im `Shutdown`\-Ereignishandlerzeitraum des Dokuments programmgesteuert zu entfernen. Die Benutzeroberflächenelemente des Dokuments sind nicht mehr verfügbar, wenn das `Shutdown`\-Ereignis ausgelöst wird. Wenn Sie Steuerelemente vor dem Schließen des Dokuments entfernen möchten, fügen Sie den Code dem Ereignishandler für ein anderes Ereignis hinzu, z. B. <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> oder <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> für Word oder <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose> oder <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> für Excel.  
  
##  <a name="HostControls"></a> Hinzufügen von Hoststeuerelementen zu Dokumenten  
 Wenn Sie Dokumenten programmgesteuert Hoststeuerelemente hinzufügen, müssen Sie einen Namen angeben, der das Steuerelement eindeutig identifiziert, und Sie müssen angeben, wo das Steuerelement im Dokument hinzugefügt werden soll. Spezifische Anweisungen finden Sie unter den folgenden Themen:  
  
-   [Gewusst wie: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)  
  
-   [Gewusst wie: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  
  
-   [Gewusst wie: Hinzufügen von Diagrammsteuerelementen zu Arbeitsblättern](../vsto/how-to-add-chart-controls-to-worksheets.md)  
  
-   [Gewusst wie: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)  
  
-   [Gewusst wie: Hinzufügen von Bookmark-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  
  
 Weitere Informationen zu Hoststeuerelementen finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md).  
  
 Wenn ein Dokument gespeichert und anschließend geschlossen wird, werden alle dynamisch erstellten Hoststeuerelemente von ihren Ereignissen getrennt und verlieren ihre Datenbindungsfunktion. Sie können der Projektmappe Code hinzufügen, damit die Hoststeuerelemente neu erstellt werden, wenn das Dokument erneut geöffnet wird. Weitere Informationen finden Sie unter [Beibehalten von dynamischen Steuerelementen in Office-Dokumenten](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
> [!NOTE]  
>  Für folgende Hoststeuerelemente werden keine Hilfsmethoden bereitgestellt, da diese Steuerelemente nicht programmgesteuert Dokumenten hinzugefügt werden können: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode> und <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
##  <a name="WindowsForms"></a> Hinzufügen von Windows Forms\-Steuerelementen zu Dokumenten  
 Wenn Sie einem Dokument programmgesteuert ein Windows Forms\-Steuerelement hinzufügen, müssen Sie die Position des Steuerelements und einen Namen angeben, der das Steuerelement eindeutig identifiziert. Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] stellt Hilfsmethoden für jedes Steuerelement bereit. Diese Methoden werden überladen, sodass Sie entweder einen Bereich oder bestimmte Koordinaten für die Position des Steuerelements übergeben können.  
  
 Wenn ein Dokument gespeichert und anschließend geschlossen wird, werden alle dynamisch erstellten Windows Forms\-Steuerelemente aus dem Dokument entfernt. Sie können der Projektmappe Code hinzufügen, damit die Steuerelemente neu erstellt werden, wenn das Dokument erneut geöffnet wird. Wenn Sie dynamische Windows Forms\-Steuerelemente erstellen, indem Sie ein VSTO\-Add\-In verwenden, werden die ActiveX\-Wrapper für die Steuerelemente im Dokument beibehalten. Weitere Informationen finden Sie unter [Beibehalten von dynamischen Steuerelementen in Office-Dokumenten](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
> [!NOTE]  
>  Windows Forms\-Steuerelemente können geschützten Dokumenten nicht programmgesteuert hinzugefügt werden. Wenn Sie den Schutz eines Word\-Dokuments oder Excel\-Arbeitsblatts programmgesteuert aufheben, um ein Steuerelement hinzuzufügen, müssen Sie zusätzlichen Code zum Entfernen des ActiveX\-Wrappers des Steuerelements beim Schließen des Dokuments schreiben. Der ActiveX\-Wrapper des Steuerelements wird nicht automatisch aus geschützten Dokumenten gelöscht.  
  
### Hinzufügen von benutzerdefinierten Steuerelementen  
 Wenn Sie ein <xref:System.Windows.Forms.Control> hinzufügen möchten, das von den verfügbaren Hilfsmethoden nicht unterstützt wird, z. B. ein benutzerdefiniertes Benutzersteuerelement, verwenden Sie folgende Methoden:  
  
-   Verwenden Sie für Excel eine der <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A>\-Methoden eines <xref:Microsoft.Office.Tools.Excel.ControlCollection>\-Objekts.  
  
-   Verwenden Sie für Word eine der <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A>\-Methoden eines <xref:Microsoft.Office.Tools.Word.ControlCollection>\-Objekts.  
  
 Übergeben Sie zum Hinzufügen des Steuerelements das <xref:System.Windows.Forms.Control>, eine Position für das Steuerelement und einen Namen, der das Steuerelement eindeutig identifiziert, an die AddControl\-Methode. Die AddControl\-Methode gibt ein Objekt zurück, das definiert, wie das Steuerelement mit dem Arbeitsblatt oder dem Dokument interagiert. Die AddControl\-Methode gibt ein <xref:Microsoft.Office.Tools.Excel.ControlSite>\- \(für Excel\) oder ein <xref:Microsoft.Office.Tools.Word.ControlSite>\-Objekt \(für Word\) zurück.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie die <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A>\-Methode verwenden, um ein benutzerdefiniertes Steuerelement dynamisch zu einem Arbeitsblatt in einem Excel\-Projekt auf Dokumentebene hinzuzufügen. In diesem Beispiel heißt das Benutzersteuerelement `UserControl1`, und der <xref:Microsoft.Office.Interop.Excel.Range> heißt `range1`. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von einer `Sheet`*n*\-Klasse im Projekt aus.  
  
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#2)]
 [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#2)]  
  
### Verwenden von Membern von benutzerdefinierten Steuerelementen  
 Nachdem Sie mit einer der AddControl\-Methoden einem Arbeitsblatt oder Dokument ein Steuerelement hinzugefügt haben, verfügen Sie nun über zwei verschiedene Steuerelementobjekte:  
  
-   das <xref:System.Windows.Forms.Control>\-Objekt, das das benutzerdefinierte Steuerelement darstellt, und  
  
-   das ControlSite\-, das OLEObject oder das OLEControl\-Objekt, das das Steuerelement nach dem Hinzufügen zum Arbeitsblatt oder Dokument darstellt.  
  
 Viele Eigenschaften und Methoden werden von diesen Steuerelementen gemeinsam verwendet. Es ist wichtig, dass Sie auf diese Member über das entsprechende Steuerelement zugreifen können:  
  
-   Verwenden Sie zum Zugreifen auf Member, die nur zum benutzerdefinierten Steuerelement gehören, <xref:System.Windows.Forms.Control>.  
  
-   Verwenden Sie zum Zugreifen auf Member, die von den Steuerelementen gemeinsam genutzt werden, das ControlSite\-, das OLEObject oder das OLEControl\-Objekt.  
  
 Wenn Sie auf einen gemeinsam genutzten Member über das <xref:System.Windows.Forms.Control> zugreifen, schlägt dieser möglicherweise ohne Warnung oder Benachrichtigung fehl, oder es werden ungültige Ergebnisse erzeugt. Verwenden Sie stets Methoden oder Eigenschaften des ControlSite\-, des OLEObject\- oder des OLEControl\-Objekts, es sei denn, die benötigte Methode oder Eigenschaft ist nicht verfügbar; nur in diesem Fall sollten Sie auf <xref:System.Windows.Forms.Control> verweisen.  
  
 Sowohl die <xref:Microsoft.Office.Tools.Excel.ControlSite>\-Klasse als auch die <xref:System.Windows.Forms.Control>\-Klasse weisen eine Top\-Eigenschaft auf. Verwenden Sie zum Abrufen oder Festlegen des Abstands zwischen dem oberen Rand des Steuerelements und dem oberen Rand des Dokuments die <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A>\-Eigenschaft von <xref:Microsoft.Office.Tools.Excel.ControlSite> anstelle der <xref:System.Windows.Forms.Control.Top%2A>\-Eigenschaft von <xref:System.Windows.Forms.Control>.  
  
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#3)]
 [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#3)]  
  
## Siehe auch  
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Beibehalten von dynamischen Steuerelementen in Office-Dokumenten](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Gewusst wie: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Gewusst wie: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Gewusst wie: Hinzufügen von Diagrammsteuerelementen zu Arbeitsblättern](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Gewusst wie: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Gewusst wie: Hinzufügen von Bookmark-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Übersicht über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  