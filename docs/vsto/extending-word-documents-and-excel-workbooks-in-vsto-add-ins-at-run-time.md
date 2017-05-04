---
title: "Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit | Microsoft Docs"
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
  - "GetVstoObject-Methode"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Hinzufügen von Steuerelementen zu Dokumenten"
  - "Hostelemente [Office-Entwicklung in Visual Studio], Erstellen zur Laufzeit in Add-Ins"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Erweitern von Word-Dokumenten"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Erweitern von Excel-Arbeitsmappen"
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Hinzufügen zur Laufzeit"
  - "HasVstoObject-Methode"
ms.assetid: c1607314-4cf8-439c-b4c5-709db8b71cff
caps.latest.revision: 61
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 60
---
# Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit
  Sie können ein VSTO\-Add\-In verwenden, um Word\-Dokumente und Excel\-Arbeitsmappen wie folgt anzupassen:  
  
-   Fügen Sie geöffneten Dokumenten oder Arbeitsblättern verwaltete Steuerelemente hinzu.  
  
-   Konvertieren Sie ein vorhandenes Listenobjekt in einem Excel\-Arbeitsblatt in ein erweitertes <xref:Microsoft.Office.Tools.Excel.ListObject>\-Element, mit dem Ereignisse verfügbar gemacht werden und das mit dem Windows Forms\-Datenbindungsmodell an Daten gebunden werden kann.  
  
-   Greifen Sie auf Ereignisse auf Anwendungsebene zu, die von Word und Excel für bestimmte Dokumente, Arbeitsmappen und Arbeitsblätter verfügbar gemacht werden.  
  
 Zum Verwenden dieser Funktionalität generieren Sie zur Laufzeit ein Objekt, mit dem das Dokument oder die Arbeitsmappe erweitert werden.  
  
 **Betrifft:** Die Informationen in diesem Thema betreffen VSTO\-Add\-In\-Projekte für die folgenden Anwendungen: Excel und Word. Weitere Informationen finden Sie unter [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).  
  
