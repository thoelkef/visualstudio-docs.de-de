---
title: "Exemplarische Vorgehensweise: Erstellen eines Webparts f&#252;r SharePoint mithilfe eines Designers"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Webparts [SharePoint-Entwicklung in Visual Studio], Erstellen"
  - "Webparts [SharePoint-Entwicklung in Visual Studio], Designer"
  - "Webparts [SharePoint-Entwicklung in Visual Studio], Entwerfen"
ms.assetid: 3dd62654-ada2-468f-b7da-eb5704a2ff7a
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Exemplarische Vorgehensweise: Erstellen eines Webparts f&#252;r SharePoint mithilfe eines Designers
  Wenn Sie Webparts für eine SharePoint\-Website erstellen, können Benutzer Inhalt, Darstellung und Verhalten der Seiten auf dieser Website direkt mithilfe eines Browsers ändern.  In dieser exemplarischen Vorgehensweise wird erläutert, wie ein Webpart mit der SharePoint\-Projektvorlage **Visuelles Webpart** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] visuell erstellt wird.  
  
 Das erstellte Webpart zeigt eine monatliche Kalenderansicht und ein Kontrollkästchen für jede Kalenderliste auf der Website an.  Die Benutzer können angeben, welche Kalenderlisten in die monatliche Kalenderansicht eingeschlossen werden, indem sie die Kontrollkästchen aktivieren.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines Webparts mit der Projektvorlage **Visuelles Webpart**  
  
-   Entwerfen des Webparts mit dem Visual Web Developer\-Designer in Visual Studio  
  
-   Hinzufügen von Code, um die Ereignisse der Steuerelemente des Webparts zu behandeln  
  
