---
title: 'Vorgehensweise: Programmgesteuertes Formatieren von Text in Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2e0cc5c9e42d3de2b0b5ed34664639b70b31abb3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835275"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Vorgehensweise: Programmgesteuertes Formatieren von Text in Dokumenten
  Sie können mit dem <xref:Microsoft.Office.Interop.Word.Range> -Objekt Text in einem Microsoft Office Word-Dokument formatieren.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Im folgenden Beispiel wird der erste Absatz des Dokuments markiert, und der Schriftgrad, der Schriftartname und die Ausrichtung werden geändert. Anschließend wird der Bereich markiert und ein Meldungsfeld angezeigt, um die Ausführung des Codes vor dem nächsten Abschnitt zu unterbrechen. Im nächste Abschnitt Ruft die rückgängig-Methode, der die <xref:Microsoft.Office.Tools.Word.Document> -Hostelements (bei einer Anpassung auf Dokumentebene) oder die <xref:Microsoft.Office.Interop.Word.Document> -Klasse (bei einem VSTO-Add-in) dreimal. Das Format Standardeinzug wird zugewiesen, und ein Meldungsfeld wird angezeigt, um die Codeausführung zu unterbrechen. Anschließend ruft der Code einmal die <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> -Methode auf und zeigt ein Meldungsfeld an.  
  
## <a name="document-level-customization-example"></a>Beispiel für die Anpassung auf Dokumentebene  
  
### <a name="to-format-text-using-a-document-level-customization"></a>So formatieren Sie Text mit einer Anpassung auf Dokumentebene  
  
1.  Das folgende Beispiel kann in einer Anpassung auf Dokumentebene verwendet werden. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisDocument`-Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]  
  
## <a name="vsto-add-in-example"></a>Beispiel für ein VSTO-Add-In  
  
### <a name="to-format-text-using-a-vsto-add-in"></a>So formatieren Sie Text mithilfe eines VSTO-Add-Ins  
  
1.  Das folgende Beispiel kann in einem VSTO-Add-In verwendet werden. In diesem Beispiel wird das aktive Dokument verwendet. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes Einfügen von Text in Word-Dokumente](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Vorgehensweise: Programmgesteuertes suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