## Generieren von erweiterten Objekten in VSTO\-Add\-Ins  
 *Erweiterte Objekte* sind Instanzen von Typen, die über die Visual Studio\-Tools für Office\-Laufzeit bereitgestellt werden. Hiermit wird Objekten Funktionalität hinzugefügt, die als systemeigene Elemente im Word\- oder Excel\-Objektmodell vorhanden sind \(als *systemeigene Office\-Objekte* bezeichnet\). Verwenden Sie die GetVstoObject\-Methode, um ein erweitertes Objekt für ein Word\- oder Excel\-Objekt zu generieren. Wenn Sie die GetVstoObject\-Methode für ein bestimmtes Word\- oder Excel\-Objekt zum ersten Mal aufrufen, wird ein neues Objekt zurückgegeben, mit dem das angegebene Objekt erweitert wird. Bei jedem Aufrufen der Methode und Angeben des gleichen Word\- oder Excel\-Objekts wird dasselbe erweiterte Objekt zurückgegeben.  
  
 Der Typ des erweiterten Objekts hat den gleichen Namen wie der Typ des systemeigenen Office\-Objekts, aber der Typ wird im Namespace <xref:Microsoft.Office.Tools.Excel> oder <xref:Microsoft.Office.Tools.Word> definiert. Wenn Sie beispielsweise die GetVstoObject\-Methode zum Erweitern eines <xref:Microsoft.Office.Interop.Word.Document>\-Objekts aufrufen, gibt die Methode ein <xref:Microsoft.Office.Tools.Word.Document>\-Objekt zurück.  
  
 Die GetVstoObject\-Methoden sind hauptsächlich für die Verwendung in VSTO\-Add\-In\-Projekten vorgesehen. Sie können diese Methoden auch in Projekten auf Dokumentebene verwenden. Hierbei weisen sie aber ein anderes Verhalten und weniger Anwendungsmöglichkeiten auf.  
  
 Verwenden Sie die HasVstoObject\-Methode, um zu ermitteln, ob ein erweitertes Objekt für ein bestimmtes systemeigenes Office\-Objekt bereits generiert wurde. Weitere Informationen finden Sie unter [Ermitteln, ob ein Office\-Objekt erweitert wurde](#HasVstoObject).  
  
### Generieren von Hostelementen  
 Wenn Sie das GetVstoObject\-Element zum Erweitern eines Objekts auf Dokumentebene verwenden \(also <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet> oder <xref:Microsoft.Office.Interop.Word.Document>\), wird das zurückgegebene Objekt als *Hostelement* bezeichnet. Ein Hostelement ist ein Typ, der andere Objekte enthalten kann, z. B. andere erweiterte Objekte und Steuerelemente. Der Typ ähnelt dem entsprechenden Typ in den primären Interopassemblys von Word oder Excel, verfügt aber über zusätzliche Funktionen. Weitere Informationen zu Hostelementen finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md).  
  
 Nachdem Sie ein Hostelement generiert haben, können Sie es verwenden, um dem Dokument, der Arbeitsmappe oder dem Arbeitsblatt verwaltete Steuerelemente hinzuzufügen. Weitere Informationen finden Sie unter [Hinzufügen von verwalteten Steuerelementen zu Dokumenten und Arbeitsblättern](#AddControls).  
  
##### So generieren Sie ein Hostelement für ein Word\-Dokument  
  
-   Im folgenden Codebeispiel wird veranschaulicht, wie Sie ein Hostelement für das aktive Dokument generieren.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_WordAddInDynamicControls#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#8)]  
  
##### So generieren Sie ein Hostelement für eine Excel\-Arbeitsmappe  
  
-   Im folgenden Codebeispiel wird veranschaulicht, wie Sie ein Hostelement für die aktive Arbeitsmappe generieren.  
  
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/VB/ThisAddIn.vb#2)]  
  
##### So generieren Sie ein Hostelement für ein Excel\-Arbeitsblatt  
  
-   Im folgenden Codebeispiel wird veranschaulicht, wie Sie ein Hostelement für das aktive Arbeitsblatt in einem Projekt generieren.  
  
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/VB/ThisAddIn.vb#1)]  
  
### Generieren von ListObject\-Hoststeuerelementen  
 Wenn Sie die GetVstoObject\-Methode zum Erweitern eines <xref:Microsoft.Office.Interop.Excel.ListObject>\-Elements verwenden, gibt die Methode ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Element zurück. Das <xref:Microsoft.Office.Tools.Excel.ListObject>\-Element verfügt über alle Funktionen des ursprünglichen <xref:Microsoft.Office.Interop.Excel.ListObject>\-Elements. Es weist aber zusätzliche Funktionen auf, z. B. das Binden von Daten mit dem Windows Forms\-Datenbindungsmodell. Weitere Informationen finden Sie unter [ListObject-Steuerelement](../vsto/listobject-control.md).  
  
##### So generieren Sie ein Hoststeuerelement für ein ListObject\-Steuerelement  
  
-   Im folgenden Codebeispiel wird veranschaulicht, wie Sie ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Element für das erste <xref:Microsoft.Office.Interop.Excel.ListObject>\-Element im aktiven Arbeitsblatt eines Projekts generieren.  
  
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDynamicControls/VB/ThisAddIn.vb#3)]  
  
##  <a name="AddControls"></a> Hinzufügen von verwalteten Steuerelementen zu Dokumenten und Arbeitsblättern  
 Nach dem Generieren eines <xref:Microsoft.Office.Tools.Word.Document>\- oder <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Elements können Sie dem Dokument oder Arbeitsblatt, für das diese erweiterten Objekte stehen, Steuerelemente hinzufügen. Verwenden Sie hierzu die Controls\-Eigenschaft des <xref:Microsoft.Office.Tools.Word.Document>\- oder <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Elements. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Sie können Windows Forms\-Steuerelemente oder *Hoststeuerelemente* hinzufügen. Ein Hoststeuerelement ist ein Steuerelement, das von der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bereitgestellt wird und mit dem ein entsprechendes Steuerelement in der primären Word\- oder Excel\-Interopassembly eingeschlossen wird. Ein Hoststeuerelement macht das gesamte Verhalten des zugrunde liegenden systemeigenen Office\-Objekts verfügbar. Es löst aber auch Ereignisse aus und kann an Daten gebunden werden, indem das Windows Forms\-Datenbindungsmodell verwendet wird. Weitere Informationen finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md).  
  
