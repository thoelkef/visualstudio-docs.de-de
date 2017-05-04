---
title: "Exemplarische Vorgehensweise: Erstellen eines einfachen Projekts f&#252;r eine Websitedefinition | Microsoft Docs"
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
  - "SharePoint-Entwicklung in Visual Studio, Websitedefinitionen"
  - "Websitedefinitionen [SharePoint-Entwicklung in Visual Studio]"
ms.assetid: b0df5b0e-5fa0-43d8-a339-6d92f1276764
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Exemplarische Vorgehensweise: Erstellen eines einfachen Projekts f&#252;r eine Websitedefinition
  In dieser exemplarischen Vorgehensweise wird erläutert, wie eine grundlegende Websitedefinition erstellt wird, die ein visuelles Webpart mit einigen Steuerelementen enthält.  Aus Übersichtsgründen verfügt das visuelle Webpart, das Sie erstellen, nur über wenige Steuerelemente.  Sie können jedoch auch anspruchsvollere SharePoint\-Websitedefinitionen mit mehr Funktionen erstellen.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer Websitedefinition mit der [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Projektvorlage.  
  
-   Erstellen einer SharePoint\-Website mithilfe einer Websitedefinition in SharePoint.  
  
-   Hinzufügen eines visuellen Webparts zur Lösung.  
  
-   Anpassen der Seite default.aspx der Website durch Hinzufügen des neuen visuellen Webparts.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint.  Weitere Informationen finden Sie unter "Anforderungen für die Entwicklung von SharePoint\-Lösungen".  
  
-   Visual Studio.  
  
## Erstellen einer Websitedefinitionslösung  
 Erstellen Sie zunächst das Websitedefinitionsprojekt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### So erstellen Sie ein Websitedefinitionsprojekt  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  Wenn die IDE festgelegt ist, um Visual Basic\-Entwicklungseinstellungen, in der Menüleiste zu verwenden, wählen Sie **Neues Projekt**, **Datei** aus.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Erweitern Sie den Knoten **Visual C\#** oder den Knoten **Visual Basic**, erweitern Sie den Knoten **SharePoint**, und wählen Sie den Knoten **2010** aus.  
  
3.  In der Liste **Vorlagen** wählen Sie die Vorlage **SharePoint 2010\-Projekt** aus.  
  
4.  Im Feld **Name** geben Sie TestSiteDef ein und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  
  
5.  Auf der Seite **Site und Sicherheitsebene für Debugging angeben** geben Sie die URL für die SharePoint\-Website, in der Sie die Websitedefinition debuggen möchten, oder verwenden Sie den Standardspeicherort \(http:\/\/*System Name*\/\).  
  
6.  Wählen Sie im Abschnitt **Wie lautet die Vertrauensebene für diese SharePoint\-Lösung?** das Optionsfeld **Als Farmlösung bereitstellen** aus.  
  
     Alle Websitedefinitionsprojekte müssen als Farmlösungen bereitgestellt werden.  Weitere Informationen über Sandkastenlösungen im Vergleich zu Farmlösungen finden Sie in [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Wählen Sie die Schaltfläche **Fertig stellen** aus.  
  
     Das Projekt wird im **Projektmappen\-Explorer** angezeigt.  
  
8.  Wählen Sie im **Projektmappen\-Explorer** den Projektknoten, und klicken Sie auf der Menüleiste, **Projekt** auswählen, **Neues Element hinzufügen** aus.  
  
9. Entweder unter **Visual C\#** oder den Knoten **Visual BasicSharePoint**, und wählen Sie den Knoten **2010** aus.  
  
10. Im Bereich **Vorlagen** wählen Sie die Vorlage **Sitedefinition** aus, übernehmen Sie **Name** als **SiteDefinition1**, und wählen Sie die Schaltfläche **Hinzufügen** aus.  
  
## Erstellen eines visuellen Webparts  
 Danach erstellen Sie ein visuelles Webpart, das auf der Hauptseite der Sitedefinition angezeigt.  
  
#### So erstellen Sie ein visuelles Webpart  
  
1.  Wählen Sie im **Projektmappen\-Explorer** die Schaltfläche **Alle Dateien anzeigen** aus.  
  
2.  Wählen Sie den Projektknoten **SiteDefinition1**, und dann, auf der Menüleiste aus, wählen Sie **Neues Element hinzufügen**, **Projekt** aus.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
3.  Erweitern Sie den Knoten **Visual C\#** oder den Knoten **Visual Basic**, erweitern Sie den Knoten **SharePoint**, und wählen Sie den Knoten **2010** aus.  
  
4.  In der Liste der Vorlagen, wählen Sie die Vorlage **Visuelles Webpart** aus, übernehmen Sie den Standardnamen VisualWebPart1, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Die VisualWebPart1.ascx\-Datei wird geöffnet.  
  
5.  Am unteren Rand VisualWebPart1.ascx fügen Sie Markup hinzu, um dem Formular drei Steuerelemente hinzuzufügen: ein Textfeld, eine Schaltfläche und eine Bezeichnung:  
  
    ```  
    <table>  
      <tr>  
        <td>  
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>  
        </td>  
        <td>  
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>  
        </td>  
        <td>  
          <asp:Label runat="server" ID="lblName"></asp:Label>  
        </td>  
      </tr>  
    </table>  
    ```  
  
6.  unter VisualWebPart1.ascx öffnen Sie die VisualWebPart1.ascx.cs\-Datei \(für [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]\) oder VisualWebPart1.ascx.vb \(für [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\), und fügen Sie dann den folgenden Code hinzu:  
  
     [!code-csharp[SP_SimpleSiteDef#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_simplesitedef/cs/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]
     [!code-vb[SP_SimpleSiteDef#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_simplesitedef/vb/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]  
  
     Mit diesem Code wird eine Funktion für das Klicken auf die Schaltfläche des Webparts hinzugefügt.  
  
## Hinzufügen des visuellen Webparts zur ASPX\-Standardseite  
 Fügen Sie jetzt der ASPX\-Standardseite der Websitedefinition das visuelle Webpart hinzu.  
  
#### So fügen Sie der ASPX\-Standardseite ein visuelles Webpart hinzu  
  
1.  Öffnen Sie die Seite "default.aspx", und fügen Sie dann der folgenden Zeile unter dem `WebPartPages`\-Tag hinzu:  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Diese Zeile ordnet dem Webpart und seinem Code den Namen MyWebPartControls zu.  Der *Namespace*\-Parameter dem Namespace ab, der in der VisualWebPart1.ascx\-Codedatei verwendet wird.  
  
2.  Nach dem `</asp:Content>`\-Element ersetzen Sie den gesamten Abschnitt `ContentPlaceHolderId="PlaceHolderMain"` und dessen Inhalt durch den folgenden Code:  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     In diesem Code wird ein Verweis auf das zuvor erstellte visuelle Webpart erstellt.  
  
3.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für den Knoten **SiteDefinition1**, und wählen Sie dann **Als Startelement festlegen** aus.  
  
## Die Sitedefinitionslösung bereitstellen und ausführen  
 Als Nächstes stellen Sie das Projekt in SharePoint bereit, und übergeben Sie dann das Projekt aus.  
  
#### So stellen Sie die Websitedefinition bereit und führen sie aus  
  
-   Wählen Sie in der Menüleiste **TestSiteDef bereitstellen**, **Erstellen** aus.  
  
-   Drücken Sie die Taste F5.  
  
     Visual Studio kompiliert den Code hinzugefügt werden, ihre Funktionen, verpackt alle Dateien in eine SharePoint\-Lösungsdatei \(WSP\) und Bereitstellen die WSP\-Datei auf dem SharePoint\-Server.  Anschließend installiert SharePoint die Dateien und aktiviert die Funktionen.  
  
## Erstellen einer Website auf Grundlage der Websitedefinition  
 Erstellen Sie dann eine Website mithilfe der neuen Websitedefinition.  
  
#### So erstellen Sie eine Website mithilfe der Websitedefinition  
  
1.  Auf der SharePoint\-Website wird die Seite Neue SharePoint\-Website angezeigt.  
  
2.  Geben Sie im Abschnitt **Titel und Beschreibung** für den Titel und die Beschreibung der Website "My New Site" ein.  
  
3.  Geben Sie im Abschnitt **Websiteadresse** im Feld **URL\-Name** den Namen "mynewsite" ein.  
  
4.  Im Abschnitt **Vorlage** wählen Sie die Registerkarte **SharePoint\-Anpassungen** aus.  
  
5.  In der Liste **Vorlage auswählen** wählen Sie **SiteDefinition1** aus.  
  
6.  Übernehmen Sie die Standardwerte für die anderen Einstellungen, und wählen Sie dann die Schaltfläche **Erstellen** aus.  
  
     Die neue Website wird angezeigt.  
  
## Testen der neuen Website  
 Testen Sie danach die neue Website, um sicherzustellen, dass sie ordnungsgemäß funktioniert.  
  
#### So testen Sie die neue Website  
  
-   Auf der ASPX\-Standardseite geben Sie Text ein, und wählen Sie dann die Schaltfläche **Bezeichnungstext ändern** neben dem Textfeld aus.  
  
     Der Text wird in der Bezeichnung rechts neben der Schaltfläche.  
  
## Siehe auch  
 [Gewusst wie: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  