---
title: 'Vorgehensweise: Programmgesteuertes verwenden Sie integrierter Dialogfelder in Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e954533957fc655c49145fec9505679d376eedb9
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872533"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Vorgehensweise: Programmgesteuertes verwenden Sie integrierter Dialogfelder in Word
  Bei der Arbeit mit Microsoft Office Word stehen gelegentlich Sie die Dialogfelder für Benutzereingaben angezeigt müssen. Obwohl Sie Ihre eigenen erstellen können, sollten Sie auch den Ansatz der Verwendung der integrierten Dialogfelder in Word, die in verfügbar gemacht werden die <xref:Microsoft.Office.Interop.Word.Dialogs> Auflistung von der <xref:Microsoft.Office.Interop.Word.Application> Objekt. Dadurch können Sie auf mehr als 200 integrierten Dialogfelder, die als Enumerationen dargestellt werden.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="display-dialog-boxes"></a>Anzeigen von Dialogfeldern  
 Um ein Dialogfeld anzuzeigen, verwenden Sie einen der Werte von der <xref:Microsoft.Office.Interop.Word.WdWordDialog> Enumeration zum Erstellen einer <xref:Microsoft.Office.Interop.Word.Dialog> -Objekt, das Dialogfeld darstellt, angezeigt werden soll. Rufen Sie dann die <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> Methode der <xref:Microsoft.Office.Interop.Word.Dialog> Objekt.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie zum Anzeigen der **Datei öffnen** Dialogfeld. Um dieses Beispiel verwenden zu können, führen Sie es aus der `ThisDocument` oder `ThisAddIn` Klasse im Projekt.  
  
 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]  
  
### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Dialogfeld Feld Member zuzugreifen, die über die späte Bindung zur Verfügung stehen  
 Einige Eigenschaften und Methoden der Dialogfelder in Word sind nur durch die späte Bindung verfügbar. In Visual Basic-Projekte, in denen **Option Strict** aktiviert ist, Sie müssen mithilfe von Reflektion auf diesen Member zugreifen. Weitere Informationen finden Sie unter [spätes Binden in Office-Projektmappen](../vsto/late-binding-in-office-solutions.md).  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie mit der **Namen** Eigenschaft der **Datei öffnen** Dialogfeld in Visual Basic-Projekte, in denen **Option Strict** ist ausgeschaltet oder in Visual c# Projekte, die auf die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Um dieses Beispiel verwenden zu können, führen Sie es aus der `ThisDocument` oder `ThisAddIn` Klasse im Projekt.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie Reflektion zu verwenden, den Zugriff auf die **Namen** Eigenschaft der **Datei öffnen** Dialogfeld in Visual Basic-Projekte, in denen **Option Strict** ist auf. Um dieses Beispiel verwenden zu können, führen Sie es aus der `ThisDocument` oder `ThisAddIn` Klasse im Projekt.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Verwenden von Word-Dialogfeldern im ausgeblendeten Modus](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)   
 [Option strict-Anweisung](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflektion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflektion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
