---
title: "Sp&#228;te Bindung in Office-L&#246;sungen | Microsoft Docs"
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
  - "Objekte [Office-Entwicklung in Visual Studio], Umwandlung"
  - "Typen [Office-Entwicklung in Visual Studio], Umwandlung"
  - "Automatisierung [Office-Entwicklung in Visual Studio], Umwandeln von Objekten"
  - "Umwandlung, Objekt in spezifischen Typ"
ms.assetid: 80b0d23e-df68-4ea9-a02b-238aee8ca9c0
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Sp&#228;te Bindung in Office-L&#246;sungen
  Einige Typen in den Objektmodellen der Office\-Anwendungen bieten Funktionen, die in Funktionen mit später Bindung verfügbar sind.  Von einigen Methoden und Eigenschaften können z. B. andere Typen von Objekten abhängig vom Kontext der Office\-Anwendung zurückgegeben werden, und von einigen Typen können andere Methoden oder Eigenschaften in anderen Kontexten verfügbar gemacht werden.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Für Visual Basic\-Projekte, in denen **Option Strict** aus ist und Visual C\#, damit die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] abzielen, oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] direkt mit Typen bearbeiten kann, die diese Funktionen mit später Bindung verwendet werden.  
  
## Implizite und explizite Umwandlung von Objektrückgabewerten  
 Zahlreiche Methoden und Eigenschaften in den primären Interopassemblys von Microsoft Office geben <xref:System.Object>\-Werte zurück, da sie mehrere verschiedene Objekttypen zurückgeben können.  Die <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A>\-Eigenschaft gibt z. B. ein <xref:System.Object>\-Objekt zurück, da der Rückgabewert ein <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekt oder <xref:Microsoft.Office.Interop.Excel.Chart>\-Objekt sein kann. Dies ist vom aktiven Blatt abhängig.  
  
 Wenn eine Methode oder eine Eigenschaft <xref:System.Object> zurückgibt, müssen Sie \(in Visual Basic\) das Objekt zu dem richtigen explizit konvertieren in Visual Basic\-Projekten, in denen **Option Strict** aktiviert ist.  Sie müssen explizit <xref:System.Object> Rückgabewerte in Visual Basic\-Projekten nicht umwandeln, in denen **Option Strict** deaktiviert ist.  
  
 In den meisten Fällen werden in der Referenzdokumentation die möglichen Typen des Rückgabewerts für einen Member aufgeführt, von dem ein <xref:System.Object> zurückgegeben wird.  Durch Konvertieren oder Umwandeln des Objekts wird IntelliSense für das Objekt im Code\-Editor aktiviert.  
  
 Informationen zum Konvertieren in Visual Basic finden Sie unter [Implicit and Explicit Conversions &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) und unter [CType-Funktion &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### Beispiele  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein Objekt in einen bestimmten Typ in einem Visual Basic\-Projekt umgewandelt wird, in dem **Option Strict** aktiviert ist.  In diesem Projekttyp, müssen Sie die \- Eigenschaft auf <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A><xref:Microsoft.Office.Interop.Excel.Range> explizit umwandeln.  Dieses Beispiel erfordert ein Excel\-Projekt auf Dokumentebene mit einer Arbeitsblattklasse mit dem Namen `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#9)]  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein Objekt implizit in einen bestimmten Typ in einem Visual Basic\-Projekt umgewandelt wird, in dem sich **Option Strict** außerhalb oder innerhalb eines Visual C\#\-Projekts befindet, für das als Zielversion [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] festgelegt wurde.  In diesen Projekttypen wird die <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A>\-Eigenschaft implizit in ein <xref:Microsoft.Office.Interop.Excel.Range>\-Objekt umgewandelt.  Dieses Beispiel erfordert ein Excel\-Projekt auf Dokumentebene mit einer Arbeitsblattklasse mit dem Namen `Sheet1`.  
  
 [!code-csharp[Trin_VstcoreProgramming#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#10)]
 [!code-vb[Trin_VstcoreProgramming#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#10)]  
  
## Zugreifen auf Member, die nur durch späte Bindung verfügbar sind  
 Einige Eigenschaften und Methoden in den Office\-PIAs sind nur durch späte Bindung verfügbar.  In Visual Basic\-Projekten, in denen **Option Strict** ist oder Visual C\# die projiziert, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] abzielen, können Sie die Funktionen für späte Bindung von den in diesen Sprachen verwenden, um auf spät gebundene Member zuzugreifen.  In Visual Basic\-Projekten, in denen **Option Strict** aktiviert ist, müssen Sie Reflektion verwenden, um diese Member zugreifen.  
  
### Beispiele  
 Im folgenden Codebeispiel wird veranschaulicht, wie auf spät gebundene Member in einem Visual Basic\-Projekt zugegriffen wird, in dem **Option Strict** außerhalb oder innerhalb eines Visual C\#\-Projekts liegt, für das als Zielversion [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] festgelegt wurde.  In diesem Beispiel wird auf die spät gebundene **Name**\-Eigenschaft des Dialogfelds **Datei öffnen** in Word zugegriffen.  Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse oder der `ThisAddIn`\-Klasse in einem Word\-Projekt aus.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 Das folgende Codebeispiel zeigt, wie Sie mithilfe von Reflektion, um die gleiche Aufgabe in einem Visual Basic\-Projekt zu erfüllen, in dem **Option Strict** aktiviert ist.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## Siehe auch  
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)   
 [Verwenden des Typs dynamic &#40;C&#35;-Programmierhandbuch&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflektion &#40;C&#35; und Visual Basic&#41;](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)   
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)  
  
  