> [!NOTE]  
>  Es ist nicht möglich, ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Steuerelement einem Arbeitsblatt oder ein <xref:Microsoft.Office.Tools.Word.XMLNode>\- oder <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelement einem Dokument per VSTO\-Add\-In hinzuzufügen. Diese Hoststeuerelemente können nicht programmgesteuert hinzugefügt werden. Weitere Informationen finden Sie unter [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### Beibehalten und Entfernen von Steuerelementen  
 Wenn Sie einem Dokument oder Arbeitsblatt verwaltete Steuerelemente hinzufügen, werden die Steuerelemente nicht beibehalten, wenn das Dokument gespeichert und anschließend geschlossen wird. Alle Hoststeuerelemente werden entfernt, sodass nur die zugrunde liegenden systemeigenen Office\-Objekte übrig bleiben. Beispielsweise wird ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Element zu einem <xref:Microsoft.Office.Interop.Excel.ListObject>\-Element. Außerdem werden alle Windows Forms\-Steuerelemente entfernt, aber ActiveX\-Wrapper für die Steuerelemente im Dokument bleiben erhalten. Sie müssen in Ihr VSTO\-Add\-In Code zum Bereinigen der Steuerelemente oder zum Neuerstellen der Steuerelemente beim nächsten Öffnen des Dokuments einfügen. Weitere Informationen finden Sie unter [Beibehalten von dynamischen Steuerelementen in Office-Dokumenten](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
## Zugreifen auf Ereignisse auf Anwendungsebene in Dokumenten und Arbeitsmappen  
 Einige Dokument\-, Arbeitsmappen und Arbeitsblattereignisse in systemeigenen Word\- und Excel\-Objektmodellen werden nur auf Anwendungsebene ausgelöst. Beispielsweise wird das <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>\-Ereignis ausgelöst, wenn ein Dokument in Word geöffnet wird. Dieses Ereignis ist aber in der <xref:Microsoft.Office.Interop.Word.Application>\-Klasse definiert, nicht in der <xref:Microsoft.Office.Interop.Word.Document>\-Klasse.  
  
 Wenn Sie in Ihrem VSTO\-Add\-In nur systemeigene Office\-Objekte verwenden, müssen Sie diese Ereignisse auf Anwendungsebene behandeln. Anschließend müssen Sie zusätzlichen Code schreiben, um zu ermitteln, ob das Dokument, von dem das Ereignis ausgelöst wurde, ein von Ihnen angepasstes Dokument ist. Hostelemente stellen diese Ereignisse auf Dokumentebene bereit, damit es einfacher ist, die Ereignisse für ein bestimmtes Dokument zu behandeln. Sie können ein Hostelement generieren und dann das Ereignis für dieses Hostelement behandeln.  
  
### Beispiel für die Verwendung systemeigener Word\-Objekte  
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie ein Ereignis auf Anwendungsebene für Word\-Dokumente behandeln. Mit der `CreateDocument`\-Methode wird ein neues Dokument erstellt und dann ein <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>\-Ereignishandler definiert, der verhindert, dass dieses Dokument gespeichert wird. Da dies ein Ereignis auf Anwendungsebene ist, das für das <xref:Microsoft.Office.Interop.Word.Application>\-Objekt ausgelöst wird, muss der Ereignishandler den Parameter `Doc` mit dem `document1`\-Objekt vergleichen. So kann ermittelt werden, ob `document1` für das gespeicherte Dokument steht.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#12)]
 [!code-vb[Trin_WordAddInDynamicControls#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#12)]  
  
### Beispiele, in denen ein Hostelement verwendet wird  
 In den folgenden Codebeispielen wird dieser Prozess vereinfacht, indem das <xref:Microsoft.Office.Tools.Word.Document.BeforeSave>\-Ereignis eines <xref:Microsoft.Office.Tools.Word.Document>\-Hostelements behandelt wird. Mit der `CreateDocument2`\-Methode wird in diesen Beispielen ein <xref:Microsoft.Office.Tools.Word.Document>\-Element zum Erweitern des `document2`\-Objekts generiert. Anschließend wird ein <xref:Microsoft.Office.Tools.Word.Document.BeforeSave>\-Ereignishandler definiert, mit dem verhindert wird, dass das Dokument gespeichert wird. Da dieser Ereignishandler nur aufgerufen wird, wenn `document2` gespeichert wird, kann der Ereignishandler die Speicheraktion abbrechen, ohne dass zusätzlicher Aufwand zur Überprüfung des Dokumentspeichervorgangs anfällt.  
  
 Diese Aufgabe wird im folgenden Codebeispiel veranschaulicht.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#13)]
 [!code-vb[Trin_WordAddInDynamicControls#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#13)]  
  
##  <a name="HasVstoObject"></a> Bestimmen, ob ein Office\-Objekt erweitert wurde  
 Verwenden Sie die HasVstoObject\-Methode, um zu ermitteln, ob ein erweitertes Objekt für ein bestimmtes systemeigenes Office\-Objekt bereits generiert wurde. Diese Methode gibt **true** zurück, wenn bereits ein erweitertes Objekt generiert wurde. Andernfalls wird **false** zurückgegeben.  
  
 Verwenden Sie die Globals.Factory.HasVstoMethod\-Methode. Übergeben Sie das systemeigene Word\- oder Excel\-Objekt, z. B. <xref:Microsoft.Office.Interop.Word.Document> oder <xref:Microsoft.Office.Interop.Excel.Worksheet>, das Sie für ein erweitertes Objekt testen möchten.  
  
 Die HasVstoObject\-Methode ist nützlich, falls Code nur ausgeführt werden soll, wenn ein bestimmtes Office\-Objekt über ein erweitertes Objekt verfügt. Angenommen, Sie verwenden ein Word\-VSTO\-Add\-In, mit dem das <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>\-Ereignis behandelt wird, um verwaltete Steuerelemente vor dem Speichern aus einem Dokument zu entfernen. Sie können dann mit der HasVstoObject\-Methode bestimmen, ob das Dokument erweitert wurde. Wenn das Dokument nicht erweitert wurde, kann es keine verwalteten Steuerelemente enthalten. Daher kann der Ereignishandler die Rückgabe einfach durchführen, ohne zu versuchen, Steuerelemente im Dokument zu bereinigen.  
  
## Siehe auch  
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md)  
  
  