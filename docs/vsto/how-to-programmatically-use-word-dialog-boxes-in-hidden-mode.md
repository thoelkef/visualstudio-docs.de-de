---
title: 'Vorgehensweise: Programmgesteuertes Verwenden von Word-Dialogfeldern im ausgeblendeten Modus'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e7a422e9548fabefa2066fb439c01e382586cd36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961604"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Vorgehensweise: Programmgesteuertes Verwenden von Word-Dialogfeldern im ausgeblendeten Modus
  Sie können komplexe Vorgänge mit einem Methodenaufruf ausführen, durch den Aufruf der integrierter Dialogfelder in Microsoft Office Word ohne diese an den Benutzer anzuzeigen. Sie erreichen dies, indem die <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> Methode der <xref:Microsoft.Office.Interop.Word.Dialog> Objekt ohne Aufrufen der <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> Methode.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Beispiele
 Die folgenden Codebeispielen wird veranschaulicht, wie Sie mit der **Seiteneinrichtung** Dialogfeld im ausgeblendeten Modus mehrere ohne Benutzereingabe festgelegt. Die Beispiele verwenden eine <xref:Microsoft.Office.Interop.Word.Dialog> Objekt so konfigurieren Sie eine benutzerdefinierte Seitengröße. Die spezifischen Einstellungen für die Seite einrichten, wie z. B. den oberen Rand der untere Rand und usw., sind verfügbar, als spät gebundene Eigenschaften der <xref:Microsoft.Office.Interop.Word.Dialog> Objekt. Diese Eigenschaften werden von Word zur Laufzeit dynamisch erstellt.

 Im folgende Beispiel wird veranschaulicht, wie zum Ausführen dieser Aufgabe in Visual Basic-Projekten, in denen **Option Strict** ist deaktiviert und in Visual C#-Projekten, die auf die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. In diesen Projekten können Sie Funktionen mit späten Bindung in der Visual Basic- und Visual C#-Compiler. Um dieses Beispiel verwenden zu können, führen Sie es aus der `ThisDocument` oder `ThisAddIn` Klasse im Projekt.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 Im folgende Beispiel wird veranschaulicht, wie zum Ausführen dieser Aufgabe in Visual Basic-Projekten, in denen **Option Strict** ist. In diesen Projekten müssen Sie die Reflektion verwenden, auf die spät gebundene Eigenschaften zugreifen. Um dieses Beispiel verwenden zu können, führen Sie es aus der `ThisDocument` oder `ThisAddIn` Klasse im Projekt.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Programmgesteuertes verwenden Sie integrierter Dialogfelder in Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)
- [Spätes Binden in Office-Projektmappen](../vsto/late-binding-in-office-solutions.md)
- [Reflektion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflektion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
