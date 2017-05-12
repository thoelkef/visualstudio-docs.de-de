---
title: "Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Multifunktionsleisten-XML"
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
  - "Benutzerdefinierte Registerkarte [Office-Entwicklung in Visual Studio]"
  - "Anpassen des Menübands, Benutzerdefiniertes Menüband, Registerkarten"
  - "Menüband [Office-Entwicklung in Visual Studio], Anpassen"
  - "Menüband [Office-Entwicklung in Visual Studio], Registerkarten"
  - "Menüband [Office-Entwicklung in Visual Studio], XML"
  - "XML [Office-Entwicklung in Visual Studio], Menüband"
ms.assetid: f6391a01-df1a-4a0f-bfbb-a9526c73b2b3
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Multifunktionsleisten-XML
  Diese exemplarische Vorgehensweise veranschaulicht das Erstellen einer benutzerdefinierten Menüband\-Registerkarte mithilfe des **Menüband \(XML\)**\-Elements.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen von Schaltflächen zur Registerkarte **\-Add\-Ins**.  Die Registerkarte **\-Add\-Ins** ist die Standardregisterkarte, die in der Menüband\-XML\-Datei definiert wird.  
  
-   Automatisieren von Microsoft Office Word mithilfe der Schaltflächen auf der Registerkarte **\-Add\-Ins**.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Diese Elemente sind von der jeweiligen Visual Studio\-Version und den verwendeten Einstellungen abhängig.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## Erstellen des Projekts  
 Der erste Schritt besteht im Erstellen eines VSTO\-Add\-In\-Projekts für Word.  Später passen Sie die Registerkarte **Add\-Ins** dieses Dokuments an.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein **Word\-Add\-in**\-Projekt mit dem Namen "MyRibbonAddIn".  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] öffnet die Codedatei **ThisAddIn.cs** oder **ThisAddIn.vb** und fügt das Projekt **MyRibbonAddIn** dem **Projektmappen\-Explorer** hinzu.  
  
## Erstellen der VSTO\-Registerkarte "Add\-Ins"  
 Fügen Sie zum Erstellen der Registerkarte **Add\-Ins** Ihrem Projekt ein **Menüband \(XML\)**\-Element  hinzu.  Später in dieser exemplarischen Vorgehensweise werden Sie dieser Registerkarte einige Schaltflächen hinzufügen.  
  
#### So erstellen Sie die Registerkarte "Add\-Ins"  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Menüband \(XML\)**.  
  
3.  Ändern Sie den Namen des neuen Menübands in **MyRibbon**, und klicken Sie dann auf **Hinzufügen**.  
  
     Die Datei **MyRibbon.cs** oder **MyRibbon.vb** wird im Designer geöffnet.  Eine XML\-Datei mit dem Namen **MyRibbon.xml** wird dem Projekt ebenfalls hinzugefügt.  
  
4.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Datei **ThisAddIn.cs** oder **ThisAddIn.vb**, und klicken Sie dann auf **Code anzeigen**.  
  
5.  Fügen Sie der Klasse **ThisAddin** den folgenden Code hinzu.  Mit diesem Code wird die CreateRibbonExtensibilityObject\-Methode überschrieben und der Office\-Anwendung die Menüband\-XML\-Klasse zurückgegeben.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
6.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt **MyRibbonAddIn**, und klicken Sie dann auf **Erstellen**.  Vergewissern Sie sich, dass das Projekt ohne Fehler erstellt wurde.  
  
## Hinzufügen von Schaltflächen zur Registerkarte "Add\-Ins"  
 Das Ziel dieses VSTO\-Add\-Ins besteht darin, Benutzern eine Möglichkeit bereitzustellen, dem aktiven Dokument Textbausteine und eine bestimmte Tabelle hinzuzufügen.  Fügen Sie zum Bereitstellen der Benutzeroberfläche der Registerkarte **Add\-Ins** zwei Schaltflächen hinzu, indem Sie die Menüband\-XML\-Datei ändern.  Später in dieser exemplarischen Vorgehensweise definieren Sie Rückrufmethoden für die Schaltflächen.  Weitere Informationen zur Menüband\-XML\-Klasse finden Sie unter [Multifunktionsleisten-XML](../vsto/ribbon-xml.md).  
  
