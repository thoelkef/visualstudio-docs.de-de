---
title: "Gewusst wie: Programmgesteuertes Hinzuf&#252;gen von Grafiken und WordArt zu Dokumenten"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Dokumente [Office-Entwicklung in Visual Studio], Hinzufügen von Bildern"
  - "Grafiken, Hinzufügen zu Word-Dokumenten"
  - "Word-Dokumente, Hinzufügen von Bildern"
  - "Word-Dokumente, Hinzufügen von WordArt"
  - "WordArt, Hinzufügen zu Dokumenten"
ms.assetid: 944e1858-bc7c-471f-b5e7-adf3b0fa574d
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Gewusst wie: Programmgesteuertes Hinzuf&#252;gen von Grafiken und WordArt zu Dokumenten
  Sie können Ihren Dokumenten zur Entwurfszeit oder zur Laufzeit Bilder und Zeichnungsobjekte hinzufügen.  Mithilfe von WordArt können Sie Microsoft Office Word\-Dokumenten dekorativen Text hinzufügen.  Diese Spezialeffekte für Text sind Zeichnungsobjekte, die Sie anpassen und in Ihr Dokument einfügen können.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Hinzufügen eines Bilds zur Entwurfszeit  
 Wenn Sie eine Anpassung auf Dokumentebene entwickeln, können Sie dem Dokument zur Entwurfszeit ein Bild hinzufügen.  
  
#### So fügen Sie einem Word\-Dokument zur Entwurfszeit ein Bild hinzu  
  
1.  Platzieren Sie den Cursor an der Stelle, an der Sie das Bild in das Dokument einfügen möchten.  
  
2.  Klicken Sie im Menüband auf die Registerkarte **Einfügen**.  
  
3.  Klicken Sie in der Gruppe **Abbildungen** auf **Bild**.  
  
4.  Navigieren Sie im Dialogfeld **Bild einfügen** zum Bild, das Sie einfügen möchten, und klicken Sie auf **Einfügen**.  
  
     Das Bild wird dem Dokument an der aktuellen Cursorposition hinzugefügt.  
  
## Hinzufügen eines Bilds zur Laufzeit  
 Sie können ein Bild an der aktuellen Cursorposition in ein Dokument einfügen.  
  
#### So fügen Sie ein Bild an der Cursorposition hinzu  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A>\-Methode der <xref:Microsoft.Office.Interop.Word.InlineShapes>\-Auflistung auf, und übergeben Sie den Namen der Datei.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#108](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#108)]
     [!code-vb[Trin_VstcoreWordAutomation#108](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#108)]  
  
## Hinzufügen von WordArt zur Entwurfszeit  
 Wenn Sie eine Anpassung auf Dokumentebene entwickeln, können Sie dem Dokument zur Entwurfszeit WordArt hinzufügen.  
  
#### So fügen Sie einem Word\-Dokument zur Entwurfszeit WordArt hinzu  
  
1.  Platzieren Sie den Cursor an der Stelle, an der Sie WordArt in das Dokument einfügen möchten.  
  
2.  Klicken Sie im Menüband auf die Registerkarte **Einfügen**.  
  
3.  Klicken Sie in der Gruppe **Text** auf **WordArt**, und wählen Sie dann ein WordArt\-Format aus.  
  
4.  Fügen Sie den Text, der im Dokument angezeigt werden soll, dem Dialogfeld **WordArt\-Text bearbeiten** hinzu, und klicken Sie auf **OK**.  
  
     Der Text wird dem Dokument mit dem ausgewählten WordArt\-Format hinzugefügt.  
  
## Hinzufügen von WordArt zur Laufzeit  
 Sie können WordArt an der aktuellen Cursorposition in ein Dokument einfügen.  Die Verfahren unterscheiden sich für Anpassungen auf Dokumentebene und VSTO\-Add\-Ins.  
  
#### So fügen Sie WordArt in einer Anpassung auf Dokumentebene an der Cursorposition hinzu  
  
1.  Rufen Sie die linke und obere Position der aktuellen Cursorposition ab.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomation#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#109)]  
  
2.  Rufen Sie die <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A>\-Methode des <xref:Microsoft.Office.Interop.Word.Shapes>\-Objekts im Dokument auf.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomation#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#110)]  
  
#### So fügen Sie WordArt in einem VSTO\-Add\-In an der Cursorposition hinzu  
  
1.  Rufen Sie die linke und obere Position der aktuellen Cursorposition ab.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#109)]  
  
2.  Rufen Sie die <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A>\-Methode des <xref:Microsoft.Office.Interop.Word.Shapes>\-Objekts des aktiven Dokuments \(oder eines anderen angegebenen Dokuments\) auf.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#110)]  
  
## Kompilieren des Codes  
  
-   Auf Laufwerk "C" muss ein Bild mit dem Namen **SamplePicture.jpg** vorhanden sein.  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Gewusst wie: Programmgesteuertes Einfügen von Text in Word-Dokumente](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Gewusst wie: Programmgesteuertes Wiederherstellen der Auswahl nach Suchvorgängen](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Dokumenten](../vsto/how-to-programmatically-save-documents.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  