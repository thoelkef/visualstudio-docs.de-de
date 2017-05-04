---
title: "Beibehalten von dynamischen Steuerelementen in Office-Dokumenten | Microsoft Docs"
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
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Hoststeuerelemente"
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Beibehalten im Dokument"
  - "Windows Forms-Steuerelemente [Office-Entwicklung in Visual Studio], Beibehalten im Dokument"
  - "Dokumente [Office-Entwicklung in Visual Studio], Windows Forms-Steuerelemente"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Hoststeuerelemente"
  - "Hoststeuerelemente [Office-Entwicklung in Visual Studio], Beibehalten im Dokument"
ms.assetid: 200352d1-66aa-4156-9ecd-6fd8792974cd
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Beibehalten von dynamischen Steuerelementen in Office-Dokumenten
  Steuerelemente, die zur Laufzeit hinzugefügt werden, werden nicht beibehalten, wenn das Dokument oder die Arbeitsmappe gespeichert und geschlossen wird. Das genaue Verhalten unterscheidet sich für Hoststeuerelemente und Windows Forms\-Steuerelemente. In beiden Fällen können Sie der Projektmappe Code hinzufügen, damit die Steuerelemente neu erstellt werden, wenn der Benutzer das Dokument erneut öffnet.  
  
 Steuerelemente, die Sie Dokumenten zur Laufzeit hinzufügen, heißen *dynamische Steuerelemente*. Weitere Informationen zu dynamischen Steuerelementen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Beibehalten von Hoststeuerelementen im Dokument  
 Wenn ein Dokument gespeichert und anschließend geschlossen wird, werden alle dynamischen Hoststeuerelemente aus dem Dokument entfernt. Nur die zugrunde liegenden systemeigenen Office\-Objekte bleiben zurück. Angenommen, ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Hoststeuerelement wird zu einem <xref:Microsoft.Office.Interop.Excel.ListObject>. Die systemeigenen Office\-Objekte sind nicht mit den Hoststeuerelementereignissen verbunden und besitzen nicht die Datenbindungsfunktionen des Hoststeuerelements.  
  
 Die folgende Tabelle enthält die systemeigenen Office\-Objekte, die in einem Dokument für jeden Typ von Hoststeuerelement zurückbleiben.  
  
|Hoststeuerelementtyp|Typ des systemeigenen Office\-Objekts|  
|--------------------------|-------------------------------------------|  
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|  
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|  
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|  
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|  
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|  
  
### Neuerstellung von dynamischen Hoststeuerelementen beim Öffnen von Dokumenten  
 Wenn ein Benutzer ein Dokument öffnet, können anstelle von vorhandenen systemeigenen Steuerelementen dynamische Hoststeuerelemente neu erstellt werden. Durch diese Erstellung von Hoststeuerelementen beim Öffnen eines Dokuments wird das Verhalten simuliert, das der Benutzer möglicherweise erwartet.  
  
 Verwenden Sie für die Neuerstellung eines Hoststeuerelements für Word bzw. eines <xref:Microsoft.Office.Tools.Excel.NamedRange>\- oder eines <xref:Microsoft.Office.Tools.Excel.ListObject>\-Hoststeuerelements für Excel eine `Add`\<*control class*\>\-Methode eines <xref:Microsoft.Office.Tools.Excel.ControlCollection>\- oder <xref:Microsoft.Office.Tools.Word.ControlCollection>\-Objekts. Verwenden Sie eine Methode, die einen Parameter für das systemeigene Office\-Objekt hat.  
  
 Wenn Sie z. B. ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Hoststeuerelement aus einem vorhandenen systemeigenen <xref:Microsoft.Office.Interop.Excel.ListObject> erstellen möchten, wenn das Dokument geöffnet wird, verwenden Sie die <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A>\-Methode, und übergeben Sie das vorhandene <xref:Microsoft.Office.Interop.Excel.ListObject>. Im folgenden Codebeispiel wird dies für ein Projekt auf Dokumentebene für Excel veranschaulicht. Der Code erstellt ein dynamisches <xref:Microsoft.Office.Tools.Excel.ListObject> neu, das auf einem vorhandenen <xref:Microsoft.Office.Interop.Excel.ListObject> namens `MyListObject` in der `Sheet1`\-Klasse basiert.  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/CS/Sheet1.cs#6)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/VB/Sheet1.vb#6)]  
  
