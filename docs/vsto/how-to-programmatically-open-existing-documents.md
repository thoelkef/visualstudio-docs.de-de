---
title: 'Vorgehensweise: Programmgesteuertes Öffnen vorhandener Dokumente'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2163ddc7db3f0fbcf32abaa8c845b3838e9d2c98
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932154"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Vorgehensweise: Programmgesteuertes Öffnen vorhandener Dokumente
  Die <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> -Methode öffnet die vorhandene Microsoft Office Word-Dokument, das durch einen vollqualifizierten Pfad und Dateiname angegeben. Diese Methode gibt eine <xref:Microsoft.Office.Interop.Word.Document> , der das geöffnete Dokument darstellt.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-open-a-document"></a>Zum Öffnen eines Dokuments  
  
-   Rufen Sie die <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> -Methode der der <xref:Microsoft.Office.Interop.Word.Documents> Sammlung und geben Sie einen Pfad zum Dokument.  
  
     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]  
  
## <a name="to-open-a-document-as-read-only"></a>Um ein Dokument als schreibgeschützt zu öffnen.  
  
-   Rufen Sie die <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> -Methode, geben Sie einen Pfad zum Dokument, und legen die *ReadOnly* Argument **"true"** im Aufruf Methode.  
  
     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Ein Dokument namens *NewDocument.doc* muss vorhanden sein, in ein Verzeichnis namens *Test* auf Laufwerk C.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Erstellen neuer Dokumente](../vsto/how-to-programmatically-create-new-documents.md)   
 [Vorgehensweise: Programmgesteuertes Schließen von Dokumenten](../vsto/how-to-programmatically-close-documents.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
