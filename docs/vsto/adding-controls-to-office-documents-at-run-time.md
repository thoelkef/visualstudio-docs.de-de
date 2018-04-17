---
title: Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at run time
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at run time
- helper methods [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 083af31a0a3208775ca14d4be07838f83fc8a3ee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="adding-controls-to-office-documents-at-run-time"></a>Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit
  Sie können einem Microsoft Office Word-Dokument und einer Microsoft Office Excel-Arbeitsmappe Steuerelemente zur Laufzeit hinzufügen. Sie können sie auch zur Laufzeit entfernen. Steuerelemente, die Sie zur Laufzeit hinzufügen oder entfernen, heißen *dynamische Steuerelemente*.  

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  

 In diesem Thema wird Folgendes beschrieben:  

-   [Verwalten von Steuerelementen zur Laufzeit mithilfe der Steuerelementauflistungen](#ControlsCollection).  

-   [Hinzufügen von Hoststeuerelementen zu Dokumenten](#HostControls).  

-   [Hinzufügen von Windows Forms-Steuerelementen zu Dokumenten](#WindowsForms).  

 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [wie: Hinzufügen von Steuerelementen zu einer Dokumentoberfläche zur Laufzeit?](http://go.microsoft.com/fwlink/?LinkId=132782).  

##  <a name="ControlsCollection"></a> Managing Controls at Run Time by Using the Control Collections  
 Verwenden Sie zum Hinzufügen, Abrufen oder Entfernen von Steuerelementen zur Laufzeit Hilfsmethoden der Objekte <xref:Microsoft.Office.Tools.Excel.ControlCollection> und <xref:Microsoft.Office.Tools.Word.ControlCollection> .  

 Wie Sie auf diese Objekte zugreifen, hängt vom Typ des Projekts ab, das Sie entwickeln:  

-   In einem Projekt auf Dokumentebene für Excel verwenden Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> -Eigenschaft der Klassen `Sheet1`, `Sheet2`und `Sheet3` . Weitere Informationen zu diesen Klassen finden Sie unter [Arbeitsblatthostelement](../vsto/worksheet-host-item.md).  

-   In einem Projekt auf Dokumentebene für Word verwenden Sie die <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> -Eigenschaft der `ThisDocument` -Klasse. Weitere Informationen zu dieser Klasse finden Sie unter [Dokumenthostelement](../vsto/document-host-item.md).  

-   Verwenden Sie in einem VSTO-Add-in-Projekt für Excel oder Word, die Steuerelemente-Eigenschaft von einem <xref:Microsoft.Office.Tools.Excel.Worksheet> oder <xref:Microsoft.Office.Tools.Word.Document> , die Sie zur Laufzeit generieren. Weitere Informationen zum Generieren dieser Objekte zur Laufzeit finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  

### <a name="adding-controls"></a>Hinzufügen von Steuerelementen  
 Die Typen <xref:Microsoft.Office.Tools.Excel.ControlCollection> und <xref:Microsoft.Office.Tools.Word.ControlCollection> enthalten Hilfsmethoden, mit denen Sie Dokumenten und Arbeitsblättern Hoststeuerelemente und allgemeine Windows Forms-Steuerelemente hinzufügen können. Jeder Methodenname weist folgendes Format auf `Add`*Steuerelementklasse*. Dabei ist *Steuerelementklasse* der Klassenname des Steuerelements, das Sie hinzufügen möchten. Verwenden Sie beispielsweise zum Hinzufügen eines <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelements zu Ihrem Dokument die <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> -Methode.  

 Im folgenden Codebeispiel wird in einem Projekt auf Dokumentebene für Excel ein <xref:Microsoft.Office.Tools.Excel.NamedRange> zu `Sheet1` hinzugefügt.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]  

### <a name="accessing-and-deleting-controls"></a>Zugreifen auf und Löschen von Steuerelementen  
 Können Sie die Steuerelemente-Eigenschaft von einem <xref:Microsoft.Office.Tools.Excel.Worksheet> oder <xref:Microsoft.Office.Tools.Word.Document> zu durchlaufen und alle Steuerelemente im Dokument, einschließlich der Steuerelemente, die Sie zur Entwurfszeit hinzugefügt. Steuerelemente, die zur Entwurfszeit hinzufügt werden, werden auch als *statische Steuerelemente*bezeichnet.  

 Sie können dynamische Steuerelemente durch Aufrufen der Delete-Methode des Steuerelements oder durch Aufrufen der Remove-Methode der einzelnen Steuerelemente-Auflistung entfernen. Im folgenden Codebeispiel wird die <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> -Methode verwendet, um in einem Projekt auf Dokumentebene für Excel ein <xref:Microsoft.Office.Tools.Excel.NamedRange> aus `Sheet1` zu entfernen.  

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]  

 Statische Steuerelemente können nicht zur Laufzeit entfernt werden. Wenn Sie versuchen, das Löschen oder entfernen-Methode verwenden, um ein statisches Steuerelement entfernen einer <xref:Microsoft.Office.Tools.CannotRemoveControlException> ausgelöst.  

> [!NOTE]  
>  Vermeiden Sie es, Steuerelemente im `Shutdown` -Ereignishandlerzeitraum des Dokuments programmgesteuert zu entfernen. Die Benutzeroberflächenelemente des Dokuments sind nicht mehr verfügbar, wenn das `Shutdown` -Ereignis ausgelöst wird. Wenn Sie Steuerelemente vor dem Schließen des Dokuments entfernen möchten, fügen Sie den Code dem Ereignishandler für ein anderes Ereignis hinzu, z. B. <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> oder <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> für Word oder <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>oder <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> für Excel.  

##  <a name="HostControls"></a> Adding Host Controls to Documents  
 Wenn Sie Dokumenten programmgesteuert Hoststeuerelemente hinzufügen, müssen Sie einen Namen angeben, der das Steuerelement eindeutig identifiziert, und Sie müssen angeben, wo das Steuerelement im Dokument hinzugefügt werden soll. Spezifische Anweisungen finden Sie unter den folgenden Themen:  

-   [Vorgehensweise: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)  

-   [Vorgehensweise: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  

-   [Vorgehensweise: Hinzufügen von Diagrammsteuerelementen zu Arbeitsblättern](../vsto/how-to-add-chart-controls-to-worksheets.md)  

-   [Vorgehensweise: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)  

-   [Vorgehensweise: Hinzufügen von Bookmark-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  

 Weitere Informationen zu Hoststeuerelementen finden Sie unter [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  

 Wenn ein Dokument gespeichert und anschließend geschlossen wird, werden alle dynamisch erstellten Hoststeuerelemente von ihren Ereignissen getrennt und verlieren ihre Datenbindungsfunktion. Sie können der Projektmappe Code hinzufügen, damit die Hoststeuerelemente neu erstellt werden, wenn das Dokument erneut geöffnet wird. Weitere Informationen finden Sie unter [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Für folgende Hoststeuerelemente werden keine Hilfsmethoden bereitgestellt, da diese Steuerelemente nicht programmgesteuert Dokumenten hinzugefügt werden können: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>und <xref:Microsoft.Office.Tools.Word.XMLNodes>.  

##  <a name="WindowsForms"></a> Adding Windows Forms Controls to Documents  
 Wenn Sie einem Dokument programmgesteuert ein Windows Forms-Steuerelement hinzufügen, müssen Sie die Position des Steuerelements und einen Namen angeben, der das Steuerelement eindeutig identifiziert. Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] stellt Hilfsmethoden für jedes Steuerelement bereit. Diese Methoden werden überladen, sodass Sie entweder einen Bereich oder bestimmte Koordinaten für die Position des Steuerelements übergeben können.  

 Wenn ein Dokument gespeichert und anschließend geschlossen wird, werden alle dynamisch erstellten Windows Forms-Steuerelemente aus dem Dokument entfernt. Sie können der Projektmappe Code hinzufügen, damit die Steuerelemente neu erstellt werden, wenn das Dokument erneut geöffnet wird. Wenn Sie dynamische Windows Forms-Steuerelemente erstellen, indem Sie ein VSTO-Add-In verwenden, werden die ActiveX-Wrapper für die Steuerelemente im Dokument beibehalten. Weitere Informationen finden Sie unter [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md).  

> [!NOTE]  
>  Windows Forms-Steuerelemente können geschützten Dokumenten nicht programmgesteuert hinzugefügt werden. Wenn Sie den Schutz eines Word-Dokuments oder Excel-Arbeitsblatts programmgesteuert aufheben, um ein Steuerelement hinzuzufügen, müssen Sie zusätzlichen Code zum Entfernen des ActiveX-Wrappers des Steuerelements beim Schließen des Dokuments schreiben. Der ActiveX-Wrapper des Steuerelements wird nicht automatisch aus geschützten Dokumenten gelöscht.  

### <a name="adding-custom-controls"></a>Hinzufügen von benutzerdefinierten Steuerelementen  
 Wenn Sie ein <xref:System.Windows.Forms.Control> hinzufügen möchten, das von den verfügbaren Hilfsmethoden nicht unterstützt wird, z. B. ein benutzerdefiniertes Benutzersteuerelement, verwenden Sie folgende Methoden:  

-   Verwenden Sie für Excel eine der <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> -Methoden eines <xref:Microsoft.Office.Tools.Excel.ControlCollection> -Objekts.  

-   Verwenden Sie für Word eine der <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> -Methoden eines <xref:Microsoft.Office.Tools.Word.ControlCollection> -Objekts.  

 Übergeben Sie zum Hinzufügen des Steuerelements die <xref:System.Windows.Forms.Control>, einen Speicherort für das Steuerelement und einen Namen, der die Steuerung an die Methode AddControl eindeutig identifiziert. Die AddControl-Methode gibt ein Objekt, das definiert, wie das Steuerelement mit dem Arbeitsblatt oder Dokument interagiert. Die AddControl-Methode gibt ein <xref:Microsoft.Office.Tools.Excel.ControlSite> (für Excel) oder ein <xref:Microsoft.Office.Tools.Word.ControlSite> Objekt (für Word).  

 Im folgenden Codebeispiel wird veranschaulicht, wie Sie die <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> -Methode verwenden, um ein benutzerdefiniertes Steuerelement dynamisch zu einem Arbeitsblatt in einem Excel-Projekt auf Dokumentebene hinzuzufügen. In diesem Beispiel heißt das Benutzersteuerelement `UserControl1`, und der <xref:Microsoft.Office.Interop.Excel.Range> heißt `range1`. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von einer `Sheet`*n* -Klasse im Projekt aus.  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]  

### <a name="using-members-of-custom-controls"></a>Verwenden von Membern von benutzerdefinierten Steuerelementen  
 Nach der Verwendung einer der Methoden AddControl zu einem Arbeitsblatt oder Dokument ein Steuerelement hinzufügen, können Sie jetzt über zwei verschiedene Steuerelementobjekte:  

-   das <xref:System.Windows.Forms.Control> -Objekt, das das benutzerdefinierte Steuerelement darstellt, und  

-   Das ControlSite, OLEObject-Klasse und OLEControl-Objekt, das das Steuerelement darstellt, nachdem es dem Arbeitsblatt oder Dokument hinzugefügt wurde.  

 Viele Eigenschaften und Methoden werden von diesen Steuerelementen gemeinsam verwendet. Es ist wichtig, dass Sie auf diese Member über das entsprechende Steuerelement zugreifen können:  

-   Verwenden Sie zum Zugreifen auf Member, die nur zum benutzerdefinierten Steuerelement gehören, <xref:System.Windows.Forms.Control>.  

-   Verwenden Sie zum Zugreifen auf Member, die von den Steuerelementen gemeinsam genutzt werden, die ControlSite, OLEObject-Klasse und OLEControl-Objekt.  

 Wenn Sie auf einen gemeinsam genutzten Member über das <xref:System.Windows.Forms.Control>zugreifen, schlägt dieser möglicherweise ohne Warnung oder Benachrichtigung fehl, oder es werden ungültige Ergebnisse erzeugt. Verwenden Sie immer Methoden oder Eigenschaften des ControlSite, OLEObject-Klasse und OLEControl-Objekts, wenn die Methode oder Eigenschaft, die erforderlich sind, nicht verfügbar ist. erst dann sollten Sie verweisen die <xref:System.Windows.Forms.Control>.  

 Z. B. die <xref:Microsoft.Office.Tools.Excel.ControlSite> Klasse und die <xref:System.Windows.Forms.Control> Klasse haben eine Top-Eigenschaft. Verwenden Sie zum Abrufen oder Festlegen des Abstands zwischen dem oberen Rand des Steuerelements und dem oberen Rand des Dokuments die <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> -Eigenschaft von <xref:Microsoft.Office.Tools.Excel.ControlSite>anstelle der <xref:System.Windows.Forms.Control.Top%2A> -Eigenschaft von <xref:System.Windows.Forms.Control>.  

 [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]  

## <a name="see-also"></a>Siehe auch  
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Beibehalten von dynamischen Steuerelementen in Office-Dokumenten](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Vorgehensweise: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Vorgehensweise: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Vorgehensweise: Hinzufügen von Diagrammsteuerelementen zu Arbeitsblättern](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Vorgehensweise: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Gewusst wie: Hinzufügen von Bookmark-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Windows Forms-Steuerelemente in Office-Dokumente (Übersicht)](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
