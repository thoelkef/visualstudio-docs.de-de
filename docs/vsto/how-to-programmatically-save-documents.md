---
title: 'Vorgehensweise: Programmgesteuertes Speichern von Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 99a50ec83d69217d123d11aa83ff02600b82108c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821593"
---
# <a name="how-to-programmatically-save-documents"></a>Vorgehensweise: Programmgesteuertes Speichern von Dokumenten
  Es gibt mehrere Möglichkeiten, Microsoft Office Word-Dokumente zu speichern. Sie können ein Dokument speichern, ohne den Namen des Dokuments zu ändern, oder Sie können ein Dokument mit einem neuen Namen speichern.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="save-a-document-without-changing-the-name"></a>Speichern eines Dokuments ohne Änderung des Namens  
  
### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Zum Speichern des Dokuments einer Anpassung auf Dokumentebene zugeordnet  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Word.Document.Save%2A> -Methode der <xref:Microsoft.Office.Tools.Word.Document> -Klasse auf. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
### <a name="to-save-the-active-document"></a>So speichern Sie das aktive Dokument  
  
1. Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.Save%2A> Methode für das aktive Dokument. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.  
  
    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
   Wenn Sie nicht sicher sind, gibt an, ob das Dokument, die, das Sie speichern möchten, das aktive Dokument ist, können Sie anhand des Namens darauf verweisen.  
  
### <a name="to-save-a-document-specified-by-name"></a>Zum Speichern eines Dokuments anhand des Namens  
  
1.  Verwenden Sie den Namen des Dokuments als Argument an die <xref:Microsoft.Office.Interop.Word.Documents> Auflistung. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="save-a-document-with-a-new-name"></a>Speichern Sie ein Dokument mit einem neuen Namen.  
 Verwenden Sie die SaveAs-Methode, um ein Dokument mit einem neuen Namen zu speichern. Sie können diese Methode verwenden die <xref:Microsoft.Office.Tools.Word.Document> Hostelement in ein Projekt auf Dokumentebene für Word oder eines systemeigenen <xref:Microsoft.Office.Interop.Word.Document> Objekt in jeder Word-Projekt. Diese Methode erfordert, dass Sie den neuen Dateinamen angeben, aber andere Argumente optional sind.  
  
> [!NOTE]  
>  Wenn Sie Anzeigen der **SaveAs** Dialogfeld in der die <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> -Ereignishandler des `ThisDocument` und legen Sie die *Abbrechen* Parameter, um **"false"**, kann die Anwendung unerwartet beendet. Setzen Sie die *Abbrechen* Parameter **"true"**, wird eine Fehlermeldung angezeigt, der angibt, dass die automatische Speicherung deaktiviert wurde.  
  
### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Um das Dokument mit einer Anpassung auf Dokumentebene mit einem neuen Namen zu speichern.  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> Methode der `ThisDocument` Klasse in Ihrem Projekt mit einem vollqualifizierten Pfad und Dateiname. Wenn der Ordner bereits eine Datei dieses Namens enthält, wird die Datei automatisch überschrieben. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es über die `ThisDocument` -Klasse aus.  
  
    > [!NOTE]  
    >  Die <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> Methode löst eine Ausnahme aus, wenn ein Zielverzeichnis nicht vorhanden ist oder liegen andere Probleme vor, das Speichern einer Datei. Es hat sich bewährt, verwenden Sie eine **try … Catch** -Block um die <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> Methode oder in ein aufrufende Methode.  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
### <a name="to-save-a-native-document-with-a-new-name"></a>Um ein systemeigenes Dokument mit einem neuen Namen zu speichern.  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Methode der <xref:Microsoft.Office.Interop.Word.Document> , die gespeichert werden soll, verwenden einen vollqualifizierten Pfad und Namen. Wenn der Ordner bereits eine Datei dieses Namens enthält, wird die Datei automatisch überschrieben.  
  
     Im folgenden Codebeispiel wird speichert das aktive Dokument unter einem neuen Namen ein. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.  
  
    > [!NOTE]  
    >  Die <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Methode löst eine Ausnahme aus, wenn ein Zielverzeichnis nicht vorhanden ist oder liegen andere Probleme vor, das Speichern einer Datei. Es hat sich bewährt, verwenden Sie eine **try … Catch** -Block um die <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Methode oder in ein aufrufende Methode.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Um ein Dokument anhand des Namens zu speichern, ein Dokument namens *NewDocument.doc* muss vorhanden sein, in ein Verzeichnis namens *Test* auf Laufwerk C.  
  
-   Um ein Dokument mit einem neuen Namen speichern, ein Verzeichnis namens *Test* muss vorhanden sein, auf Laufwerk C.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Schließen von Dokumenten](../vsto/how-to-programmatically-close-documents.md)   
 [Vorgehensweise: Programmgesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Dokumenthostelement](../vsto/document-host-item.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