-   Testen des Webparts in SharePoint  
  
    > [!NOTE]  
    >  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt, als in den folgenden Anweisungen aufgeführt werden.  Die Elemente werden durch die verwendete Edition von Visual Studio und die gewählten Einstellungen bestimmt.  Siehe [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Windows und SharePoint.  Siehe [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] oder höher  
  
## Erstellen eines Webpartprojekts  
 Erstellen Sie zunächst mit der Projektvorlage **Visuelles Webpart** ein Webpartprojekt.  
  
#### So erstellen Sie ein Projekt vom Typ Visuelles Webpart  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit der Option **Als Administrator ausführen**.  
  
2.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  Erweitern Sie im Dialogfeld **Neues Projekt** unter **Visual C\#** oder **Visual Basic** den Eintrag **Office\/SharePoint**, und wählen Sie dann die Kategorie **SharePoint\-Lösungen** aus.  
  
4.  Wählen Sie in der Liste der Vorlagen die Vorlage **Visuelles SharePoint 2013\-Webpart** aus, und klicken Sie dann auf die Schaltfläche **OK**.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  Mit diesem Assistenten können Sie die Website, die Sie zum Debuggen des Projekts verwenden, sowie die Vertrauensebene der Projektmappe angeben.  
  
5.  Wählen Sie im Abschnitt **Wie lautet die Vertrauensebene für diese SharePoint\-Lösung?** das Optionsfeld **Als Farmlösung bereitstellen** aus.  
  
6.  Klicken Sie auf die Schaltfläche **Fertig stellen**, um die standardmäßige lokale SharePoint\-Website zu übernehmen.  
  
## Entwerfen des Webparts  
 Entwerfen Sie das Webpart, indem Sie Steuerelemente aus dem **Werkzeugkasten** auf der Oberfläche des Visual Web Developer\-Designers hinzufügen.  
  
#### So entwerfen Sie das Layout für das Webpart  
  
1.  Klicken Sie im Visual Web Developer\-Designer auf die Registerkarte **Entwurf**, um zur Entwurfsansicht zu wechseln.  
  
2.  Wählen Sie in der Menüleiste **Ansicht**, **Werkzeugkasten** aus.  
  
3.  Wählen Sie im Knoten **Standard** im **Werkzeugkasten** das Steuerelement **CheckBoxList** aus, und führen Sie dann einen der folgenden Schritte aus:  
  
    -   Öffnen Sie das Kontextmenü für das Steuerelement **CheckBoxList**, wählen Sie **Kopieren** aus, öffnen Sie das Kontextmenü für die erste Zeile im Designer, und wählen Sie dann **Einfügen** aus.  
  
    -   Ziehen Sie das Steuerelement **CheckBoxList** aus dem **Werkzeugkasten**, und verbinden Sie das Steuerelement mit der ersten Zeile im Designer.  
  
4.  Wiederholen Sie den vorherigen Schritt, aber verschieben Sie eine Schaltfläche in die nächste Zeile des Designers.  
  
5.  Wählen Sie im Designer die Schaltfläche **Button1** aus.  
  
6.  Wählen Sie auf der Menüleiste die Optionen **Ansicht** und **Eigenschaftenfenster** aus.  
  
     Das **Eigenschaftenfenster** wird geöffnet.  
  
7.  Geben Sie in der Eigenschaft **Text** der Schaltfläche "Aktualisieren" ein.  
  
## Behandeln der Ereignisse von Steuerelementen des Webparts  
 Fügen Sie Code hinzu, der es dem Benutzer ermöglicht, der Masterkalenderansicht Kalender hinzuzufügen.  
  
#### So behandeln Sie Ereignisse der Steuerelemente des Webparts  
  
1.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Doppelklicken Sie im Designer auf die Schaltfläche **Aktualisieren**.  
  
    -   Wählen Sie im Fenster **Eigenschaften** für die Schaltfläche **Aktualisieren** die Schaltfläche **Ereignisse** aus.  In der Eigenschaft **Klicken** geben Sie **Button1\_Click** ein und drücken dann die EINGABETASTE.  
  
     Die Benutzersteuerelement\-Codedatei wird im Code\-Editor geöffnet, und der `Button1_Click`\-Ereignishandler wird angezeigt.  Später fügen Sie diesem Ereignishandler Code hinzu.  
  
2.  Fügen Sie am Anfang der Benutzersteuerelement\-Codedatei die folgenden Anweisungen hinzu.  
  
     [!code-csharp[SP_VisualWebPart#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]
     [!code-vb[SP_VisualWebPart#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]  
  
3.  Fügen Sie der `VisualWebPart1`\-Klasse folgende Codezeile hinzu.  In diesem Code wird ein monatliches Kalenderansichtssteuerelement deklariert.  
  
     [!code-csharp[SP_VisualWebPart#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]
     [!code-vb[SP_VisualWebPart#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]  
  
4.  Ersetzen Sie die `Page_Load`\-Methode der `VisualWebPart1`\-Klasse durch folgenden Code.  Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Fügt dem Benutzersteuerelement eine monatliche Kalenderansicht hinzu.  
  
    -   Fügt ein Kontrollkästchen für jede Kalenderliste der Website hinzu.  
  
    -   Gibt eine Vorlage für jeden Typ von Element an, das in der Kalenderansicht angezeigt wird.  
  
     [!code-csharp[SP_VisualWebPart#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]
     [!code-vb[SP_VisualWebPart#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]  
  
5.  Ersetzen Sie die `Button1_Click`\-Methode der `VisualWebPart1`\-Klasse durch folgenden Code.  Mit diesem Code werden der Masterkalenderansicht Elemente aus jedem ausgewählten Kalender hinzugefügt.  
  
     [!code-csharp[SP_VisualWebPart#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]
     [!code-vb[SP_VisualWebPart#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]  
  
## Testen des Webparts  
 Wenn Sie das Projekt ausführen, wird die SharePoint\-Website geöffnet.  Das Webpart wird automatisch dem Webpartkatalog in SharePoint hinzugefügt.  Um dieses Projekt zu testen, führen Sie folgende Aufgaben aus:  
  
-   Fügen Sie jeder von zwei separaten Kalenderlisten ein Ereignis hinzu.  
  
-   Fügen Sie das Webpart einer Webpartseite hinzu.  
  
-   Geben Sie die Listen an, die in die monatliche Kalenderansicht eingeschlossen werden sollen.  
  
#### So fügen Sie Kalenderlisten der Website Ereignisse hinzu  
  
1.  In Visual Studio drücken Sie die Taste F5.  
  
     Die SharePoint\-Website wird geöffnet, und die [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]\-Schnellstartleiste wird auf der Seite angezeigt.  
  
2.  Wählen Sie auf der Schnellstartleiste unter **Listen** den Link **Kalender** aus.  
  
     Die Seite **Kalender** wird angezeigt.  
  
     Wenn der Link "Kalender" nicht in der Schnellstartleiste angezeigt wird, wählen Sie den Link **Websiteinhalte** aus.  Wenn das Element **Kalender** auf der Seite "Websiteinhalte" nicht angezeigt wird, erstellen Sie es.  
  
3.  Wählen Sie auf der Seite "Kalender" einen Tag aus, und klicken Sie dann im ausgewählten Tag auf den Link **Hinzufügen**, um ein Ereignis hinzuzufügen.  
  
4.  Geben Sie im Feld **Titel** im Standardkalender "Ereignis" ein, und klicken Sie dann auf die Schaltfläche **Speichern**.  
  
5.  Klicken Sie auf den Link **Websiteinhalte**, und wählen Sie dann die Kachel **App hinzufügen** aus.  
  
6.  Wählen Sie auf der Seite **Erstellen** den Typ **Kalender** aus, benennen Sie den Kalender, und klicken Sie dann auf die Schaltfläche **Erstellen**.  
  
7.  Fügen Sie dem neuen Kalender ein Ereignis hinzu, geben Sie dem Ereignis im benutzerdefinierten Kalender den Namen "Ereignis", und klicken Sie dann auf die Schaltfläche **Speichern**.  
  
#### So fügen Sie das Webpart einer Webpartseite hinzu  
  
1.  Öffnen Sie auf der Seite **Websiteinhalte** den Ordner **Websiteseiten**.  
  
2.  Klicken Sie im Menüband auf die Registerkarte **Dateien**, öffnen Sie das Menü **Neues Dokument**, und wählen Sie dann den Befehl **Webpartseite** aus.  
  
3.  Geben Sie auf der Seite **Neue Webpartseite** den Namen **SampleWebPartPage.aspx** für die Seite an, und klicken Sie dann auf die Schaltfläche **Erstellen**.  
  
     Die Webpartseite wird angezeigt.  
  
4.  Wählen Sie im oberen Bereich der Webpartseite die Registerkarte **Einfügen** aus, und klicken Sie dann auf die Schaltfläche **Webpart**.  
  
5.  Wählen Sie den Ordner **Benutzerdefiniert** aus, wählen Sie das Webpart **VisualWebPart1** aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen**.  
  
     Das Webpart wird auf der Seite angezeigt.  Die folgenden Steuerelemente werden für das Webpart angezeigt:  
  
    -   Eine monatliche Kalenderansicht.  
  
    -   Eine Schaltfläche **Aktualisieren**.  
  
    -   Ein Kontrollkästchen **Kalender**.  
  
    -   Ein Kontrollkästchen **Benutzerdefinierter Kalender**.  
  
#### So geben Sie die Listen an, die in die monatliche Kalenderansicht eingeschlossen werden sollen  
  
1.  Geben Sie im Webpart Kalender an, die Sie in die monatliche Kalenderansicht einschließen möchten, und klicken Sie dann auf die Schaltfläche **Aktualisieren**.  
  
     Die Ereignisse aus allen angegebenen Kalendern werden in der monatlichen Kalenderansicht angezeigt.  
  
## Siehe auch  
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Gewusst wie: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Gewusst wie: Erstellen eines SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)  
  
  