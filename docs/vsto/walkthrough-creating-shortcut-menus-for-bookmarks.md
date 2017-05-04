---
title: "Exemplarische Vorgehensweise: Erstellen von Kontextmen&#252;s f&#252;r Lesezeichen | Microsoft Docs"
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
  - "Bookmark-Steuerelement, Ereignisse"
  - "Kontextmenüs, Word"
  - "Menüs, Erstellen in Office-Anwendungen"
  - "Kontextmenüs, Word"
ms.assetid: 86dbf3ff-ba75-42f9-8df6-abfc19b3cf6b
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Exemplarische Vorgehensweise: Erstellen von Kontextmen&#252;s f&#252;r Lesezeichen
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Kontextmenüs für <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelemente in einer Anpassung auf Dokumentebene für Word erstellt werden.  Wenn ein Benutzer mit der rechten Maustaste auf den Text in einem Lesezeichen klickt, wird ein Kontextmenü mit Optionen zum Formatieren des Texts angezeigt.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   [Erstellen des Projekts](#BKMK_CreateProject).  
  
-   [Hinzufügen von Text und Lesezeichen zum Dokument](#BKMK_addtextandbookmarks).  
  
-   [Hinzufügen von Befehlen zu einem Kontextmenü](#BKMK_AddCmndsShortMenu).  
  
-   [Formatieren des Texts im Lesezeichen](#BKMK_formattextbkmk).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a> Erstellen des Projekts  
 Der erste Schritt besteht darin, ein Word\-Dokumentprojekt in Visual Studio zu erstellen.  
  
#### So erstellen Sie ein neues Projekt  
  
-   Erstellen Sie ein Word\-Dokumentprojekt mit dem Namen My Bookmark Shortcut Menu.  Wählen Sie im Assistenten **Neues Dokument erstellen** aus.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet das neue Word\-Dokument im Designer und fügt dem **Projektmappen\-Explorer** das **Mein Lesezeichenkontextmenü**\-Projekt hinzu.  
  
##  <a name="BKMK_addtextandbookmarks"></a> Hinzufügen von Text und Lesezeichen zum Dokument  
 Fügen Sie dem Dokument etwas Text und dann zwei überlappende Lesezeichen hinzu.  
  
#### So fügen Sie dem Dokument Text hinzu  
  
-   Geben Sie in das im Designer angezeigte Dokument den folgenden Text ein.  
  
     Dies ist ein Beispiel für das Erstellen eines Kontextmenüs, das angezeigt wird, wenn Sie mit der rechten Maustaste auf den Text in einem Lesezeichen klicken.  
  
#### So fügen Sie dem Dokument ein Lesezeichen\-Steuerelement hinzu  
  
1.  Ziehen Sie im **Werkzeugkasten** von der Registerkarte **Word\-Steuerelemente** ein <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelement zum Dokument.  
  
     Das Dialogfeld **Lesezeichen\-Steuerelement hinzufügen** wird angezeigt.  
  
2.  Markieren Sie die Wörter "Erstellen eines Kontextmenüs, wenn Sie mit der rechten Maustaste auf den Text klicken", und klicken Sie dann auf **OK**.  
  
     Dem Dokument wird `bookmark1` hinzugefügt.  
  
3.  Fügen Sie den Wörtern "mit der rechten Maustaste auf den Text in einem Lesezeichen klicken" ein weiteres <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelement hinzu.  
  
     Dem Dokument wird `bookmark2` hinzugefügt.  
  
    > [!NOTE]  
    >  Die Wörter "mit der rechten Maustaste auf den Text klicken" werden sowohl in `bookmark1` als auch in `bookmark2` angezeigt.  
  
 Wenn Sie einem Dokument zur Entwurfszeit ein Lesezeichen hinzufügen, wird ein <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelement erstellt.  Sie können mehrere Ereignisse des Lesezeichens programmieren.  Sie können Code in das <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>\-Ereignis des Lesezeichens schreiben, sodass ein Kontextmenü angezeigt wird, wenn der Benutzer mit der rechten Maustaste auf den Text in einem Lesezeichen klickt.  
  
##  <a name="BKMK_AddCmndsShortMenu"></a> Hinzufügen von Befehlen zu einem Kontextmenü  
 Hinzufügen von Schaltflächen zum Kontextmenü, das angezeigt wird, wenn Sie mit der rechten Maustaste auf das Dokument klicken.  
  
#### So fügen Sie einem Kontextmenü Befehle hinzu  
  
1.  Fügen Sie dem Projekt ein neues **Menüband\-XML**\-Element hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Erste Schritte beim Anpassen der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Wählen Sie im **Projektmappen\-Explorer** die Datei **ThisDocument.cs** oder **ThisDocument.vb** aus.  
  
3.  Wählen Sie in der Menüleiste **Ansicht** und **Code**.  
  
     Die **ThisDocument**\-Klassendatei wird im Code\-Editor geöffnet.  
  
4.  Fügen Sie der **ThisDocument**\-Klasse den folgenden Code hinzu.  Mit diesem Code wird die CreateRibbonExtensibilityObject\-Methode überschrieben und der Office\-Anwendung die Menüband\-XML\-Klasse zurückgegeben.  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#1)]  
  
5.  Wählen Sie die Menüband\-XML\-Datei im **Projektmappen\-Explorer** aus.  Standardmäßig erhält die Menüband\-XML\-Datei den Namen "Ribbon1.xml".  
  
6.  Wählen Sie in der Menüleiste **Ansicht** und **Code**.  
  
     Die Menüband\-XML\-Datei wird im Code\-Editor geöffnet.  
  
7.  Ersetzen Sie im Code\-Editor den Inhalt der Menüband\-XML\-Datei durch den folgenden Code:  
  
    ```  
  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="BoldButton" label="Bold" onAction="ButtonClick"          
               getVisible="GetVisible" />  
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"   
              getVisible="GetVisible"/>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
     Dieser Code fügt dem Kontextmenü, das beim Rechtsklick auf das Dokument angezeigt wird, zwei Schaltflächen hinzu.  
  
8.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf `ThisDocument`, und klicken Sie dann auf **Code anzeigen**.  
  
9. Deklarieren Sie auf Klassenebene die folgenden Variablen sowie eine Lesezeichenvariable.  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#2)]  
  
10. Wählen Sie die Menüband\-Codedatei im **Projektmappen\-Explorer** aus.  Standardmäßig wird die Menüband\-Codedatei **Ribbon1.cs** oder **Ribbon1.vb** genannt.  
  
11. Wählen Sie in der Menüleiste **Ansicht** und **Code**.  
  
     Die Menüband\-Codedatei wird im Code\-Editor geöffnet.  
  
12. Fügen Sie der Menüband\-Codedatei die folgende Methode hinzu.  Dies ist eine Rückrufmethode für die zwei Schaltflächen, die Sie dem Kontextmenü des Dokuments hinzugefügt haben.  Diese Methode bestimmt, ob diese Schaltflächen im Kontextmenü angezeigt werden.  Die Schaltflächen für Fett\- und Kursivformatierung werden nur angezeigt, wenn Sie mit der rechten Maustaste auf Text innerhalb eines Lesezeichens klicken.  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a> Formatieren des Texts im Lesezeichen  
  
#### So formatieren Sie den Text im Lesezeichen  
  
1.  Fügen Sie der Menüband\-Codedatei einen `ButtonClick`\-Ereignishandler hinzu, um die Formatierung auf das Lesezeichen anzuwenden.  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/ribbon1.vb#6)]  
  
2.  Wählen Sie im **Projektmappen\-Explorer** die Datei **ThisDocument.cs** oder **ThisDocument.vb** aus.  
  
3.  Wählen Sie in der Menüleiste **Ansicht** und **Code**.  
  
     Die **ThisDocument**\-Klassendatei wird im Code\-Editor geöffnet.  
  
4.  Fügen Sie der **ThisDocument**\-Klasse den folgenden Code hinzu.  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  Sie müssen Code schreiben, um Fälle zu behandeln, in denen sich Lesezeichen überlappen.  Ohne solchen Code wird standardmäßig der Code für alle Lesezeichen aufgerufen, auf die geklickt wurde.  
  
5.  In C\# müssen Sie Ereignishandler für die Bookmark\-Steuerelemente zum <xref:Microsoft.Office.Tools.Word.Document.Startup>\-Ereignis hinzufügen.  Weitere Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#4)]  
  
## Testen der Anwendung  
 Testen Sie das Dokument, um sicherzustellen, dass die fett und kursiv formatierten Menüelemente im Kontextmenü angezeigt werden, wenn Sie mit der rechten Maustaste auf den Text in einem Lesezeichen klicken. Außerdem müssen Sie prüfen, ob der Text korrekt formatiert ist.  
  
#### So testen Sie das Dokument  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Klicken Sie mit der rechten Maustaste in das erste Lesezeichen, und klicken Sie dann auf **Fett**.  
  
3.  Stellen Sie sicher, dass der gesamte Text in `bookmark1` fett formatiert ist.  
  
4.  Klicken Sie mit der rechten Maustaste auf den Text, in dem sich die Lesezeichen überlappen, und klicken Sie dann auf **Kursiv**.  
  
5.  Stellen Sie sicher, dass der gesamte Text in `bookmark2` kursiv formatiert ist, in `bookmark1` jedoch nur der Teil des Texts, der `bookmark2` überlappt, kursiv formatiert ist.  
  
## Nächste Schritte  
 Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Schreiben von Code, um in Excel auf Ereignisse von Hoststeuerelementen zu reagieren.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Programmieren in Abhängigkeit von Ereignissen eines NamedRange-Steuerelements](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
-   Verwenden eines Kontrollkästchens, um die Formatierung in einem Lesezeichen zu ändern.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Ändern der Dokumentformatierung mit CheckBox-Steuerelementen](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen in Word](../vsto/walkthroughs-using-word.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [Bookmark-Steuerelement](../vsto/bookmark-control.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  