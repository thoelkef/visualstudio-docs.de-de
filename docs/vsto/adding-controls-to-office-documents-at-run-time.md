---
title: Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at runtime
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at runtime
- helper methods [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af280d407a8453b66658ee5395a88d2b91b991b7
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="add-controls-to-office-documents-at-runtime"></a>Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit
  Sie können eine Microsoft Office Word-Dokument und Microsoft Office Excel-Arbeitsmappe zur Laufzeit Steuerelemente hinzugefügt. Sie können auch zur Laufzeit entfernen. Steuerelemente, die Sie hinzufügen oder entfernen zur Laufzeit heißen *dynamische Steuerelemente*.  

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  

 In diesem Thema wird Folgendes beschrieben:  

-   [Verwalten von Steuerelementen zur Laufzeit mithilfe der steuerelementauflistungen](#ControlsCollection).  

-   [Hinzufügen von Hoststeuerelementen zu Dokumenten](#HostControls).  

-   [Hinzufügen von Windows Forms-Steuerelementen zu Dokumenten](#WindowsForms).  

 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [wie I: Hinzufügen von Steuerelementen zu einem Dokument zur Laufzeit surface.?](http://go.microsoft.com/fwlink/?LinkId=132782).  

##  <a name="ControlsCollection"></a> Verwalten von Steuerelementen zur Laufzeit mithilfe der steuerelementauflistungen  
 Verwenden Sie zum Hinzufügen, Abrufen oder Entfernen von Steuerelementen zur Laufzeit, die Hilfsmethoden der <xref:Microsoft.Office.Tools.Excel.ControlCollection> und <xref:Microsoft.Office.Tools.Word.ControlCollection> Objekte.  

 Wie Sie auf diese Objekte zugreifen, hängt vom Typ des Projekts ab, das Sie entwickeln:  

-   In einem Projekt auf Dokumentebene für Excel verwenden Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> -Eigenschaft der Klassen `Sheet1`, `Sheet2`und `Sheet3` . Weitere Informationen zu diesen Klassen finden Sie unter [Arbeitsblatthostelement](../vsto/worksheet-host-item.md).  

-   In einem Projekt auf Dokumentebene für Word verwenden Sie die <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> -Eigenschaft der `ThisDocument` -Klasse. Weitere Informationen zu dieser Klasse finden Sie unter [Dokumenthostelement](../vsto/document-host-item.md).  

-   Verwenden Sie in einem VSTO-Add-in-Projekt für Excel oder Word, die `Controls` Eigenschaft eine <xref:Microsoft.Office.Tools.Excel.Worksheet> oder <xref:Microsoft.Office.Tools.Word.Document> , die Sie zur Laufzeit generieren. Weitere Informationen zum Generieren dieser Objekte zur Laufzeit finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  

### <a name="add-controls"></a>Hinzufügen von Steuerelementen  
 Die Typen <xref:Microsoft.Office.Tools.Excel.ControlCollection> und <xref:Microsoft.Office.Tools.Word.ControlCollection> enthalten Hilfsmethoden, mit denen Sie Dokumenten und Arbeitsblättern Hoststeuerelemente und allgemeine Windows Forms-Steuerelemente hinzufügen können. Jeder Methodenname weist folgendes Format auf `Add`*Steuerelementklasse*. Dabei ist *Steuerelementklasse* der Klassenname des Steuerelements, das Sie hinzufügen möchten. Verwenden Sie beispielsweise zum Hinzufügen eines <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelements zu Ihrem Dokument die <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> -Methode.  

 Im folgenden Codebeispiel wird in einem Projekt auf Dokumentebene für Excel ein <xref:Microsoft.Office.Tools.Excel.NamedRange> zu `Sheet1` hinzugefügt.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]  

### <a name="access-and-delete-controls"></a>Zugriff und Delete-Steuerelemente  
 Können Sie die `Controls` Eigenschaft eine <xref:Microsoft.Office.Tools.Excel.Worksheet> oder <xref:Microsoft.Office.Tools.Word.Document> zu durchlaufen und alle Steuerelemente im Dokument, einschließlich der Steuerelemente, die Sie zur Entwurfszeit hinzugefügt. Steuerelemente, die zur Entwurfszeit hinzufügt werden, werden auch als *statische Steuerelemente*bezeichnet.  

 Sie können dynamische Steuerelemente entfernen, durch Aufrufen der `Delete` Methode des Steuerelements oder durch Aufrufen der `Remove` -Methode der einzelnen Steuerelemente-Auflistung. Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> -Methode verwendet, um in einem Projekt auf Dokumentebene für Excel ein <xref:Microsoft.Office.Tools.Excel.NamedRange> aus `Sheet1` zu entfernen.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]  

 Statische Steuerelemente zur Laufzeit kann nicht entfernt werden. Wenn Sie versuchen, verwenden Sie die `Delete` oder `Remove` Methode, um ein statisches Steuerelement entfernen einer <xref:Microsoft.Office.Tools.CannotRemoveControlException> ausgelöst.  

> [!NOTE]  
>  Vermeiden Sie es, Steuerelemente im `Shutdown` -Ereignishandlerzeitraum des Dokuments programmgesteuert zu entfernen. Die Benutzeroberflächenelemente des Dokuments sind nicht mehr verfügbar, wenn das `Shutdown` -Ereignis ausgelöst wird. Wenn Sie Steuerelemente vor dem Schließen des Dokuments entfernen möchten, fügen Sie den Code dem Ereignishandler für ein anderes Ereignis hinzu, z. B. <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> oder <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> für Word oder <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>oder <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> für Excel.  

##  <a name="HostControls"></a> Hinzufügen von Hoststeuerelementen zu Dokumenten  
 Wenn Sie Dokumenten programmgesteuert Hoststeuerelemente hinzufügen, müssen Sie einen Namen angeben, der das Steuerelement eindeutig identifiziert, und Sie müssen angeben, wo das Steuerelement im Dokument hinzugefügt werden soll. Spezifische Anweisungen finden Sie unter den folgenden Themen:  

-   [Vorgehensweise: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)  

-   [Vorgehensweise: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  

-   [Vorgehensweise: Hinzufügen von Diagrammsteuerelementen zu Arbeitsblättern](../vsto/how-to-add-chart-controls-to-worksheets.md)  

-   [Vorgehensweise: Hinzufügen von Inhalten Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)  

-   [Vorgehensweise: Hinzufügen von Lesezeichen-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  

 Weitere Informationen zu Hoststeuerelementen finden Sie unter [Hostelemente und Hosten von Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md).  

 Wenn ein Dokument gespeichert und anschließend geschlossen wird, werden alle dynamisch erstellten Hoststeuerelemente von ihren Ereignissen getrennt und verlieren ihre Datenbindungsfunktion. Sie können der Projektmappe Code hinzufügen, damit die Hoststeuerelemente neu erstellt werden, wenn das Dokument erneut geöffnet wird. Weitere Informationen finden Sie unter [beibehalten von dynamische Steuerelementen in Office-Dokumente](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Für folgende Hoststeuerelemente werden keine Hilfsmethoden bereitgestellt, da diese Steuerelemente nicht programmgesteuert Dokumenten hinzugefügt werden können: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>und <xref:Microsoft.Office.Tools.Word.XMLNodes>.  

##  <a name="WindowsForms"></a> Hinzufügen von Windows Forms-Steuerelementen zu Dokumenten  
 Wenn Sie einem Dokument programmgesteuert ein Windows Forms-Steuerelement hinzufügen, müssen Sie die Position des Steuerelements und einen Namen angeben, der das Steuerelement eindeutig identifiziert. Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] stellt Hilfsmethoden für jedes Steuerelement bereit. Diese Methoden werden überladen, sodass Sie entweder einen Bereich oder bestimmte Koordinaten für die Position des Steuerelements übergeben können.  

 Wenn ein Dokument gespeichert und anschließend geschlossen wird, werden alle dynamisch erstellten Windows Forms-Steuerelemente aus dem Dokument entfernt. Sie können der Projektmappe Code hinzufügen, damit die Steuerelemente neu erstellt werden, wenn das Dokument erneut geöffnet wird. Wenn Sie dynamische Windows Forms-Steuerelemente erstellen, indem Sie ein VSTO-Add-In verwenden, werden die ActiveX-Wrapper für die Steuerelemente im Dokument beibehalten. Weitere Informationen finden Sie unter [beibehalten von dynamische Steuerelementen in Office-Dokumente](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Windows Forms-Steuerelemente können geschützten Dokumenten nicht programmgesteuert hinzugefügt werden. Wenn Sie den Schutz eines Word-Dokuments oder Excel-Arbeitsblatts programmgesteuert aufheben, um ein Steuerelement hinzuzufügen, müssen Sie zusätzlichen Code zum Entfernen des ActiveX-Wrappers des Steuerelements beim Schließen des Dokuments schreiben. Der ActiveX-Wrapper des Steuerelements wird nicht automatisch aus geschützten Dokumenten gelöscht.  

### <a name="add-custom-controls"></a>Hinzufügen von benutzerdefinierten Steuerelementen  
 Wenn Sie ein <xref:System.Windows.Forms.Control> hinzufügen möchten, das von den verfügbaren Hilfsmethoden nicht unterstützt wird, z. B. ein benutzerdefiniertes Benutzersteuerelement, verwenden Sie folgende Methoden:  

-   Verwenden Sie für Excel eine der <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> -Methoden eines <xref:Microsoft.Office.Tools.Excel.ControlCollection> -Objekts.  

-   Verwenden Sie für Word eine der <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> -Methoden eines <xref:Microsoft.Office.Tools.Word.ControlCollection> -Objekts.  

 Zum Hinzufügen des Steuerelements übergeben der <xref:System.Windows.Forms.Control>, einen Speicherort für das Steuerelement und einen Namen, der das Steuerelement eindeutig identifiziert die `AddControl` Methode. Die `AddControl` Methode gibt ein Objekt, das definiert, wie das Steuerelement mit dem Arbeitsblatt oder Dokument interagiert. Die `AddControl` Methode gibt ein <xref:Microsoft.Office.Tools.Excel.ControlSite> (für Excel) oder ein <xref:Microsoft.Office.Tools.Word.ControlSite> Objekt (für Word).  

 Im folgenden Codebeispiel wird veranschaulicht, wie Sie die <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> -Methode verwenden, um ein benutzerdefiniertes Steuerelement dynamisch zu einem Arbeitsblatt in einem Excel-Projekt auf Dokumentebene hinzuzufügen. In diesem Beispiel heißt das Benutzersteuerelement `UserControl1`, und der <xref:Microsoft.Office.Interop.Excel.Range> heißt `range1`. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von einer `Sheet`*n* -Klasse im Projekt aus.  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]  

### <a name="use-members-of-custom-controls"></a>Verwenden von Membern von benutzerdefinierten Steuerelementen  
 Nach Anwendung einer der `AddControl` Methoden zum Hinzufügen eines Steuerelements zu einem Arbeitsblatt oder Dokument, Sie jetzt haben Sie zwei verschiedene Steuerelementobjekte:  

-   das <xref:System.Windows.Forms.Control> -Objekt, das das benutzerdefinierte Steuerelement darstellt, und  

-   Die `ControlSite`, `OLEObject`, oder `OLEControl` -Objekt, das das Steuerelement darstellt, nachdem es dem Arbeitsblatt oder Dokument hinzugefügt wurde.  

 Viele Eigenschaften und Methoden werden von diesen Steuerelementen gemeinsam verwendet. Es ist wichtig, dass Sie auf diese Member über das entsprechende Steuerelement zugreifen können:  

-   Verwenden Sie zum Zugreifen auf Member, die nur zum benutzerdefinierten Steuerelement gehören, <xref:System.Windows.Forms.Control>.  

-   Verwenden Sie zum Zugreifen auf Member, die von den Steuerelementen gemeinsam genutzt werden, die `ControlSite`, `OLEObject`, oder `OLEControl` Objekt.  

 Wenn Sie auf einen gemeinsam genutzten Member über das <xref:System.Windows.Forms.Control>zugreifen, schlägt dieser möglicherweise ohne Warnung oder Benachrichtigung fehl, oder es werden ungültige Ergebnisse erzeugt. Verwenden Sie immer Methoden oder Eigenschaften der `ControlSite`, `OLEObject`, oder `OLEControl` Objekt, wenn die Methode oder Eigenschaft erforderlich ist nicht verfügbar; nur in diesem Fall sollten Sie den Verweis der <xref:System.Windows.Forms.Control>.  

 Z. B. die <xref:Microsoft.Office.Tools.Excel.ControlSite> Klasse und die <xref:System.Windows.Forms.Control> Klasse haben eine `Top` Eigenschaft. Verwenden Sie zum Abrufen oder Festlegen des Abstands zwischen dem oberen Rand des Steuerelements und dem oberen Rand des Dokuments die <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> -Eigenschaft von <xref:Microsoft.Office.Tools.Excel.ControlSite>anstelle der <xref:System.Windows.Forms.Control.Top%2A> -Eigenschaft von <xref:System.Windows.Forms.Control>.  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]  

## <a name="see-also"></a>Siehe auch  
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Beibehalten von dynamische Steuerelementen in Office-Dokumente](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Vorgehensweise: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Vorgehensweise: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Vorgehensweise: Hinzufügen von Diagrammsteuerelementen zu Arbeitsblättern](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Vorgehensweise: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Vorgehensweise: Hinzufügen von Lesezeichen-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Windows Forms-Steuerelemente in Office-Dokumente (Übersicht)](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
