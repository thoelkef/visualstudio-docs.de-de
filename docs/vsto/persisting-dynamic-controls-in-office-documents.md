---
title: Beibehalten von dynamischen Steuerelementen in Office-Dokumente
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8fd44d535cd8a9920ebc3de37d0c483a19dac8f8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976591"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Beibehalten von dynamischen Steuerelementen in Office-Dokumente

Steuerelemente, die zur Laufzeit hinzugefügt werden, werden nicht beibehalten, wenn das Dokument oder die Arbeitsmappe gespeichert und geschlossen wird. Das genaue Verhalten unterscheidet sich für Hoststeuerelemente und Windows Forms-Steuerelemente. In beiden Fällen können Sie der Projektmappe Code hinzufügen, damit die Steuerelemente neu erstellt werden, wenn der Benutzer das Dokument erneut öffnet.

Steuerelemente, die Sie Dokumenten zur Laufzeit hinzufügen, heißen *dynamische Steuerelemente*. Weitere Informationen zu dynamischen Steuerelementen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="persist-host-controls-in-the-document"></a>Beibehalten von Hoststeuerelementen im Dokument

Wenn ein Dokument gespeichert und anschließend geschlossen wird, werden alle dynamischen Hoststeuerelemente aus dem Dokument entfernt. Nur die zugrunde liegenden systemeigenen Office-Objekte bleiben zurück. Angenommen, ein <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> -Hoststeuerelement wird zu einem <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName>. Die systemeigenen Office-Objekte sind nicht mit den Hoststeuerelementereignissen verbunden und besitzen nicht die Datenbindungsfunktionen des Hoststeuerelements.

Die folgende Tabelle enthält die systemeigenen Office-Objekte, die in einem Dokument für jeden Typ von Hoststeuerelement zurückbleiben.

|Hoststeuerelementtyp|Typ des systemeigenen Office-Objekts|
|-----------------------|-------------------------------|
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|

### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>Neu erstellen von dynamischen Hoststeuerelementen beim Öffnen von Dokumenten

Wenn ein Benutzer ein Dokument öffnet, können anstelle von vorhandenen systemeigenen Steuerelementen dynamische Hoststeuerelemente neu erstellt werden. Durch diese Erstellung von Hoststeuerelementen beim Öffnen eines Dokuments wird das Verhalten simuliert, das der Benutzer möglicherweise erwartet.

Zum Neuerstellen eines Hoststeuerelements für Word oder <xref:Microsoft.Office.Tools.Excel.NamedRange> oder <xref:Microsoft.Office.Tools.Excel.ListObject> -Hoststeuerelements für Excel eine `Add` \< *Steuerelementklasse*>-Methode der ein <xref:Microsoft.Office.Tools.Excel.ControlCollection?displayProperty=fullName> oder <xref:Microsoft.Office.Tools.Word.ControlCollection?displayProperty=fullName> Objekt. Verwenden Sie eine Methode, die einen Parameter für das systemeigene Office-Objekt hat.

Wenn Sie z. B. ein <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> -Hoststeuerelement aus einem vorhandenen systemeigenen <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> erstellen möchten, wenn das Dokument geöffnet wird, verwenden Sie die <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> -Methode, und übergeben Sie das vorhandene <xref:Microsoft.Office.Interop.Excel.ListObject>. Im folgenden Codebeispiel wird dies für ein Projekt auf Dokumentebene für Excel veranschaulicht. Der Code erstellt ein dynamisches <xref:Microsoft.Office.Tools.Excel.ListObject> neu, das auf einem vorhandenen <xref:Microsoft.Office.Interop.Excel.ListObject> namens `MyListObject` in der `Sheet1` -Klasse basiert.

[!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
[!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]

### <a name="re-create-chart"></a>Diagramm neu erstellen.

Zum Neuerstellen einer <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> -Hoststeuerelements müssen Sie zunächst das systemeigene löschen <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>, und dann neu erstellen die <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> mithilfe der <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> Methode. Gibt es keine `Add` \< *Steuerelementklasse*>-Methode, die Sie zum Erstellen eines neuen kann <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> basierend auf einer vorhandenen <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>.

Wenn Sie nicht zuerst die systemeigene löschen <xref:Microsoft.Office.Interop.Excel.Chart>, und klicken Sie dann die zweites, doppelte eines Diagramms Sie beim Neuerstellen Erstellung werden der <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName>.

## <a name="persist-windows-forms-controls-in-documents"></a>Beibehalten von Windows Forms-Steuerelemente in Dokumenten

Wenn Sie ein Dokument speichern und schließen, entfernt die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] automatisch alle dynamisch erstellten Windows Forms-Steuerelemente aus dem Dokument. Das Verhalten unterscheidet sich jedoch für Projekte auf Dokumentebene und VSTO-Add-In-Projekte.

In Anpassungen auf Dokumentebene werden die Steuerelemente und die zugrunde liegenden ActiveX-Wrapper (mit denen die Steuerelemente im Dokument gehostet werden) beim nächsten Öffnen des Dokuments entfernt. Es ist nicht zu erkennen, dass die Steuerelemente jemals vorhanden waren.

