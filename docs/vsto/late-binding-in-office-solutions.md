---
title: Spätes Binden in Office-Projektmappen
ms.date: 02/02/2017
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
ms.openlocfilehash: c886305b3cfe63ef2d2821752d97099d93689891
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847255"
---
# <a name="late-binding-in-office-solutions"></a>Spätes Binden in Office-Projektmappen
  Einige Typen in der Objektmodelle von Office-Anwendungen bieten Funktionen, die über die Funktionen mit späten Bindung verfügbar ist. Beispielsweise werden einige Methoden und Eigenschaften können je nach Kontext der Office-Anwendung verschiedene Objekttypen zurückgeben, und einige Typen können verschiedene Methoden oder Eigenschaften in unterschiedlichen Kontexten verfügbar machen.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual Basic-Projekte, in denen **Option Strict** ist und Sie können in Visual C# Projekte, die auf die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] können arbeiten direkt mit Typen, die diese Funktionen mit späten Bindung verwendet.  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Implizite und explizite Umwandlung des Objekts geben Werte zurück.  
 Viele Methoden und Eigenschaften in das Zurückgeben von primären Interop-Assemblys (PIAs) für Microsoft Office <xref:System.Object> Werte, da sie verschiedene Arten von Objekten zurückgeben können. Z. B. die <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> -Eigenschaft gibt ein <xref:System.Object> , da der Rückgabewert möglich ein <xref:Microsoft.Office.Interop.Excel.Worksheet> oder <xref:Microsoft.Office.Interop.Excel.Chart> -Objekt, je nachdem, was das aktive Blatt ist.  
  
 Wenn eine Methode oder Eigenschaft gibt eine <xref:System.Object>, müssen explizit konvertiert (in Visual Basic) des Objekts in den richtigen Typ in Visual Basic-Projekten, in denen **Option Strict** befindet sich auf. Sie müssen nicht explizit umgewandelt <xref:System.Object> Rückgabewerte in Visual Basic-Projekte, in denen **Option Strict** ist deaktiviert.  
  
 In den meisten Fällen enthält die Referenzdokumentation zu den möglichen Typen von der Rückgabewert für ein Element, das zurückgegeben ein <xref:System.Object>. Konvertieren oder Umwandeln des Objekts können IntelliSense für das Objekt im Code-Editor ein.  
  
 Weitere Informationen zur Konvertierung in Visual Basic finden Sie unter [implizite und explizite Konvertierungen &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) und [CType-Funktion &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### <a name="examples"></a>Beispiele  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein Objekt für einen bestimmten Typ in Visual Basic-Projekt umgewandelt, in denen **Option Strict** ist. In dieser Art des Projekts müssen Sie explizit umwandeln der <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> Eigenschaft, um eine <xref:Microsoft.Office.Interop.Excel.Range>. Dieses Beispiel erfordert ein Excel-Projekt auf Dokumentebene mit einer Arbeitsblattklasse mit dem Namen `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein Objekt für einen bestimmten Typ implizit in ein Visual Basic-Projekt umgewandelt, in denen **Option Strict** ist ausgeschaltet oder in einem visuellen Objekt C# Projekt, das [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. In diesen Typen von Projekten die <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> Eigenschaft wird implizit umgewandelt in ein <xref:Microsoft.Office.Interop.Excel.Range>. Dieses Beispiel erfordert ein Excel-Projekt auf Dokumentebene mit einer Arbeitsblattklasse mit dem Namen `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="access-members-that-are-available-only-through-late-binding"></a>Zugreifen auf Member, die nur durch die späte Bindung verfügbar sind.  
 Einige Eigenschaften und Methoden in der Office-PIAs sind nur über die späte Bindung verfügbar. In Visual Basic-Projekte, in denen **Option Strict** ist ausgeschaltet oder in Visual C# Projekte, die auf die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], können Sie die Funktionen für die späte Bindung in den folgenden Sprachen auf spät gebundene Member zugreifen. In Visual Basic-Projekte, in denen **Option Strict** aktiviert ist, Sie müssen mithilfe von Reflektion auf diesen Member zugreifen.  
  
### <a name="examples"></a>Beispiele  
 Im folgenden Codebeispiel wird veranschaulicht, wie auf spät gebundene Member in Visual Basic-Projekt, in denen **Option Strict** ist ausgeschaltet oder in einem visuellen Objekt C# Projekt, das [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. In diesem Beispiel greift auf die spät gebundene **Namen** Eigenschaft der **Datei öffnen** in Word im Dialogfeld. Um dieses Beispiel verwenden zu können, führen Sie es aus der `ThisDocument` oder `ThisAddIn` Klasse in einem Word-Projekt.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie die Reflektion verwenden, um die gleiche Aufgabe in Visual Basic-Projekt, in denen **Option Strict** ist.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)   
 [Verwenden von dynamischen Typen &#40;C&#35; -Programmierhandbuch&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict-Anweisung](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflektion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflektion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)  
