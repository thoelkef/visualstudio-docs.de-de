---
title: 'Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite | Microsoft Docs'
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
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
ms.assetid: 5b6dd941-5c59-4a89-89d0-8e973a00ae9e
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e49e8d50905dc0bb0b3c104a7133fe7435e2e944
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-sharepoint-application-page"></a>Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite
  Eine Anwendungsseite ist eine spezielle Form einer ASP.NET-Seite. Anwendungsseiten enthalten Inhalt, der mit einer SharePoint-Masterseite zusammengeführt wird. Weitere Informationen finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 In dieser exemplarischen Vorgehensweise wird erläutert, wie Sie eine Anwendungsseite erstellen und sie dann mithilfe einer lokalen SharePoint-Website debuggen. Auf dieser Seite werden alle Elemente angezeigt, die die einzelnen Benutzer auf allen Websites der Serverfarm erstellt oder geändert haben.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines SharePoint-Projekts.  
  
-   Hinzufügen einer Anwendungsseite zum SharePoint-Projekt.  
  
-   Hinzufügen von ASP.NET-Steuerelementen zur Anwendungsseite.  
  
-   Hinzufügen von Code hinter den ASP.NET-Steuerelementen.  
  
-   Testen der Anwendungsseite.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Windows und SharePoint. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]oder eine Edition von Visual Studio Ultimate oder Visual Studio Premium.  
  
## <a name="creating-a-sharepoint-project"></a>Erstellen eines SharePoint-Projekts  
 Erstellen Sie zunächst eine **leeres SharePoint-Projekt**. Später fügen Sie ein **Anwendungsseite** Element aus, um dieses Projekt.  
  
#### <a name="to-create-a-sharepoint-project"></a>So erstellen Sie ein SharePoint-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Öffnen der **neues Projekt** Dialogfeld erweitern Sie die **Office/SharePoint** Knoten unter der Sprache, die Sie verwenden möchten, und wählen Sie dann die **SharePoint-Lösungen** Knoten.  
  
3.  In der **Visual Studio installierte Vorlagen** Bereich, wählen Sie die **SharePoint 2010 - leeres Projekt** Vorlage. Nennen Sie das Projekt **Namen "MySharePointProject"**, und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird. Mit diesem Assistenten können Sie die Website, die Sie zum Debuggen des Projekts verwenden, sowie die Vertrauensebene der Projektmappe auswählen.  
  
4.  Wählen Sie die **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche, um die standardmäßige lokale SharePoint-Website zu übernehmen.  
  
## <a name="creating-an-application-page"></a>Erstellen einer Anwendungsseite  
 Fügen Sie zum Erstellen einer Anwendungsseite einer **Anwendungsseite** Element aus, um das Projekt.  
  
#### <a name="to-create-an-application-page"></a>So erstellen Sie eine Anwendungsseite  
  
1.  In **Projektmappen-Explorer**, wählen Sie die **Namen "MySharePointProject"** Projekt.  
  