In VSTO-Add-Ins werden die Steuerelemente entfernt, die ActiveX-Wrapper hingegen verbleiben im Dokument. Beim nächsten Öffnen des Dokuments sind die ActiveX-Wrapper sichtbar. In Excel zeigen die ActiveX-Wrapper Bilder der Steuerelemente an, wie diese beim letzten Speichern des Dokuments dargestellt wurden. In Word sind die ActiveX-Wrapper nur sichtbar, wenn der Benutzer darauf klickt. In diesem Fall wird der Rahmen eines Steuerelements als gepunktete Linie angezeigt. Es gibt mehrere Möglichkeiten, die ActiveX-Wrapper zu entfernen. Weitere Informationen finden Sie unter [Entfernen von ActiveX-Wrappern in einem Add-in](#removingActiveX).

### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>Windows Forms-Steuerelemente neu zu erstellen, beim Öffnen von Dokumenten

Gelöschte Windows Forms-Steuerelemente können neu erstellt werden, wenn der Benutzer das Dokument erneut öffnet. Hierzu müssen in der Projektmappe folgende Aufgaben ausgeführt werden:

1. Informationen zu Größe, Position und Zustand der Steuerelemente müssen beim Speichern oder Schließen des Dokuments gespeichert werden. In einer Anpassung auf Dokumentebene können Sie die Daten, das dem Datencache im Dokument speichern. In einem VSTO-Add-in können Sie die Daten an einen benutzerdefinierten XML-Abschnitt im Dokument speichern.

2. Die Steuerelemente werden im Falle eines Ereignisses neu erstellt, das beim Öffnen des Dokuments ausgelöst wird. Bei Projekten auf Dokumentebene können Sie dieses Verhalten im `Sheet`*n*`_Startup` - oder `ThisDocument_Startup` -Ereignishandler veranlassen. Bei VSTO-Add-In-Projekten können Sie dieses Verhalten in den Ereignishandlern für das <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> - oder das <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> -Ereignis veranlassen.

### <a name="removingActiveX"></a> Entfernen von ActiveX-Wrappern in einem Add-in

Wenn Sie Dokumenten dynamische Windows Forms-Steuerelemente mithilfe eines VSTO-Add-Ins hinzufügen, können Sie verhindern, dass die ActiveX-Wrapper für die Steuerelemente im Dokument das nächste Mal auf folgende Weise öffnen angezeigt werden.

#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>ActiveX-Wrapper zu entfernen, wenn das Dokument geöffnet ist

Rufen Sie zum Entfernen aller ActiveX-Wrapper die `GetVstoObject`-Methode auf, um ein Hostelement für <xref:Microsoft.Office.Interop.Word.Document> oder <xref:Microsoft.Office.Interop.Excel.Workbook> zu generieren, das das neu geöffnete Dokument darstellt. Beispiel: Zum Entfernen aller ActiveX-Wrapper aus einem Word-Dokument können Sie die `GetVstoObject`-Methode aufrufen, um ein Hostelement für das <xref:Microsoft.Office.Interop.Word.Document>-Objekt zu generieren, das an den Ereignishandler für das <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>-Ereignis übergeben wird.

Diese Vorgehensweise ist hilfreich, wenn Sie wissen, dass das Dokument nur auf Computern geöffnet wird, auf denen das VSTO-Add-In installiert ist. Wenn das Dokument an andere Benutzer weitergegeben werden könnte, die das VSTO-Add-In nicht installiert haben, können Sie in Erwägung ziehen, die Steuerelemente vor dem Schließen des Dokuments zu entfernen.

Das folgende Codebeispiel veranschaulicht, wie die `GetVstoObject`-Methode beim Öffnen des Dokuments aufgerufen wird.

[!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
[!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]

Obwohl die `GetVstoObject` Methode dient in erster Linie zum Generieren eines neuen Hostelements zur Laufzeit, die diese Methode löscht auch alle ActiveX-Wrapper aus dem Dokument beim ersten Aufruf ist für ein bestimmtes Dokument. Weitere Informationen zur Verwendung der `GetVstoObject` -Methode finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

Wenn Ihr VSTO-Add-in beim Öffnen des Dokuments dynamische Steuerelemente erstellt, das VSTO-Add-in bereits Ruft die `GetVstoObject` Methode als Teil des Prozesses, der die Steuerelemente erstellt werden. Es ist nicht erforderlich, einen separaten Aufruf der `GetVstoObject`-Methode hinzuzufügen, um in diesem Szenario ActiveX-Wrapper zu entfernen.

#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>Entfernen Sie die dynamischen Steuerelemente aus, bevor das Dokument geschlossen wird

Das VSTO-Add-In kann explizit alle dynamischen Steuerelemente aus dem Dokument entfernen, bevor das Dokument geschlossen wird. Diese Vorgehensweise ist bei Dokumenten hilfreich, die möglicherweise an andere Benutzer übergeben werden, die das VSTO-Add-In nicht installiert haben.

Das folgende Codebeispiel veranschaulicht das Entfernen aller Windows Forms-Steuerelemente aus einem Word-Dokument beim Schließen des Dokuments.

[!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
[!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]

## <a name="see-also"></a>Siehe auch

- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