#### So fügen Sie der Registerkarte "Add\-Ins" Schaltflächen hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Datei **MyRibbon.xml**, und klicken Sie dann auf **Öffnen**.  
  
2.  Ersetzen Sie den Inhalt des **tab**\-Elements durch folgenden XML\-Code.  Dieser XML\-Code ändert die Bezeichnung der Standardsteuerelementgruppe in **Inhalt** und fügt zwei neue Schaltflächen mit den Bezeichnungen **Text einfügen** und **Tabelle einfügen** hinzu.  
  
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
  
## Automatisieren des Dokuments mithilfe der Schaltflächen  
 Sie müssen `onAction`\-Rückrufmethoden für die Schaltflächen **Text einfügen** und **Tabelle einfügen** zum Ausführen von Aktionen hinzufügen, wenn der Benutzer auf diese klickt.  Weitere Informationen zu Rückrufmethoden für Menübandsteuerelemente finden Sie unter [Multifunktionsleisten-XML](../vsto/ribbon-xml.md).  
  
#### So fügen Sie Rückrufmethoden für die Schaltflächen hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Datei **MyRibbon.cs**, oder **MyRibbon.vb**, und klicken Sie dann auf **Öffnen**.  
  
2.  Fügen Sie den folgenden Code am Anfang der Datei **MyRibbon.cs** oder **MyRibbon.vb** hinzu.  Dieser Code erstellt einen Alias für den Namespace <xref:Microsoft.Office.Interop.Word>.  
  
     [!code-csharp[Trin_RibbonButtons#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonButtons/CS/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonButtons/VB/MyRibbon.vb#1)]  
  
3.  Fügen Sie der `MyRibbon`\-Klasse die folgende Methode hinzu.  Dies ist eine Rückrufmethode für die Schaltfläche **Text einfügen**, die dem aktiven Dokument an der aktuellen Position des Cursors eine Zeichenfolge hinzufügt.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/MyRibbon.vb#2)]  
  
4.  Fügen Sie der `MyRibbon`\-Klasse die folgende Methode hinzu.  Dies ist eine Rückrufmethode für die Schaltfläche **Tabelle einfügen**, die dem aktiven Dokument an der aktuellen Position des Cursors eine Tabelle hinzufügt.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/MyRibbon.vb#3)]  
  
## Testen des VSTO\-Add\-Ins  
 Beim Ausführen des Projekts wird Word geöffnet, und die Registerkarte mit dem Namen**Add\-Ins** wird auf dem Menüband angezeigt.  Klicken Sie auf die Schaltflächen **Text einfügen** und **Tabelle einfügen** auf der Registerkarte **Add\-Ins**, um den Code zu testen.  
  
#### So testen Sie Ihr VSTO\-Add\-In  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Bestätigen Sie, dass die Registerkarte **Add\-Ins** auf dem Menüband angezeigt wird.  
  
3.  Klicken Sie auf die Registerkarte **Add\-Ins**.  
  
4.  Bestätigen Sie, dass die Gruppe **Inhalt** auf dem Menüband angezeigt wird.  
  
5.  Klicken Sie auf die Schaltfläche **Text einfügen** in der Gruppe **Inhalt**.  
  
     Eine Zeichenfolge wird dem Dokument an der aktuellen Position des Cursors hinzugefügt.  
  
6.  Klicken Sie auf die Schaltfläche **Tabelle einfügen** in der Gruppe **Inhalt**.  
  
     Eine Tabelle wird dem Dokument an der aktuellen Position des Cursors hinzugefügt.  
  
## Nächste Schritte  
 Weitere Informationen zum Anpassen der Office\-Benutzeroberfläche finden Sie in diesen Themen:  
  
-   Anpassen des Menübands einer anderen Office\-Anwendung.  Weitere Informationen zu den Anwendungen, die eine Anpassung des Menübands unterstützen, finden Sie unter[Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md).  
  
-   Anpassen des Menüband einer Office\-Anwendung mithilfe des Menüband\-Designers.  Weitere Informationen finden Sie unter [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md).  
  
-   Erstellen eines benutzerdefinierten Aktionsbereichs.  Weitere Informationen finden Sie unter [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md).  
  
-   Anpassen der Benutzeroberfläche von Microsoft Office Outlook mithilfe von Outlook\-Formularbereichen.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## Siehe auch  
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Multifunktionsleisten-XML](../vsto/ribbon-xml.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  