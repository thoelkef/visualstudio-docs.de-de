---
title: "Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite"
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
  - "Anwendungsseiten [SharePoint-Entwicklung in Visual Studio], entwickeln"
  - "Anwendungsseiten [SharePoint-Entwicklung in Visual Studio], erstellen"
ms.assetid: 5b6dd941-5c59-4a89-89d0-8e973a00ae9e
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite
  Eine Anwendungsseite ist eine spezielle Form einer ASP.NET\-Seite.  Anwendungsseiten enthalten Inhalt, der mit einer SharePoint\-Masterseite zusammengeführt wird.  Weitere Informationen finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 In dieser exemplarischen Vorgehensweise wird erläutert, wie Sie eine Anwendungsseite erstellen und sie dann mithilfe einer lokalen SharePoint\-Website debuggen.  Auf dieser Seite werden alle Elemente angezeigt, die die einzelnen Benutzer auf allen Websites der Serverfarm erstellt oder geändert haben.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines SharePoint\-Projekts.  
  
-   Hinzufügen einer Anwendungsseite zum SharePoint\-Projekt.  
  
-   Hinzufügen von ASP.NET\-Steuerelementen zur Anwendungsseite.  
  
-   Hinzufügen von Code hinter den ASP.NET\-Steuerelementen.  
  
-   Testen der Anwendungsseite.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die Elemente werden durch die verwendete Edition von Visual Studio und die gewählten Einstellungen bestimmt.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Windows und SharePoint.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] oder eine Edition von Visual Studio Ultimate oder von Visual Studio Premium.  
  
## Erstellen eines SharePoint\-Projekts  
 Erstellen Sie zunächst ein **leeres SharePoint\-Projekt**.  Später fügen Sie diesem Projekt ein Element **Anwendungsseite** hinzu.  
  
#### So erstellen Sie ein SharePoint\-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Öffnen Sie das Dialogfeld **Neues Projekt**, erweitern Sie den Knoten **Office\/SharePoint** unter der gewünschten Sprache, und wählen Sie dann den Knoten **SharePoint\-Lösungen** aus.  
  
3.  Wählen Sie im Bereich **Von Visual Studio installierte Vorlagen** die Vorlage **SharePoint 2010 \- Leeres Projekt** aus.  Geben Sie dem Projekt den Namen "MySharePointProject", und wählen Sie dann die Schaltfläche **OK**.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  Mit diesem Assistenten können Sie die Website, die Sie zum Debuggen des Projekts verwenden, sowie die Vertrauensebene der Projektmappe auswählen.  
  
4.  Wählen Sie das Optionsfeld **Als Farmlösung bereitstellen** aus, und klicken Sie dann auf die Schaltfläche **Fertig stellen**, um die standardmäßige lokale SharePoint\-Website zu übernehmen.  
  
## Erstellen einer Anwendungsseite  
 Um eine Anwendungsseite zu erstellen, fügen Sie dem Projekt ein Element **Anwendungsseite** hinzu.  
  
#### So erstellen Sie eine Anwendungsseite  
  
1.  Wählen Sie im **Projektmappen\-Explorer** das Projekt **MySharePointProject** aus.  
  
2.  Wählen Sie in der Menüleiste **Projekt**,  **Neues Element hinzufügen** aus.  
  
3.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Vorlage **Anwendungsseite \(nur Farmlösung\)** aus.  
  
4.  Nennen Sie die Seite "SearchItems", und klicken Sie dann auf die Schaltfläche **Hinzufügen**.  
  
     Der Visual Web Developer\-Designer zeigt die Anwendungsseite in der Ansicht **Quelle** an, in der die HTML\-Elemente der Seite aufgeführt werden.  Der Designer zeigt das Markup für mehrere <xref:System.Web.UI.WebControls.Content>\-Steuerelemente an.  Jedes Steuerelement ist einem <xref:System.Web.UI.WebControls.ContentPlaceHolder>\-Steuerelement zugeordnet, das auf der standardmäßigen Anwendungsmasterseite definiert ist.  
  
