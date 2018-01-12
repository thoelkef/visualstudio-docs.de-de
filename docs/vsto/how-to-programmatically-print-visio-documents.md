---
title: 'Vorgehensweise: Programmgesteuertes Drucken von Visio-Dokumenten | Microsoft Docs'
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
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a2ce41f14758d1f34c3e8c31d2ec013fa24c27b1
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-print-visio-documents"></a>Gewusst wie: Programmgesteuertes Drucken von Visio-Dokumenten
  Sie können ein vollständiges Microsoft Office Visio-Dokument oder nur eine bestimmte Seite drucken.  
  
 Ausführliche Informationen zu den Druckmethoden finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Document.Print](https://msdn.microsoft.com/library/office/ff767996.aspx) -Methode und [Microsoft.Office.Interop.Visio.Page.Print](https://msdn.microsoft.com/library/office/ff765064.aspx) -Methode.  
  
## <a name="printing-a-visio-document"></a>Drucken eines Visio-Dokuments  
  
#### <a name="to-print-a-complete-document"></a>So drucken Sie ein vollständiges Dokument  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Document.Print-Methode des Microsoft.Office.Interop.Visio.Document-Objekts, das Sie drucken möchten.  
  
     Im folgenden Codebeispiel wird das aktive Dokument gedruckt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="printing-a-page-of-a-visio-document"></a>Drucken einer Seite eines Visio-Dokuments  
  
#### <a name="to-print-a-page-of-a-document"></a>So drucken Sie eine Seite eines Dokuments  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Pages.Print-Methode des Microsoft.Office.Interop.Visio.Pages-Objekts, das Sie drucken möchten.  
  
     Im folgenden Codebeispiel wird die erste Seite des aktiven Dokuments gedruckt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Visio-Objektmodellübersicht](../vsto/visio-object-model-overview.md)   
 [Vorgehensweise: Programmgesteuertes Erstellen neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  