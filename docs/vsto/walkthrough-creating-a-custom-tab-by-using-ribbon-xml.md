---
title: "Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML | Microsoft Docs"
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
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
ms.assetid: f6391a01-df1a-4a0f-bfbb-a9526c73b2b3
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8933345017cef96c17ed69a42dc3e095fcf7c7ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-tab-by-using-ribbon-xml"></a>Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Multifunktionsleisten-XML
  In dieser exemplarischen Vorgehensweise veranschaulicht, wie eine benutzerdefinierte Registerkarte des Menübands mithilfe der **Menüband (XML)** Element.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen von Schaltflächen auf der **-Add-Ins** Registerkarte. Die **-Add-Ins** Registerkarte ist die Standardregisterkarte, die in der Menüband-XML-Datei definiert ist.  
  
-   Automatisieren von Microsoft Office Word mithilfe der Schaltflächen auf der **-Add-Ins** Registerkarte.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="creating-the-project"></a>Erstellen des Projekts  
 Der erste Schritt besteht im Erstellen eines VSTO-Add-In-Projekts für Word. Später passen die **-Add-Ins** Registerkarte dieses Dokuments.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen einer **Word-Add-in** Projekt mit dem Namen **MyRibbonAddIn**.  
  
     Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Öffnet die **"ThisAddIn.cs"** oder **"ThisAddIn.vb"** Codedatei und fügt die **MyRibbonAddIn** Projekt **Projektmappen-Explorer**.  
  
## <a name="creating-the-vsto-add-ins-tab"></a>Erstellen der VSTO-Registerkarte „Add-Ins“  
 Zum Erstellen der **-Add-Ins** hinzu eine **Menüband (XML)** Element aus, um das Projekt. Später in dieser exemplarischen Vorgehensweise werden Sie dieser Registerkarte einige Schaltflächen hinzufügen.  
  
#### <a name="to-create-the-add-ins-tab"></a>So erstellen Sie die Registerkarte "Add-Ins"  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  In der **neues Element hinzufügen** wählen Sie im Dialogfeld **Menüband (XML)**.  
  
3.  Ändern Sie den Namen des neuen Menübands in **MyRibbon**, und klicken Sie dann auf **Hinzufügen**.  
  
     Die **MyRibbon.cs** oder **"MyRibbon.vb"** Datei wird im Designer geöffnet. Eine XML-Datei mit dem Namen **MyRibbon.xml** wird ebenfalls dem Projekt hinzugefügt.  
  
4.  In **Projektmappen-Explorer**, mit der rechten Maustaste **"ThisAddIn.cs"** oder **"ThisAddIn.vb"**, und klicken Sie dann auf **Code anzeigen**.  
  
5.  Fügen Sie der Klasse **ThisAddin** den folgenden Code hinzu. Dieser Code überschreibt die CreateRibbonExtensibilityObject-Methode und die Office-Anwendung die Menüband-XML-Klasse zurückgegeben.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **MyRibbonAddIn** Projekt, und klicken Sie dann auf **erstellen**. Vergewissern Sie sich, dass das Projekt ohne Fehler erstellt wurde.  
  
## <a name="adding-buttons-to-the-add-ins-tab"></a>Hinzufügen von Schaltflächen zur Registerkarte "Add-Ins"  
 Das Ziel dieses VSTO-Add-Ins besteht darin, Benutzern eine Möglichkeit bereitzustellen, dem aktiven Dokument Textbausteine und eine bestimmte Tabelle hinzuzufügen. Um die Benutzeroberfläche zu gewährleisten, fügen Sie zwei Schaltflächen auf der **-Add-Ins** Registerkarte vom Menüband-XML-Datei ändern. Später in dieser exemplarischen Vorgehensweise definieren Sie Rückrufmethoden für die Schaltflächen. Weitere Informationen über die Menüband-XML-Datei finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md).  
  
#### <a name="to-add-buttons-to-the-add-ins-tab"></a>So fügen Sie der Registerkarte "Add-Ins" Schaltflächen hinzu  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **MyRibbon.xml** , und klicken Sie dann auf **öffnen**.  
  
