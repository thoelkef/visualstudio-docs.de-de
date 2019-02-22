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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3e31e5307acb8dadd627cc0a7a0c65572c7ab219
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56653982"
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
- [Vorgehensweise: Programmgesteuertes Erstellen neuer Dokumente](../vsto/how-to-programmatically-create-new-documents.md)
- [Vorgehensweise: Programmgesteuertes Schließen von Dokumenten](../vsto/how-to-programmatically-close-documents.md)
- [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
