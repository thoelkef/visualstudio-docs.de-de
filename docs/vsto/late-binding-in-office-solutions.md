---
title: Späte Bindung in Office-Projektmappen
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5616ce958747f90c8015df858f657299ba52852b
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572549"
---
# <a name="late-binding-in-office-solutions"></a>Späte Bindung in Office-Projektmappen
  Einige Typen in den Objektmodellen von Office-Anwendungen bieten Funktionen, die über spätes Binden Funktionen verfügbar sind. Z. B. einige Methoden und Eigenschaften können verschiedene Typen von Objekten abhängig vom Kontext der Office-Anwendung zurückgeben, und einige Typen können andere Methoden oder Eigenschaften in unterschiedlichen Kontexten verfügbar machen.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual Basic-Projekte, in denen **Option Strict** deaktiviert ist, und Visual C#-Projekte, die auf die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] können arbeiten direkt mit Typen, die diese Funktionen mit später Bindung verwendet.  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Implizite und explizite Umwandlung eines Objekts geben Werte zurück.  
 Zahlreiche Methoden und Eigenschaften in das Zurückgeben von primären Interopassemblys (PIAs) für Microsoft Office <xref:System.Object> Werte, da sie mehrere verschiedene Objekttypen zurückgeben können. Z. B. die <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> -Eigenschaft gibt ein <xref:System.Object> da ihres Rückgabewerts sein kann eine <xref:Microsoft.Office.Interop.Excel.Worksheet> oder <xref:Microsoft.Office.Interop.Excel.Chart> -Objekt, je nachdem, was das aktive Blatt wird.  
  
 Wenn eine Methode oder Eigenschaft gibt eine <xref:System.Object>, müssen explizit konvertiert (in Visual Basic) des Objekts in den richtigen Typ in Visual Basic-Projekte, in denen **Option Strict** befindet sich auf. Sie müssen nicht explizit umgewandelt <xref:System.Object> Rückgabewerte in Visual Basic-Projekte, in denen **Option Strict** ist deaktiviert.  
  
 In den meisten Fällen führt die Referenzdokumentation die möglichen Typen des Rückgabewerts für ein Element, das gibt eine <xref:System.Object>. Konvertieren oder Umwandeln des Objekts können IntelliSense für das Objekt im Code-Editor ein.  
  
 Informationen zum Konvertieren in Visual Basic finden Sie unter [implizite und explizite Konvertierungen &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) und [CType-Funktion &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### <a name="examples"></a>Beispiele  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein Objekt für einen bestimmten Typ in einem Visual Basic-Projekt umgewandelt, in denen **Option Strict** befindet sich auf. Bei dieser Art des Projekts, müssen Sie explizit eine Umwandlung der <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> Eigenschaft, um eine <xref:Microsoft.Office.Interop.Excel.Range>. Dieses Beispiel benötigen Sie ein Excel-Projekt auf Dokumentebene mit einer Arbeitsblattklasse mit dem Namen `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein Objekt für einen bestimmten Typ in einem Visual Basic-Projekt implizit umgewandelt, in denen **Option Strict** ist ausgeschaltet oder in einem Visual C#-Projekt, das als Ziel verwendet die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. In diesen Typen von Projekten die <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> Eigenschaft wird implizit umgewandelt in ein <xref:Microsoft.Office.Interop.Excel.Range>. Dieses Beispiel benötigen Sie ein Excel-Projekt auf Dokumentebene mit einer Arbeitsblattklasse mit dem Namen `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="access-members-that-are-available-only-through-late-binding"></a>Auf Member zuzugreifen, die nur durch späte Bindung verfügbar sind  
 Einige Eigenschaften und Methoden in den Office-PIAs sind nur über spätes Binden. In Visual Basic-Projekte, in denen **Option Strict** ist ausgeschaltet oder in Visual C#-Projekten, die auf die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], können Sie die Funktionen für die späte Bindung in diesen Sprachen auf spät gebundene Member zugreifen. In Visual Basic-Projekte, in denen **Option Strict** ist, müssen Sie mithilfe von Reflektion auf diesen Member zugreifen.  
  
### <a name="examples"></a>Beispiele  
 Im folgenden Codebeispiel wird veranschaulicht, wie auf spät gebundene Member in einem Visual Basic-Projekt, in dem **Option Strict** ist ausgeschaltet oder in einem Visual C#-Projekt, das als Ziel verwendet die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. In diesem Beispiel greift auf die spät gebundene **Namen** Eigenschaft von der **Datei öffnen** in Word im Dialogfeld. Um dieses Codebeispiel verwenden möchten, führen Sie ihn von der `ThisDocument` oder `ThisAddIn` -Klasse in einem Word-Projekt.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie die Reflektion verwenden, um die gleiche Aufgabe in einem Visual Basic-Projekt, in dem **Option Strict** befindet sich auf.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)   
 [Verwendung Typs Dynamic &#40;C&#35; Programmierhandbuch&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict-Anweisung](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflektion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflektion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)  
  
  