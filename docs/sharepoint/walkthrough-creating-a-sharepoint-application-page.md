---
title: 'Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 802c20a21b624e868cddac4badfd8827ef765506
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866190"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite
 
Eine Anwendungsseite ist eine spezielle Form einer ASP.NET-Seite. Anwendungsseiten enthalten Inhalt, der mit einer SharePoint-Masterseite zusammengeführt wird. Weitere Informationen finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

In dieser exemplarischen Vorgehensweise wird erläutert, wie Sie eine Anwendungsseite erstellen und sie dann mithilfe einer lokalen SharePoint-Website debuggen. Auf dieser Seite werden alle Elemente angezeigt, die die einzelnen Benutzer auf allen Websites der Serverfarm erstellt oder geändert haben.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines SharePoint-Projekts.
- Hinzufügen einer Anwendungsseite zum SharePoint-Projekt.
- Hinzufügen von ASP.NET-Steuerelementen zur Anwendungsseite.
- Hinzufügen von Code hinter den ASP.NET-Steuerelementen.
- Testen der Anwendungsseite.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Vorraussetzungen

- Unterstützte Editionen von Windows und SharePoint.

## <a name="create-a-sharepoint-project"></a>Erstellen Sie ein SharePoint-Projekt

Erstellen Sie zunächst eine **leeres SharePoint-Projekt**. Später fügen Sie eine **Anwendungsseite** dieses Projekt ein Element.

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Öffnen der **neues Projekt** Dialogfeld erweitern Sie die **Office/SharePoint** Knoten unter der Sprache, die Sie verwenden möchten, und wählen Sie dann die **SharePoint-Lösungen** Knoten.

3. In der **Visual Studio installierte Vorlagen** Bereich, wählen Sie die **SharePoint 2010 - leeres Projekt** Vorlage. Nennen Sie das Projekt **MySharePointProject**, und wählen Sie dann die **OK** Schaltfläche.

     Die **SharePoint Customization Wizard** angezeigt wird. Mit diesem Assistenten können Sie die Website, die Sie zum Debuggen des Projekts verwenden, sowie die Vertrauensebene der Projektmappe auswählen.

4. Wählen Sie die **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche, um die standardmäßige lokale SharePoint-Website zu akzeptieren.

## <a name="create-an-application-page"></a>Erstellen einer Anwendungsseite

Fügen Sie zum Erstellen einer Anwendungsseite einer **Anwendungsseite** Elements zum Projekt.

1. In **Projektmappen-Explorer**, wählen Sie die **MySharePointProject** Projekt.

2. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

3. In der **neues Element hinzufügen** Dialogfeld auf die **Anwendungsseite (nur Farmlösung** Vorlage.

4. Nennen Sie die Seite **"SearchItems"**, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Visual Web Developer-Designer zeigt die Anwendungsseite im **Quelle** anzeigen, die Sie, in dem die HTML-Elemente sehen. Der Designer zeigt das Markup für mehrere <xref:System.Web.UI.WebControls.Content>-Steuerelemente an. Jedes Steuerelement ist einem <xref:System.Web.UI.WebControls.ContentPlaceHolder>-Steuerelement zugeordnet, das auf der standardmäßigen Anwendungsmasterseite definiert ist.

## <a name="design-the-layout-of-the-application-page"></a>Entwerfen des Layouts der Anwendungsseite

Das Element Anwendungsseite ermöglicht Ihnen die Verwendung eines Designers, um der Anwendungsseite ASP.NET-Steuerelemente hinzuzufügen. Dieser Designer ist mit dem in Visual Web Developer verwendeten Designer identisch. Hinzufügen einer Bezeichnung, eine Optionsfeldliste und eine Tabelle der **Quelle** -Ansicht des Designers, und legen Sie dann Eigenschaften aus, wie Sie beim Entwerfen einer standardmäßigen ASP.NET-Seite.

1. Wählen Sie in der Menüleiste **Ansicht** > **Toolbox** aus.

2. Im Knoten "Standard" von der **Toolbox**, führen Sie eine der folgenden Schritte aus:

    - Öffnen Sie das Kontextmenü für die **Bezeichnung** Element, und wählen Sie **kopieren**, öffnen Sie das Kontextmenü für die Zeile unter der **PlaceHolderMain** content-Steuerelement im Designer, und klicken Sie dann Wählen Sie **einfügen**.

    - Ziehen Sie die **Bezeichnung** Element aus der **Toolbox** auf den Text des der **PlaceHolderMain** Inhaltssteuerelement.

3. Wiederholen Sie den vorherigen Schritt zum Hinzufügen einer **DropDownList** Element und ein **Tabelle** Element für die **PlaceHolderMain** Inhaltssteuerelement.

4. Ändern Sie den Wert der im Designer die `Text` Attribut des Label-Steuerelements in **alle Elemente anzeigen**.

5. Oder ersetzen Sie im Designer das `<asp:DropDownList>`-Element durch folgendes XML.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Behandeln der Ereignisse von Steuerelementen auf der Seite

Behandeln Sie Steuerelemente auf einer Anwendungsseite ebenso wie bei einer ASP.NET-Seite. In diesem Verfahren behandeln Sie das `SelectedIndexChanged`-Ereignis der Dropdownliste.

1. Auf der **Ansicht** Menü wählen **Code**.

     Die Codedatei für die Anwendungsseite wird im Code-Editor geöffnet.

2. Fügen Sie der `SearchItems` -Klasse die folgende Methode hinzu. In diesem Code wird das <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged>-Ereignis der <xref:System.Web.UI.WebControls.DropDownList> behandelt, indem eine Methode aufgerufen wird, die Sie später in dieser exemplarischen Vorgehensweise erstellen.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Fügen Sie am Anfang der Codedatei für die Anwendungsseite die folgenden Anweisungen hinzu.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Fügen Sie der `SearchItems` -Klasse die folgende Methode hinzu. Diese Methode durchläuft alle Websites der Serverfarm und sucht nach Elementen, die vom aktuellen Benutzer erstellt oder geändert wurden.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Fügen Sie der `SearchItems` -Klasse die folgende Methode hinzu. Diese Methode zeigt Elemente an, die vom aktuellen Benutzer in der Tabelle erstellt oder geändert wurden.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>Testen Sie die Seite "Anwendung"

Wenn Sie das Projekt ausführen, wird die SharePoint-Website geöffnet, und die Anwendungsseite wird angezeigt.

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die Seite "Anwendung" aus, und wählen Sie dann **als Startelement festlegen**.

2. Drücken Sie die Taste **F5**.

     Die SharePoint-Website wird geöffnet.

3. Wählen Sie auf der Anwendungsseite die **geändert von mir** Option.

     Die Anwendungsseite wird aktualisiert und zeigt alle Elemente an, die Sie auf allen Websites der Serverfarm geändert haben.

4. Wählen Sie auf der Anwendungsseite **von mir erstellte** in der Liste.

     Die Anwendungsseite wird aktualisiert und zeigt alle Elemente an, die Sie auf allen Websites der Serverfarm erstellt haben.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SharePoint-Anwendungsseiten, finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Weitere Informationen zum Entwerfen von SharePoint-Seiteninhalten mit dem Visual Web Designer finden Sie in folgenden Themen:

- [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Siehe auch

[Vorgehensweise: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md)  
[Anwendungsseitentyp "_layouts für Anwendung"](http://go.microsoft.com/fwlink/?LinkID=169274)
