---
title: 'Vorgehensweise: Programmgesteuertes Speichern von Dokumenten | Microsoft Docs'
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
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
ms.assetid: a6225ae9-94f5-421a-9860-5299002d543d
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 251522a745ee7b8dc9894a403f09d1a6d3f32793
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-save-documents"></a>Gewusst wie: Programmgesteuertes Speichern von Dokumenten
  Es gibt mehrere Möglichkeiten, Microsoft Office Word-Dokumente zu speichern. Sie können ein Dokument speichern, ohne den Namen des Dokuments zu ändern, oder Sie können ein Dokument unter einem neuen Namen speichern.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="saving-a-document-without-changing-the-name"></a>Speichern eines Dokuments ohne Änderung des Namens  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Zum Speichern des Dokuments einer Anpassung auf Dokumentebene zugeordnet  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Word.Document.Save%2A>-Methode der <xref:Microsoft.Office.Tools.Word.Document>-Klasse auf. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
#### <a name="to-save-the-active-document"></a>So speichern Sie das aktive Dokument  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.Save%2A> Methode für das aktive Dokument. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
     [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
 Wenn Sie nicht sicher sind, ob das Dokument, das Sie speichern möchten das aktive Dokument ist, finden Sie in er mit seinem Namen.  
  
#### <a name="to-save-a-document-specified-by-name"></a>Speichern Sie ein namentlich angegebenes Dokument  
  
1.  Verwenden Sie den Namen des Dokuments als Argument an die <xref:Microsoft.Office.Interop.Word.Documents> Auflistung. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="saving-a-document-with-a-new-name"></a>Speichern eines Dokuments unter einem neuen Namen  
 Verwenden Sie die SaveAs-Methode, um ein Dokument unter einem neuen Namen speichern. Können Sie diese Methode von der <xref:Microsoft.Office.Tools.Word.Document> Hostelements in einem Word-Projekt auf Dokumentebene oder ein systemeigenes <xref:Microsoft.Office.Interop.Word.Document> Objekt in einem Word-Projekt. Diese Methode erfordert, dass Sie den neuen Dateinamen angeben, aber andere Argumente optional sind.  
  
> [!NOTE]  
>  Wenn Sie Anzeigen der **SaveAs** Dialogfeld innerhalb eines der <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> -Ereignishandler des `ThisDocument` und legen Sie die *"Abbrechen"* Parameter **"false"**, kann die Anwendung unerwartet beendet. Wenn Sie festlegen, die *"Abbrechen"* Parameter **"true"**, wird eine Fehlermeldung angezeigt, der angibt, dass die automatische Speicherung deaktiviert wurde.  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Zum Speichern des Dokuments einer Anpassung auf Dokumentebene mit einem neuen Namen zugeordnet  
  
1.  Aufrufen der <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> Methode der `ThisDocument` Klasse im Projekt verwenden einen vollqualifizierten Pfad und Namen. Wenn der Ordner bereits eine Datei dieses Namens enthält, wird die Datei automatisch überschrieben. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es über die `ThisDocument` -Klasse aus.  
  
    > [!NOTE]  
    >  Die <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> Methode löst eine Ausnahme aus, wenn ein Zielverzeichnis nicht vorhanden ist oder es sind andere Probleme, die eine Datei speichern. Es empfiehlt sich zu verwenden ist eine **try…catch** blockieren, um die <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> Methode oder innerhalb einer aufrufenden Methode.  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
#### <a name="to-save-a-native-document-with-a-new-name"></a>Ein systemeigenes Dokument unter einem neuen Namen speichern  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Methode der <xref:Microsoft.Office.Interop.Word.Document> , die Sie speichern möchten, verwenden einen vollqualifizierten Pfad und Namen. Wenn der Ordner bereits eine Datei dieses Namens enthält, wird die Datei automatisch überschrieben.  
  
     Im folgenden Codebeispiel wird speichert das aktive Dokument unter einem neuen Namen ein. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.  
  
    > [!NOTE]  
    >  Die <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Methode löst eine Ausnahme aus, wenn ein Zielverzeichnis nicht vorhanden ist oder es sind andere Probleme, die eine Datei speichern. Es empfiehlt sich zu verwenden ist eine **try…catch** blockieren, um die <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Methode oder innerhalb einer aufrufenden Methode.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Zum Speichern eines Dokuments anhand des Namens muss in einem Verzeichnis namens Test auf Laufwerk "c" ein Dokument mit dem Namen NewDocument.doc vorhanden sein.  
  
-   Um ein Dokument unter einem neuen Namen speichern möchten, muss auf Laufwerk "c" ein Verzeichnis namens Test vorhanden sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Schließen von Dokumenten](../vsto/how-to-programmatically-close-documents.md)   
 [Vorgehensweise: Programmgesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Dokumenthostelement](../vsto/document-host-item.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  