2.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
3.  In der **neues Element hinzufügen** Dialogfeld Wählen Sie die **Anwendungsseite (nur Farmlösung** Vorlage.  
  
4.  Nennen Sie die Seite **"SearchItems"**, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Visual Web Developer-Designer zeigt die Anwendungsseite in **Quelle** anzeigen, in dem HTML-Elemente der Seite angezeigt. Der Designer zeigt das Markup für mehrere <xref:System.Web.UI.WebControls.Content>-Steuerelemente an. Jedes Steuerelement ist einem <xref:System.Web.UI.WebControls.ContentPlaceHolder>-Steuerelement zugeordnet, das auf der standardmäßigen Anwendungsmasterseite definiert ist.  
  
## <a name="designing-the-layout-of-the-application-page"></a>Entwerfen des Layouts der Anwendungsseite  
 Das Element Anwendungsseite ermöglicht Ihnen die Verwendung eines Designers, um der Anwendungsseite ASP.NET-Steuerelemente hinzuzufügen. Dieser Designer ist mit dem in Visual Web Developer verwendeten Designer identisch. Fügen Sie eine Bezeichnung, eine Optionsfeldliste und eine Tabelle, die die **Quelle** -Ansicht des Designers, und legen Sie dann Eigenschaften aus, wie Sie beim Entwerfen einer standardmäßigen ASP.NET-Seite.  
  
#### <a name="to-design-the-layout-of-the-application-page"></a>So entwerfen Sie das Layout der Anwendungsseite  
  
1.  Klicken Sie in der Menüleiste auf **Ansicht**, **Toolbox**.  
  
2.  In den Knoten "Standard" die **Toolbox**, führen Sie einen der folgenden Schritte aus:  
  
    -   Öffnen Sie das Kontextmenü für die **Bezeichnung** Element, wählen Sie **Kopie**, öffnen Sie das Kontextmenü für die Zeile unter der **PlaceHolderMain** content-Steuerelement im Designer, und klicken Sie dann Wählen Sie **einfügen**.  
  
    -   Ziehen Sie die **Bezeichnung** Element aus der **Toolbox** auf den Text des der **PlaceHolderMain** Inhaltssteuerelement.  
  
3.  Wiederholen Sie den vorherigen Schritt zum Hinzufügen einer **DropDownList** Element und ein **Tabelle** Element zum der **PlaceHolderMain** Inhaltssteuerelement.  
  
4.  Ändern Sie den Wert der im Designer die `Text` Attribut des Label-Steuerelements in **alle Elemente anzeigen**.  
  
5.  Oder ersetzen Sie im Designer das `<asp:DropDownList>`-Element durch folgendes XML.  
  
    ```  
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"  
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">  
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>  
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>  
    </asp:DropDownList>  
    ```  
  
## <a name="handling-the-events-of-controls-on-the-page"></a>Behandeln der Ereignisse von Steuerelementen auf der Seite  
 Behandeln Sie Steuerelemente auf einer Anwendungsseite ebenso wie bei einer ASP.NET-Seite. In diesem Verfahren behandeln Sie das `SelectedIndexChanged`-Ereignis der Dropdownliste.  
  
#### <a name="to-handle-the-events-of-controls-on-the-page"></a>So behandeln Sie die Ereignisse von Steuerelementen auf der Seite  
  
1.  Auf der **Ansicht** Menü wählen **Code**.  
  
     Die Codedatei für die Anwendungsseite wird im Code-Editor geöffnet.  
  
2.  Fügen Sie der `SearchItems`-Klasse die folgende Methode hinzu. In diesem Code wird das <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged>-Ereignis der <xref:System.Web.UI.WebControls.DropDownList> behandelt, indem eine Methode aufgerufen wird, die Sie später in dieser exemplarischen Vorgehensweise erstellen.  
  
     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]  
  
3.  Fügen Sie am Anfang der Codedatei für die Anwendungsseite die folgenden Anweisungen hinzu.  
  
     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]  
  
4.  Fügen Sie der `SearchItems`-Klasse die folgende Methode hinzu. Diese Methode durchläuft alle Websites der Serverfarm und sucht nach Elementen, die vom aktuellen Benutzer erstellt oder geändert wurden.  
  
     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]  
  
5.  Fügen Sie der `SearchItems`-Klasse die folgende Methode hinzu. Diese Methode zeigt Elemente an, die vom aktuellen Benutzer in der Tabelle erstellt oder geändert wurden.  
  
     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]  
  
## <a name="testing-the-application-page"></a>Testen der Anwendungsseite  
 Wenn Sie das Projekt ausführen, wird die SharePoint-Website geöffnet, und die Anwendungsseite wird angezeigt.  
  
#### <a name="to-test-the-application-page"></a>So testen Sie die Anwendungsseite  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die Seite "Anwendung", und wählen Sie dann **als Startelement festlegen**.  
  
2.  Drücken Sie die Taste F5.  
  
     Die SharePoint-Website wird geöffnet.  
  
3.  Wählen Sie auf der Seite "Anwendung" die **geändert von mir** Option.  
  
     Die Anwendungsseite wird aktualisiert und zeigt alle Elemente an, die Sie auf allen Websites der Serverfarm geändert haben.  
  
4.  Wählen Sie auf der Seite "Anwendung" **von mir erstellte** in der Liste.  
  
     Die Anwendungsseite wird aktualisiert und zeigt alle Elemente an, die Sie auf allen Websites der Serverfarm erstellt haben.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Weitere Informationen zu SharePoint-Anwendungsseiten, finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Weitere Informationen zum Entwerfen von SharePoint-Seiteninhalten mit dem Visual Web Designer finden Sie in folgenden Themen:  
  
-   [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Erstellen von Wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: erstellen eine Anwendungsseite](../sharepoint/how-to-create-an-application-page.md)   
 [Geben auf der Seite "Anwendung _layouts"](http://go.microsoft.com/fwlink/?LinkID=169274)  
  
  