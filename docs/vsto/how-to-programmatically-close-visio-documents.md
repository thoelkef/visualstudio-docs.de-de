---
title: 'Gewusst wie: Programmgesteuertes Schließen von Visio-Dokumenten'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d800fbe0a6dda6fc7c5160d607d393afcb920cd9
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671572"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Gewusst wie: Programmgesteuertes Schließen von Visio-Dokumenten
  Sie können das aktive Microsoft Office Visio-Dokument schließen, indem Sie die `Microsoft.Office.Interop.Visio.Document.Close`-Methode verwenden.  
  
 Ausführliche Informationen zu dieser Methode finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) -Methode.  
  
## <a name="close-the-active-document"></a>Schließt das aktive Dokument  
  
### <a name="to-close-the-active-document"></a>So schließen Sie das aktive Dokument  
  
-   Rufen Sie die `Microsoft.Office.Interop.Visio.Document.Close`-Methode auf, um das aktive Dokument zu schließen.  
  
     Um das folgende Codebeispiel verwenden möchten, führen Sie es der `ThisAddIn` Klasse in einem VSTO-Add-in-Projekt für Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Gewusst wie: Programmgesteuertes Erstellen neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  