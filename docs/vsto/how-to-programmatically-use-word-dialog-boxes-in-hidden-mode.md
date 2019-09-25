---
title: 'Vorgehensweise: Programm gesteuertes Verwenden von Word-Dialogfeldern im verborgenen Modus'
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
ms.openlocfilehash: e32c97069e3400b447f8756f9638c9d88d38d99a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255848"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Vorgehensweise: Programm gesteuertes Verwenden von Word-Dialogfeldern im verborgenen Modus
  Sie können komplexe Vorgänge mit einem Methodenaufruf ausführen, indem Sie die integrierten Dialogfelder in Microsoft Office Word aufrufen, ohne Sie dem Benutzer anzuzeigen. Verwenden Sie hierzu die <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> -Methode <xref:Microsoft.Office.Interop.Word.Dialog> des-Objekts, ohne die <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> -Methode aufrufen zu müssen.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Beispiele
 In den folgenden Codebeispielen wird veranschaulicht, wie das Dialogfeld **Seite einrichten** im Modus ausgeblendet verwendet wird, um mehrere Seiten Einrichtungs Eigenschaften ohne Benutzereingaben festzulegen. In den Beispielen wird <xref:Microsoft.Office.Interop.Word.Dialog> ein-Objekt verwendet, um eine benutzerdefinierte Seitengröße zu konfigurieren. Die spezifischen Einstellungen für das Einrichten der Seite, z. b. der obere Rand, der untere Rand usw., sind als spät gebundene Eigenschaften des <xref:Microsoft.Office.Interop.Word.Dialog> -Objekts verfügbar. Diese Eigenschaften werden von Word zur Laufzeit dynamisch erstellt.

 Im folgenden Beispiel wird veranschaulicht, wie Sie diese Aufgabe in Visual Basic Projekten ausführen, bei denen " **Option Strict** " deaktiviert ist C# [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], und in visuellen Projekten, die auf ausgerichtet sind. In diesen Projekten können Sie Features für die späte Bindung in den Visual Basic-und C# Visual-Compilern verwenden. Um dieses Beispiel zu verwenden, führen Sie es `ThisDocument` von `ThisAddIn` der-Klasse oder der-Klasse in Ihrem Projekt aus.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 Im folgenden Beispiel wird veranschaulicht, wie diese Aufgabe in Visual Basic Projekten durchgeführt wird, in denen **Option Strict aktiviert** ist. In diesen Projekten müssen Sie die Reflektion verwenden, um auf die spät gebundenen Eigenschaften zuzugreifen. Um dieses Beispiel zu verwenden, führen Sie es `ThisDocument` von `ThisAddIn` der-Klasse oder der-Klasse in Ihrem Projekt aus.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Programm gesteuertes Verwenden integrierter Dialogfelder in Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)
- [Späte Bindung in Office-Projektmappen](../vsto/late-binding-in-office-solutions.md)
- [Reflektion (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflektion (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
