---
title: "Vorgehensweise: Programmgesteuertes Öffnen vorhandener Dokumente | Microsoft Docs"
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
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 151571ace6790f05c067f8dff641988301bc1b0e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-open-existing-documents"></a>Gewusst wie: Programmgesteuertes Öffnen vorhandener Dokumente
  Die <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> Methode öffnet den vorhandene Microsoft Office Word-Dokument, das durch einen vollqualifizierten Pfad und Dateiname angegeben. Diese Methode gibt ein <xref:Microsoft.Office.Interop.Word.Document> , die das geöffnete Dokument darstellt.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-open-a-document"></a>Um ein Dokument zu öffnen.  
  
-   Rufen Sie die <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> Methode der <xref:Microsoft.Office.Interop.Word.Documents> Auflistung, und geben Sie einen Pfad zum Dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]  
  
### <a name="to-open-a-document-as-read-only"></a>Um ein Dokument nur schreibgeschützt öffnen.  
  
-   Rufen Sie die <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> Methode, geben Sie einen Pfad auf das Dokument, und legen Sie die *ReadOnly* Argument **"true"** im Aufruf Methode.  
  
     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Ein Dokument mit dem Namen NewDocument.doc muss in einem Verzeichnis namens Test auf Laufwerk "c" vorhanden sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Erstellen neuer Dokumente](../vsto/how-to-programmatically-create-new-documents.md)   
 [Vorgehensweise: Programmgesteuertes Schließen von Dokumenten](../vsto/how-to-programmatically-close-documents.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  