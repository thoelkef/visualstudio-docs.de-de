---
title: 'Vorgehensweise: Programmgesteuertes Verwenden integrierter Dialogfelder in Word | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 961f6ac2aa9852170ecce35aa18ce4c39d7a9983
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Gewusst wie: Programmgesteuertes Verwenden integrierter Dialogfelder in Word
  Bei der Arbeit mit Microsoft Office Word stehen vorkommen, dass die Anzeige von Dialogfeldern für Benutzereingaben werden müssen. Auch wenn Sie eine eigene erstellen können, sollten Sie auch der Ansatz der Verwendung der integrierten Dialogfelder in Word, die in verfügbar gemacht werden die <xref:Microsoft.Office.Interop.Word.Dialogs> Auflistung von der <xref:Microsoft.Office.Interop.Word.Application> Objekt. Dadurch können Sie mehr als 200 integrierte Dialogfelder zugreifen, die als Enumerationen dargestellt werden.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="displaying-dialog-boxes"></a>Anzeigen von Dialogfeldern  
 Um ein Dialogfeld anzuzeigen, verwenden Sie einen der Werte von der <xref:Microsoft.Office.Interop.Word.WdWordDialog> Enumeration zum Erstellen einer <xref:Microsoft.Office.Interop.Word.Dialog> -Objekt, das das Dialogfeld stellt angezeigt werden soll. Rufen Sie dann die <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> Methode der <xref:Microsoft.Office.Interop.Word.Dialog> Objekt.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie zum Anzeigen der **Datei öffnen** (Dialogfeld). Um dieses Codebeispiel verwenden möchten, führen Sie ihn von der `ThisDocument` oder `ThisAddIn` -Klasse im Projekt.  
  
 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]  
  
### <a name="accessing-dialog-box-members-that-are-available-through-late-binding"></a>Zugreifen auf Member des Dialogfelds, die über die späte Bindung zur Verfügung stehen  
 Einige Eigenschaften und Methoden der Dialogfelder in Word sind nur durch späte Bindung verfügbar. In Visual Basic-Projekte, in denen **Option Strict** ist, müssen Sie mithilfe von Reflektion auf diesen Member zugreifen. Weitere Informationen finden Sie unter [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md).  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie die **Namen** Eigenschaft von der **Datei öffnen** Dialogfeld in Visual Basic-Projekte, in denen **Option Strict** ist ausgeschaltet oder in Visual c# Projekte, die auf die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Um dieses Codebeispiel verwenden möchten, führen Sie ihn von der `ThisDocument` oder `ThisAddIn` -Klasse im Projekt.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie die Reflexion verwenden, den Zugriff auf die **Namen** Eigenschaft von der **Datei öffnen** Dialogfeld in Visual Basic-Projekte, in denen **Option Strict** ist auf. Um dieses Codebeispiel verwenden möchten, führen Sie ihn von der `ThisDocument` oder `ThisAddIn` -Klasse im Projekt.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Verwenden von Word-Dialogfeldern im ausgeblendeten Modus](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)   
 [Option Strict-Anweisung](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflektion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflektion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  