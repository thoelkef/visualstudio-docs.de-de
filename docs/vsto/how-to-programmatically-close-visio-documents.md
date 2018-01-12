---
title: "Vorgehensweise: Programmgesteuertes Schließen von Visio-Dokumenten | Microsoft Docs"
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
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 090ba1dae3e870f5864455685c55092eac87f4df
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-close-visio-documents"></a>Gewusst wie: Programmgesteuertes Schließen von Visio-Dokumenten
  Sie können das aktive Microsoft Office Visio-Dokument mithilfe der Microsoft.Office.Interop.Visio.Document.Close-Methode schließen.  
  
 Ausführliche Informationen zu dieser Methode finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Document.Close](http://msdn.microsoft.com/library/office/ff767415.aspx) -Methode.  
  
## <a name="closing-the-active-document"></a>Schließen des aktiven Dokuments  
  
#### <a name="to-close-the-active-document"></a>So schließen Sie das aktive Dokument  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Document.Close-Methode, um das aktive Dokument zu schließen.  
  
     Um das folgende Codebeispiel zu verwenden, führen sie es in der `ThisAddIn` -Klasse in einem VSTO-Add-In-Projekt für Visio aus.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Visio-Objektmodellübersicht](../vsto/visio-object-model-overview.md)   
 [Vorgehensweise: Programmgesteuertes Erstellen neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  