## Entwerfen des Layouts der Anwendungsseite  
 Das Element Anwendungsseite ermöglicht Ihnen die Verwendung eines Designers, um der Anwendungsseite ASP.NET\-Steuerelemente hinzuzufügen.  Dieser Designer ist mit dem in Visual Web Developer verwendeten Designer identisch.  Fügen Sie eine Bezeichnung, eine Optionsfeldliste und eine Tabelle in der Ansicht **Quelle** des Designers hinzu, und legen Sie die Eigenschaften ebenso fest wie beim Entwerfen einer standardmäßigen ASP.NET\-Seite.  
  
 Weitere Informationen zum Verwenden des Designers in Visual Web Developer finden Sie unter [Visual Studio Web Development Content Map](http://msdn.microsoft.com/de-de/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
#### So entwerfen Sie das Layout der Anwendungsseite  
  
1.  Wählen Sie in der Menüleiste **Ansicht**, **Werkzeugkasten** aus.  
  
2.  Im Knoten "Standard" im **Werkzeugkasten** führen Sie einen der folgenden Schritte aus:  
  
    -   Öffnen Sie das Kontextmenü für das Element **Bezeichnung**, wählen Sie **Kopieren** aus, öffnen Sie das Kontextmenü für die Zeile unter dem Inhaltssteuerelement **PlaceHolderMain** im Designer, und wählen Sie dann **Einfügen** aus.  
  
    -   Ziehen Sie das Element aus **Bezeichnung** aus dem **Werkzeugkasten** auf den Text des Inhaltssteuerelements **PlaceHolderMain**.  
  
3.  Wiederholen Sie den vorherigen Schritt, um dem Inhaltssteuerelement**PlaceHolderMain** ein **DropDownList**\-Element und ein **Table**\-Element hinzuzufügen.  
  
4.  Ändern Sie im Designer den Wert des `Text`\-Attributs des Label\-Steuerelements in Alle Elemente anzeigen.  
  
5.  Oder ersetzen Sie im Designer das `<asp:DropDownList>`\-Element durch folgendes XML.  
  
    ```  
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"  
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">  
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>  
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>  
    </asp:DropDownList>  
    ```  
  
## Behandeln der Ereignisse von Steuerelementen auf der Seite  
 Behandeln Sie Steuerelemente auf einer Anwendungsseite ebenso wie bei einer ASP.NET\-Seite.  In diesem Verfahren behandeln Sie das `SelectedIndexChanged`\-Ereignis der Dropdownliste.  
  
#### So behandeln Sie die Ereignisse von Steuerelementen auf der Seite  
  
1.  Wählen Sie im Menü **Ansicht** den Befehl **Code** aus.  
  
     Die Codedatei für die Anwendungsseite wird im Code\-Editor geöffnet.  
  
2.  Fügen Sie der `SearchItems`\-Klasse die folgende Methode hinzu.  In diesem Code wird das <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged>\-Ereignis der <xref:System.Web.UI.WebControls.DropDownList> behandelt, indem eine Methode aufgerufen wird, die Sie später in dieser exemplarischen Vorgehensweise erstellen.  
  
     [!code-csharp[SP_ApplicationPage#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]
     [!code-vb[SP_ApplicationPage#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]  
  
3.  Fügen Sie am Anfang der Codedatei für die Anwendungsseite die folgenden Anweisungen hinzu.  
  
     [!code-csharp[SP_ApplicationPage#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]
     [!code-vb[SP_ApplicationPage#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]  
  
4.  Fügen Sie der `SearchItems`\-Klasse die folgende Methode hinzu.  Diese Methode durchläuft alle Websites der Serverfarm und sucht nach Elementen, die vom aktuellen Benutzer erstellt oder geändert wurden.  
  
     [!code-csharp[SP_ApplicationPage#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]
     [!code-vb[SP_ApplicationPage#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]  
  
5.  Fügen Sie der `SearchItems`\-Klasse die folgende Methode hinzu.  Diese Methode zeigt Elemente an, die vom aktuellen Benutzer in der Tabelle erstellt oder geändert wurden.  
  
     [!code-csharp[SP_ApplicationPage#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]
     [!code-vb[SP_ApplicationPage#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]  
  
## Testen der Anwendungsseite  
 Wenn Sie das Projekt ausführen, wird die SharePoint\-Website geöffnet, und die Anwendungsseite wird angezeigt.  
  
#### So testen Sie die Anwendungsseite  
  
1.  Im **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für die Anwendungsseite, und wählen Sie dann **Als Startelement festlegen** aus.  
  
2.  Drücken Sie die Taste F5.  
  
     Die SharePoint\-Website wird geöffnet.  
  
3.  Wählen Sie auf der Anwendungsseite die Option **Geändert von mir** aus.  
  
     Die Anwendungsseite wird aktualisiert und zeigt alle Elemente an, die Sie auf allen Websites der Serverfarm geändert haben.  
  
4.  Wählen Sie auf der Anwendungsseite **Von mir erstellt** in der Liste aus.  
  
     Die Anwendungsseite wird aktualisiert und zeigt alle Elemente an, die Sie auf allen Websites der Serverfarm erstellt haben.  
  
## Nächste Schritte  
 Weitere Informationen über SharePoint\-Anwendungsseiten finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Weitere Informationen zum Entwerfen von SharePoint\-Seiteninhalten mit dem Visual Web Designer finden Sie in folgenden Themen:  
  
-   [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## Siehe auch  
 [Gewusst wie: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md)   
 [Thema zum Anwendungsseitentyp "\_layouts"](http://go.microsoft.com/fwlink/?LinkID=169274)  
  
  