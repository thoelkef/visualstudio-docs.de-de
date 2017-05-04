---
title: "Programmgesteuerte Einschr&#228;nkungen von Hostelementen und Hoststeuerelementen | Microsoft Docs"
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
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Hoststeuerelemente"
  - "Anwendungsentwicklung [Office-Entwicklung in Visual Studio], Hostelemente"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Hostelemente"
  - "Hostelemente [Office-Entwicklung in Visual Studio], Programmgesteuerte Einschränkungen"
  - "Excel [Office-Entwicklung in Visual Studio], Hostelemente"
  - "Hoststeuerelemente [Office-Entwicklung in Visual Studio], Erstellen"
  - "Anpassungen auf Dokumentebene [Office-Entwicklung in Visual Studio], Hoststeuerelemente"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Hoststeuerelemente"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Hoststeuerelemente"
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Hoststeuerelemente"
  - "Hoststeuerelemente [Office-Entwicklung in Visual Studio], Übergeben an Methoden und Eigenschaften"
  - "Anwendungsentwicklung [Office-Entwicklung in Visual Studio], Hoststeuerelemente"
  - "Excel [Office-Entwicklung in Visual Studio], Hoststeuerelemente"
  - "Hoststeuerelemente [Office-Entwicklung in Visual Studio], Programmgesteuerte Einschränkungen"
  - "Dokumente [Office-Entwicklung in Visual Studio], Hostelemente"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Hostelemente"
  - "Word [Office-Entwicklung in Visual Studio], Hostelemente"
  - "Anpassungen auf Dokumentebene [Office-Entwicklung in Visual Studio], Hostelemente"
  - "Word [Office-Entwicklung in Visual Studio], Hoststeuerelemente"
ms.assetid: 88487946-6f3d-4ea6-8de0-dd219b8002df
caps.latest.revision: 67
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 63
---
# Programmgesteuerte Einschr&#228;nkungen von Hostelementen und Hoststeuerelementen
  Jedes Hostelement und Hoststeuerelement ist so konzipiert, dass es sich wie ein entsprechendes systemeigenes Microsoft Office Word\- oder Microsoft Office Excel\-Objekt mit zusätzlichen Funktionen verhält. Es gibt jedoch einige grundlegende Unterschiede zwischen dem Verhalten von Hostelementen und Hoststeuerelementen und systemeigenen Office\-Objekten zur Laufzeit.  
  
 Allgemeine Informationen zu Hostelementen und Hoststeuerelementen finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Programmgesteuertes Erstellen von Hostelementen  
 Wenn Sie ein Dokument, eine Arbeitsmappe oder ein Arbeitsblatt mithilfe des Word\- oder Excel\-Objektmodells zur Laufzeit programmgesteuert erstellen, ist das Element kein Hostelement. Stattdessen ist das neue Objekt ein systemeigenes Office\-Objekt. Wenn Sie z. B. die <xref:Microsoft.Office.Interop.Word.Documents.Add%2A>\-Methode zum Erstellen eines neuen Word\-Dokuments zur Laufzeit verwenden, handelt es sich dabei um ein systemeigenes <xref:Microsoft.Office.Interop.Word.Document>\-Objekt, anstatt um ein <xref:Microsoft.Office.Tools.Word.Document>\-Hostelement. Beim Erstellen eines neuen Arbeitsblatts zur Laufzeit mithilfe der <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A>\-Methode erhalten Sie entsprechend ein systemeigenes <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekt, anstatt ein <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelement.  
  
 In Projekten auf Dokumentebene können Sie zur Laufzeit keine Hostelemente erstellen. Hostelemente können in Projekten auf Dokumentebene nur zur Entwurfszeit erstellt werden. Weitere Informationen finden Sie unter [Dokumenthostelement](../vsto/document-host-item.md), [Arbeitsmappenhostelement](../vsto/workbook-host-item.md) und [Arbeitsblatthostelement](../vsto/worksheet-host-item.md).  
  
 In VSTO\-Add\-In\-Projekten können Sie <xref:Microsoft.Office.Tools.Word.Document>\-, <xref:Microsoft.Office.Tools.Excel.Workbook>\- oder <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelemente zur Laufzeit erstellen. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Programmgesteuertes Erstellen von Hoststeuerelementen  
 Sie können Hoststeuerelemente zur Laufzeit programmgesteuert zu einem <xref:Microsoft.Office.Tools.Word.Document>\- oder <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelement hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Sie können Hoststeuerelemente nicht zu einem systemeigenen <xref:Microsoft.Office.Interop.Word.Document> oder <xref:Microsoft.Office.Interop.Excel.Worksheet> hinzufügen.  
  
