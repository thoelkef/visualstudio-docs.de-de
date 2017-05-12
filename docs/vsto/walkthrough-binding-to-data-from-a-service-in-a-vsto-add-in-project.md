---
title: "Exemplarische Vorgehensweise: Binden an Daten aus einem Dienst in einem VSTO-Add-In-Projekt"
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
  - "Datenbanken [Office-Entwicklung in Visual Studio], Scrollen von Datensätzen"
  - "Datensätze [Office-Entwicklung in Visual Studio], scrollen"
  - "Daten [Office-Entwicklung in Visual Studio], Scrollen von Datenbankdatensätzen"
ms.assetid: 9b008be4-06a3-4ffc-9f02-79dd6cfe00ab
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Exemplarische Vorgehensweise: Binden an Daten aus einem Dienst in einem VSTO-Add-In-Projekt
  Sie können Daten in VSTO\-Add\-In\-Projekten an Hoststeuerelemente binden. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Steuerelemente zu einem Microsoft Office Word\-Dokument hinzugefügt werden, wie die Steuerelemente an Daten gebunden werden, die aus dem MSDN Content Service abgerufen werden, und wie auf Ereignisse zur Laufzeit reagiert wird.  
  
 **Betrifft:** Die Informationen in diesem Thema betreffen Projekte auf Anwendungsebene für Word 2010. Weitere Informationen finden Sie unter [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen eines <xref:Microsoft.Office.Tools.Word.RichTextContentControl>\-Steuerelements zu einem Dokument zur Laufzeit  
  
-   Binden des <xref:Microsoft.Office.Tools.Word.RichTextContentControl>\-Steuerelements an Daten aus einem Webdienst  
  
-   Reagieren auf das <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>\-Ereignis eines <xref:Microsoft.Office.Tools.Word.RichTextContentControl>Steuerelements  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Erstellen eines neuen Projekts  
 Der erste Schritt besteht im Erstellen eines VSTO\-Add\-In\-Projekts für Word.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie in Visual Basic oder C\# ein Word\-VSTO\-Add\-In\-Projekt namens **MTPS Content Service**.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die Datei `ThisAddIn.vb` oder `ThisAddIn.cs` und fügt das Projekt dem **Projektmappen\-Explorer** hinzu.  
  
## Hinzufügen eines Webdiensts  
 Für diese exemplarische Vorgehensweise verwenden Sie einen Webdienst, der den Namen „MTPS Content Service“ hat. Dieser Webdienst gibt Informationen aus einem angegebenen MSDN\-Artikel in Form einer XML\-Zeichenfolge oder als Nur\-Text zurück. In einem späteren Schritt wird gezeigt, wie die zurückgegebenen Informationen in einem Inhaltssteuerelement angezeigt werden.  
  
#### So fügen Sie dem Projekt den „MTPS Content Service“ hinzu  
  
1.  Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.  
  
2.  Klicken Sie im **Assistent zum Konfigurieren von Datenquellen** auf **Dienst** und dann auf **Weiter**.  
  
3.  Geben Sie die folgende URL in das Feld **Adresse** ein:  
  
     **http:\/\/services.msdn.microsoft.com\/ContentServices\/ContentService.asmx**  
  
4.  Klicken Sie auf **Go**.  
  
5.  Geben Sie in das Feld **Namespace** die Zeichenfolge **ContentService** ein, und klicken Sie auf **OK**.  
  
6.  Klicken Sie im Dialogfeld **Assistent zum Hinzufügen von Verweisen** auf **Fertig stellen**.  
  
## Hinzufügen eines Inhaltssteuerelements und Binden an Daten zur Laufzeit  
 In VSTO\-Add\-In\-Projekten nehmen Sie das Hinzufügen und Binden von Steuerelementen zur Laufzeit vor. In dieser exemplarischen Vorgehensweise konfigurieren Sie das Inhaltssteuerelement so, dass es Daten aus dem Webdienst abruft, wenn ein Benutzer auf das Steuerelement klickt.  
  
#### So fügen Sie ein Inhaltssteuerelement hinzu und binden es an Daten  
  
1.  Deklarieren Sie in der `ThisAddIn`\-Klasse die Variablen für „MTPS Content Service“, das Inhaltssteuerelement und die Datenbindung.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#2)]  
  
2.  Fügen Sie der `ThisAddIn`\-Klasse die folgende Methode hinzu. Diese Methode erstellt ein Inhaltssteuerelement am Anfang des aktiven Dokuments.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#4)]  
  
3.  Fügen Sie der `ThisAddIn`\-Klasse die folgende Methode hinzu. Diese Methode initialisiert die Objekte, die zum Erstellen und Senden einer Anforderung an den Webdienst erforderlich sind.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#6)]  
  
4.  Erstellen Sie einen Ereignishandler, um das MSDN Library\-Dokument über Inhaltssteuerelemente abzurufen, wenn ein Benutzer auf das Inhaltssteuerelement klickt, und die Daten an das Inhaltssteuerelement zu binden.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#5)]  
  
5.  Rufen Sie die Methoden `AddRichTextControlAtRange` und `InitializeServiceObjects` aus der `ThisAddIn_Startup`\-Methode auf. C\#\-Programmierer müssen einen Ereignishandler hinzufügen.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#3)]  
  
## Testen des Add\-Ins  
 Wenn Sie Word öffnen, wird das <xref:Microsoft.Office.Tools.Word.RichTextContentControl>\-Steuerelement angezeigt. Der Text im Steuerelement ändert sich, wenn Sie auf das Steuerelement klicken.  
  
#### So testen Sie das VSTO\-Add\-In  
  
1.  Drücken Sie **F5**.  
  
2.  Klicken Sie auf das Inhaltssteuerelement.  
  
     Es werden Informationen aus dem „MTPS Content Service“ heruntergeladen und im Inhaltssteuerelement angezeigt.  
  
## Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  