2.  Ersetzen Sie den Inhalt von der **Registerkarte** Element durch das folgende XML. Diese XML-Code ändert die Bezeichnung der Standardsteuerelementgruppe in **Content**, und fügt zwei neue Schaltflächen mit den Bezeichnungen **Text einfügen** und **Tabelle einfügen**.  
  
    ```  
    <tab idMso="TabAddIns">  
        <group id="ContentGroup" label="Content">  
            <button id="textButton" label="Insert Text"  
                 screentip="Text" onAction="OnTextButton"  
                 supertip="Inserts text at the cursor location."/>  
            <button id="tableButton" label="Insert Table"  
                 screentip="Table" onAction="OnTableButton"  
                 supertip="Inserts a table at the cursor location."/>  
        </group>  
    </tab>  
    ```  
  
## <a name="automating-the-document-by-using-the-buttons"></a>Automatisieren des Dokuments mithilfe der Schaltflächen  
 Sie müssen hinzufügen `onAction` Rückrufmethoden für die **Text einfügen** und **Tabelle einfügen** Schaltflächen, um Aktionen durchzuführen, wenn der Benutzer darauf klickt. Weitere Informationen zu Rückrufmethoden für Menübandsteuerelemente finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md).  
  
#### <a name="to-add-callback-methods-for-the-buttons"></a>So fügen Sie Rückrufmethoden für die Schaltflächen hinzu  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **MyRibbon.cs** oder **"MyRibbon.vb"**, und klicken Sie dann auf **öffnen**.  
  
2.  Fügen Sie den folgenden Code am Anfang der **MyRibbon.cs** oder **"MyRibbon.vb"** Datei. Dieser Code erstellt einen Alias für den Namespace <xref:Microsoft.Office.Interop.Word>.  
  
     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]  
  
3.  Fügen Sie der `MyRibbon`-Klasse die folgende Methode hinzu. Dies ist eine Rückrufmethode für die **Text einfügen** Schaltfläche, eine Zeichenfolge mit dem aktiven Dokument an der aktuellen Position des Cursors hinzugefügt.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]  
  
4.  Fügen Sie der `MyRibbon`-Klasse die folgende Methode hinzu. Dies ist eine Rückrufmethode für die **Tabelle einfügen** Schaltfläche, eine Tabelle mit dem aktiven Dokument an der aktuellen Position des Cursors hinzugefügt.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]  
  
## <a name="testing-the-vsto-add-in"></a>Testen des VSTO-Add-Ins  
 Beim Ausführen des Projekts, Word geöffnet, und der Registerkarte "mit dem Namen" **-Add-Ins** im Menüband angezeigt wird. Klicken Sie auf die **Text einfügen** und **Tabelle einfügen** Schaltflächen auf der **-Add-Ins** Tab, um den Code zu testen.  
  
#### <a name="to-test-your-vsto-add-in"></a>So testen Sie Ihr VSTO-Add-In  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Überprüfen Sie, ob die **-Add-Ins** Registerkarte auf dem Menüband angezeigt wird.  
  
3.  Klicken Sie auf die Registerkarte **Add-Ins** .  
  
4.  Überprüfen Sie, ob die **Content** Gruppe auf dem Menüband angezeigt wird.  
  
5.  Klicken Sie auf die **Text einfügen** Schaltfläche der **Content** Gruppe.  
  
     Eine Zeichenfolge wird dem Dokument an der aktuellen Position des Cursors hinzugefügt.  
  
6.  Klicken Sie auf die **Tabelle einfügen** Schaltfläche der **Content** Gruppe.  
  
     Eine Tabelle wird dem Dokument an der aktuellen Position des Cursors hinzugefügt.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Weitere Informationen zum Anpassen der Office-Benutzeroberfläche finden Sie in diesen Themen:  
  
-   Anpassen des Menübands einer anderen Office-Anwendung. Weitere Informationen zu den Anwendungen, die beim Anpassen des Menübands unterstützen, finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).  
  
-   Anpassen des Menüband einer Office-Anwendung mithilfe des Menüband-Designers. Weitere Informationen finden Sie unter [Ribbon Designer](../vsto/ribbon-designer.md).  
  
-   Erstellen eines benutzerdefinierten Aktionsbereichs. Weitere Informationen finden Sie unter [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
-   Anpassen der Benutzeroberfläche von Microsoft Office Outlook mithilfe von Outlook-Formularbereichen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Menüband](../vsto/ribbon-overview.md)   
 [Menüband-XML](../vsto/ribbon-xml.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  