> [!NOTE]  
>  Die folgenden Hoststeuerelemente können nicht programmgesteuert zu Arbeitsblättern oder Dokumenten hinzugefügt werden: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode> und <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## Grundlegendes zu Typunterschieden zwischen Hostelementen, Hoststeuerelementen und systemeigenen Office\-Objekten  
 Für jedes Hostelement und Hoststeuerelement gibt es ein zugrunde liegendes systemeigenes Microsoft Office Word\- oder Microsoft Office Excel\-Objekt. Sie mithilfe der InnerObject\-Eigenschaft des Hostelements oder Hoststeuerelements auf das zugrunde liegende Objekt zugreifen. Allerdings besteht keine Möglichkeit, ein systemeigenes Office\-Objekt in ein entsprechendes Hostelement oder Hoststeuerelement umzuwandeln. Wenn Sie versuchen, ein systemeigenes Office\-Objekt in ein Hostelement oder Hoststeuerelement umzuwandeln, wird ein <xref:System.InvalidCastException> ausgelöst.  
  
 Es gibt verschiedene Szenarien, in denen sich die Unterschiede zwischen den Typen von Hostelementen und Hoststeuerelementen sowie den zugrunde liegenden systemeigenen Office\-Objekte auf den Code auswirken können.  
  
### Übergeben von Hoststeuerelementen an Methoden und Eigenschaften  
 In Word können Sie ein Hoststeuerelement nicht an eine Methode oder Eigenschaft übergeben, die ein systemeigenes Word\-Objekt als Parameter erfordert. Sie müssen die InnerObject\-Eigenschaft des Hoststeuerelements verwenden, um das zugrunde liegende systemeigene Word\-Objekt zurückzugeben. Sie können z. B. ein <xref:Microsoft.Office.Interop.Word.Bookmark>\-Objekt an eine Methode übergeben, indem Sie die <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A>\-Eigenschaft des <xref:Microsoft.Office.Tools.Word.Bookmark>\-Hoststeuerelements an die Methode übergeben.  
  
 In Excel müssen Sie die InnerObject\-Eigenschaft des Hoststeuerelements verwenden, um das Hoststeuerelement an eine Methode oder Eigenschaft zu übergeben, wenn die Methode oder Eigenschaft das zugrunde liegende Excel\-Objekt erwartet.  
  
 Im folgenden Beispiel wird ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement erstellt und an die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>\-Methode übergeben. Der Code verwendet die <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A>\-Eigenschaft des benannten Bereichs, um das zugrunde liegende Office\-<xref:Microsoft.Office.Interop.Excel.Range> zurückzugeben, das von der <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>\-Methode benötigt wird.  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#28)]  
  
### Rückgabetypen von systemeigenen Office\-Methoden und \-Eigenschaften  
 Die meisten Methoden und Eigenschaften von Hostelementen geben das zugrunde liegende systemeigene Office\-Objekt zurück, auf dem das Hostelement basiert. Die <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A>\-Eigenschaft des <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Hoststeuerelements in Excel gibt z. B. ein <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekt anstelle eines <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelements zurück. Die <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A>\-Eigenschaft eines <xref:Microsoft.Office.Tools.Word.RichTextContentControl>\-Hoststeuerelements in Word gibt entsprechend ein <xref:Microsoft.Office.Interop.Word.Document>\-Objekt anstelle eines <xref:Microsoft.Office.Tools.Word.Document>\-Hostelements zurück.  
  
### Zugreifen auf Auflistungen von Hoststeuerelementen  
 Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bietet für die einzelnen Hoststeuerelementtypen keine individuellen Auflistungen. Verwenden Sie stattdessen die Controls\-Eigenschaft eines Hostelements zum Durchlaufen aller verwalteten Steuerelemente \(sowohl Hoststeuerelemente als auch Windows Forms\-Steuerelemente\) im Dokument oder Arbeitsblatt, und suchen Sie dann nach Elementen, die dem Typ des gewünschten Hoststeuerelements entsprechen. Im folgenden Codebeispiel wird jedes Steuerelement in einem Word\-Dokument untersucht und dann bestimmt, ob das Steuerelement ein <xref:Microsoft.Office.Tools.Word.Bookmark> ist.  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#10)]  
  
 Weitere Informationen zur Controls\-Eigenschaft von Hostelementen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Die Objektmodelle von Word und Excel enthalten Eigenschaften, die Auflistungen von systemeigenen Steuerelementen für Dokumente und Arbeitsblätter bereitstellen. Sie können mithilfe dieser Eigenschaften nicht auf verwaltete Steuerelemente zugreifen. Es ist z. B. nicht möglich, jedes <xref:Microsoft.Office.Tools.Word.Bookmark>\-Hoststeuerelement in einem Dokument mithilfe der <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A>\-Eigenschaft einer <xref:Microsoft.Office.Interop.Word.Document>\- oder <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A>\-Eigenschaft eines <xref:Microsoft.Office.Tools.Word.Document> aufzuzählen. Diese Eigenschaften beziehen nur die <xref:Microsoft.Office.Interop.Word.Bookmark>\-Steuerelemente im Dokument ein. Sie enthalten nicht die <xref:Microsoft.Office.Tools.Word.Bookmark>\-Hoststeuerelemente im Dokument.  
  
## Siehe auch  
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Arbeitsblatthostelement](../vsto/worksheet-host-item.md)   
 [Arbeitsmappenhostelement](../vsto/workbook-host-item.md)   
 [Dokumenthostelement](../vsto/document-host-item.md)  
  
  