### Neuerstellung von Diagrammen  
 Für die Neuerstellung eines <xref:Microsoft.Office.Tools.Excel.Chart>\-Hoststeuerelements müssen Sie zunächst das systemeigene <xref:Microsoft.Office.Interop.Excel.Chart> löschen. Erstellen Sie dann das <xref:Microsoft.Office.Tools.Excel.Chart> mithilfe der <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A>\- oder <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A>\-Methode neu. Es gibt keine `Add`\<*control class*\>\-Methode, mit der Sie ein neues <xref:Microsoft.Office.Tools.Excel.Chart> auf Basis eines vorhandenen <xref:Microsoft.Office.Interop.Excel.Chart> erstellen können.  
  
 Wenn Sie das systemeigene <xref:Microsoft.Office.Interop.Excel.Chart> nicht zuerst löschen, wird ein Diagrammduplikat erstellt, wenn Sie das <xref:Microsoft.Office.Tools.Excel.Chart> erstellen.  
  
## Beibehalten von Windows Forms\-Steuerelementen in Dokumenten  
 Wenn Sie ein Dokument speichern und schließen, entfernt die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] automatisch alle dynamisch erstellten Windows Forms\-Steuerelemente aus dem Dokument. Das Verhalten unterscheidet sich jedoch für Projekte auf Dokumentebene und VSTO\-Add\-In\-Projekte.  
  
 In Anpassungen auf Dokumentebene werden die Steuerelemente und die zugrunde liegenden ActiveX\-Wrapper \(mit denen die Steuerelemente im Dokument gehostet werden\) beim nächsten Öffnen des Dokuments entfernt. Es ist nicht zu erkennen, dass die Steuerelemente jemals vorhanden waren.  
  
 In VSTO\-Add\-Ins werden die Steuerelemente entfernt, die ActiveX\-Wrapper hingegen verbleiben im Dokument. Beim nächsten Öffnen des Dokuments sind die ActiveX\-Wrapper sichtbar. In Excel zeigen die ActiveX\-Wrapper Bilder der Steuerelemente an, wie diese beim letzten Speichern des Dokuments dargestellt wurden. In Word sind die ActiveX\-Wrapper nur sichtbar, wenn der Benutzer darauf klickt. In diesem Fall wird der Rahmen eines Steuerelements als gepunktete Linie angezeigt. Es gibt mehrere Möglichkeiten, die ActiveX\-Wrapper zu entfernen. Weitere Informationen finden Sie unter [Entfernen von ActiveX\-Wrappern in einem Add\-In](#removingActiveX).  
  
### Neuerstellung von Windows Forms\-Steuerelementen beim Öffnen von Dokumenten  
 Gelöschte Windows Forms\-Steuerelemente können neu erstellt werden, wenn der Benutzer das Dokument erneut öffnet. Hierzu müssen in der Projektmappe folgende Aufgaben ausgeführt werden:  
  
1.  Informationen zu Größe, Position und Zustand der Steuerelemente müssen beim Speichern oder Schließen des Dokuments gespeichert werden. Bei einer Anpassung auf Dokumentebene können diese Daten im Datencache des Dokuments gespeichert werden. Bei einem VSTO\-Add\-In können diese Daten in einer benutzerdefinierten XML\-Komponente im Dokument gespeichert werden.  
  
2.  Die Steuerelemente werden im Falle eines Ereignisses neu erstellt, das beim Öffnen des Dokuments ausgelöst wird. Bei Projekten auf Dokumentebene können Sie dieses Verhalten im `Sheet`*n*`_Startup`\- oder `ThisDocument_Startup`\-Ereignishandler veranlassen. Bei VSTO\-Add\-In\-Projekten können Sie dieses Verhalten in den Ereignishandlern für das <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen>\- oder das <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>\-Ereignis veranlassen.  
  
###  <a name="removingActiveX"></a> Entfernen von ActiveX\-Wrappern in einem Add\-In  
 Wenn Sie Dokumenten dynamische Windows Forms\-Steuerelemente mithilfe eines VSTO\-Add\-Ins hinzufügen, können Sie verhindern, dass die ActiveX\-Wrapper für die Steuerelemente im Dokument angezeigt werden, wenn es das nächste Mal geöffnet wird. Dafür stehen folgende Möglichkeiten zur Verfügung.  
  
#### Entfernen von ActiveX\-Wrappern beim Öffnen des Dokuments  
 Rufen Sie zum Entfernen aller ActiveX\-Wrapper die GetVstoObject\-Methode auf, um ein Hostelement für <xref:Microsoft.Office.Interop.Word.Document> oder <xref:Microsoft.Office.Interop.Excel.Workbook> zu generieren, das das neu geöffnete Dokument darstellt. Beispiel: Zum Entfernen aller ActiveX\-Wrapper aus einem Word\-Dokument können Sie die GetVstoObject\-Methode aufrufen, um ein Hostelement für das <xref:Microsoft.Office.Interop.Word.Document>\-Objekt zu generieren, das an den Ereignishandler für das <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>\-Ereignis übergeben wird.  
  
 Diese Vorgehensweise ist hilfreich, wenn Sie wissen, dass das Dokument nur auf Computern geöffnet wird, auf denen das VSTO\-Add\-In installiert ist. Wenn das Dokument an andere Benutzer weitergegeben werden könnte, die das VSTO\-Add\-In nicht installiert haben, können Sie in Erwägung ziehen, die Steuerelemente vor dem Schließen des Dokuments zu entfernen.  
  
 Das folgende Codebeispiel veranschaulicht, wie die GetVstoObject\-Methode beim Öffnen des Dokuments aufgerufen wird.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#11)]
 [!code-vb[Trin_WordAddInDynamicControls#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#11)]  
  
 Obwohl die GetVstoObject\-Methode primär zum Generieren eines neuen Hostelements zur Laufzeit verwendet wird, werden mit ihr beim ersten Aufruf für ein bestimmtes Dokument auch alle ActiveX\-Wrapper aus dem Dokument entfernt. Weitere Informationen zum Verwenden der GetVstoObject\-Methode finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Wenn das VSTO\-Add\-In beim Öffnen des Dokuments dynamische Steuerelemente erstellt, ruft das VSTO\-Add\-In die GetVstoObject\-Methode bereits als Teil des Prozesses der Erstellung von Steuerelementen auf. Es ist nicht erforderlich, einen separaten Aufruf der GetVstoObject\-Methode hinzuzufügen, um in diesem Szenario ActiveX\-Wrapper zu entfernen.  
  
#### Entfernen der dynamischen Steuerelemente vor dem Schließen des Dokuments  
 Das VSTO\-Add\-In kann explizit alle dynamischen Steuerelemente aus dem Dokument entfernen, bevor das Dokument geschlossen wird. Diese Vorgehensweise ist bei Dokumenten hilfreich, die möglicherweise an andere Benutzer übergeben werden, die das VSTO\-Add\-In nicht installiert haben.  
  
 Das folgende Codebeispiel veranschaulicht das Entfernen aller Windows Forms\-Steuerelemente aus einem Word\-Dokument beim Schließen des Dokuments.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#10)]
 [!code-vb[Trin_WordAddInDynamicControls#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#10)]  
  
## Siehe auch  
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  