---
title: 'Vorgehensweise: Programmgesteuertes Verwenden von Word-Dialogfeldern im ausgeblendeten Modus | Microsoft Docs'
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
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
ms.assetid: a5619325-8b54-41f1-becb-3f6eae7e4a6b
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: daf5cfb79c16a26b871e2c4d07ec304c17cb6a33
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Gewusst wie: Programmgesteuertes Verwenden von Word-Dialogfeldern im ausgeblendeten Modus
  Sie können komplexe Vorgänge mit einem Methodenaufruf ausführen, durch den Aufruf der integrierter Dialogfelder in Microsoft Office Word ohne diese dem Benutzer angezeigt. Sie erreichen dies, indem die <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> Methode der <xref:Microsoft.Office.Interop.Word.Dialog> Objekt ohne Aufrufen der <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> Methode.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Codebeispiele veranschaulichen die **Seiteneinrichtung** Dialogfeld im ausgeblendeten Modus mehrere ohne Benutzereingabe festgelegt. Die Beispiele verwenden eine <xref:Microsoft.Office.Interop.Word.Dialog> Objekt so konfigurieren Sie eine benutzerdefinierte Seitengröße. Die spezifischen Einstellungen für die Seite einrichten, z. B. den oberen Rand, unterer Rand usw., sind verfügbar, als spät gebundener Eigenschaften die <xref:Microsoft.Office.Interop.Word.Dialog> Objekt. Diese Eigenschaften werden von Word zur Laufzeit dynamisch erstellt.  
  
 Im folgenden Beispiel wird veranschaulicht, wie zum Ausführen dieser Aufgabe in Visual Basic-Projekte, in denen **Option Strict** ist deaktiviert und in Visual C#-Projekten, die auf die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. In diesen Projekten können Sie Funktionen für späte Bindung in den Visual Basic- und Visual C#-Compiler. Um dieses Codebeispiel verwenden möchten, führen Sie ihn von der `ThisDocument` oder `ThisAddIn` -Klasse im Projekt.  
  
 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]  
  
 Im folgenden Beispiel wird veranschaulicht, wie zum Ausführen dieser Aufgabe in Visual Basic-Projekte, in denen **Option Strict** befindet sich auf. In diesen Projekten müssen Sie den Zugriff auf die spät gebundene Eigenschaften Reflektion verwenden. Um dieses Codebeispiel verwenden möchten, führen Sie ihn von der `ThisDocument` oder `ThisAddIn` -Klasse im Projekt.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Verwenden integrierter Dialogfelder in Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
 [Späte Bindung in Office-Projektmappen](../vsto/late-binding-in-office-solutions.md)   
 [Reflektion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflektion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  