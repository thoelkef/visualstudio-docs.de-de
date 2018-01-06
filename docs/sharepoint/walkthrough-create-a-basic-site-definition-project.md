---
title: 'Exemplarische Vorgehensweise: Erstellen einer einfachen Projekts Websitedefinition | Microsoft Docs'
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
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
ms.assetid: b0df5b0e-5fa0-43d8-a339-6d92f1276764
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a792ab750decf1a14b589116d886c847b3ddd478
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Exemplarische Vorgehensweise: Erstellen eines einfachen Projekts für eine Websitedefinition
  In dieser exemplarischen Vorgehensweise wird gezeigt, wie eine grundlegenden Websitedefinition erstellt, die ein visuelles Webpart mit einigen Steuerelementen enthält. Aus Gründen der Übersichtlichkeit weist das visuelle Webpart, das Sie erstellen nur wenige Steuerelemente. Allerdings können Sie komplexere Websitedefinitionen für SharePoint erstellen, die weitere Funktionen enthalten.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer Sitedefinition mit der [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Projektvorlage.  
  
-   Erstellen einer SharePoint-Websites mithilfe einer Websitedefinition in SharePoint.  
  
-   Die Projektmappe hinzugefügt ein visuelles Webpart.  
  
-   Anpassen der Seite "default.aspx" der Website durch die neue visuelles Webpart hinzugefügt.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint. Weitere Informationen finden Sie in der Anforderungen für die Entwicklung von SharePoint-Lösungen.  
  
-   Visual Studio.  
  
## <a name="creating-a-site-definition-solution"></a>Erstellen eine Sitedefinitionslösung  
 Erstellen Sie zunächst die Projekts Websitedefinition in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-create-a-site-definition-project"></a>Zum Erstellen des Projekts für eine Websitedefinition  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus. Wenn die IDE für die Verwendung von Visual Basic-entwicklungseinstellungen auf der Menüleiste festgelegt ist, wählen Sie **Datei**, **neues Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Erweitern Sie die **Visual C#-** Knoten oder die **Visual Basic** Knoten, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
3.  In der **Vorlagen** wählen Sie die **SharePoint 2010-Projekt** Vorlage.  
  
4.  In der **Namen** geben **"TestSiteDef" ein**, und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird.  
  
5.  Auf der **Geben Sie die Website und die Sicherheit für das Debuggen** Seite Geben Sie die URL der SharePoint-Website, in dem Sie die Sitedefinition debuggen möchten, oder verwenden den Standardspeicherort (http://*Systemname*/).  
  
6.  In der **neuerungen die Vertrauensebene für diese SharePoint-Lösung?** Abschnitt der **als farmlösung bereitstellen** Optionsfeld.  
  
     Alle Websiteprojekten Definition müssen als farmlösungen bereitgestellt werden. Weitere Informationen über sandkastenlösungen im Vergleich zu farmlösungen finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Wählen Sie die **Fertig stellen** Schaltfläche.  
  
     Das Projekt wird im **Projektmappen-Explorer**.  
  
8.  In **Projektmappen-Explorer**, wählen Sie den Projektknoten, und wählen Sie dann auf der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
9. Unter einem **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
10. In der **Vorlagen** Bereich, wählen Sie die **Sitedefinition** Vorlage, lassen Sie die **Namen** als **SiteDefinition1**, und wählen Sie dann die  **Hinzufügen** Schaltfläche.  
  
## <a name="create-a-visual-web-part"></a>Erstellen Sie ein visuelles Webpart  
 Als Nächstes erstellen Sie ein visuelles Webpart auf der Hauptseite der Websitedefinition angezeigt werden.  
  
#### <a name="to-create-a-visual-web-part"></a>So erstellen ein visuelles Webpart  
  
1.  In **Projektmappen-Explorer**, wählen Sie die **alle Dateien anzeigen** Schaltfläche.  
  
2.  Wählen Sie die **SiteDefinition1** Projektknoten, und wählen Sie dann auf der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
3.  Erweitern Sie die **Visual C#-** Knoten oder die **Visual Basic** Knoten, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
4.  Wählen Sie in der Liste der Vorlagen, die **visuelles Webpart** Vorlage, behalten Sie die Standardeinstellung VisualWebPart1 benennen, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Die VisualWebPart1.ascx-Datei wird geöffnet.  
  
5.  Fügen Sie am unteren Rand VisualWebPart1.ascx, das folgende Markup zum Hinzufügen von drei Steuerelementen zum Formular: ein Textfeld, eine Schaltfläche und eine Bezeichnung:  
  
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
  
6.  Unter VisualWebPart1.ascx, öffnen Sie die VisualWebPart1.ascx.cs-Datei (für [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) oder VisualWebPart1.ascx.vb (für [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), und fügen Sie den folgenden Code hinzu:  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     Dieser Code fügt Funktionen für das Webpart Schaltflächen-Klickereignis hinzu.  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Hinzufügen von visuellen Webparts die ASPX-Standardseite  
 Fügen Sie das visuelle Webpart dann die Sitedefinition ASPX-Standardseite.  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Die Standard-ASPX-Seite ein visuelles Webpart hinzu  
  
1.  Öffnen Sie die Seite "default.aspx", und fügen Sie dann die folgende Zeile unter der `WebPartPages` Tag:  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Diese Zeile ordnet den Namen MyWebPartControls mit das Webpart und des Codes. Die *Namespace* Parameter entspricht den Namespace, der in der Codedatei VisualWebPart1.ascx verwendet wird.  
  
2.  Nach der `</asp:Content>` Element ersetzen den gesamten `ContentPlaceHolderId="PlaceHolderMain"` Abschnitt und seines Inhalts durch den folgenden Code:  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     Dieser Code erstellt einen Verweis auf das visuelle Webpart, das Sie zuvor erstellt haben.  
  
3.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SiteDefinition1** Knoten, und wählen Sie dann **als Startelement festlegen**.  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>Die Sitedefinitionslösung bereitstellen und ausführen  
 Als Nächstes bereitstellen Sie des Projekts in SharePoint, und führen Sie das Projekt.  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>So stellen Sie die Websitedefinition bereit und führen sie aus  
  
-   Wählen Sie in der Menüleiste **erstellen**, **bereitstellen "TestSiteDef" ein**.  
  
-   Drücken Sie die Taste F5.  
  
     Visual Studio kompiliert den Code, dessen Funktionen hinzugefügt, Pakete aller Dateien in einer SharePoint-Lösungsdatei (WSP) und die WSP-Datei auf SharePoint-Server bereitgestellt. SharePoint werden dann die Dateien installiert und aktiviert die Funktionen.  
  
## <a name="create-a-site-based-on-the-site-definition"></a>Erstellen Sie eine Website, die basierend auf der Websitedefinition  
 Als Nächstes erstellen Sie einen Standort mithilfe der neuen Websitedefinition.  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>Zum Erstellen einer Website unter Verwendung der Websitedefinition  
  
1.  Auf der SharePoint-Website angezeigt wird die Seite "neue SharePoint-Website" aus.  
  
2.  In der **Titel und Beschreibung** Geben Sie im Abschnitt **mynewsite** für den Titel und eine Beschreibung des Standorts.  
  
3.  In der **Websiteadresse** Geben Sie im Abschnitt **"mynewsite"** in der **URL-Name** Feld.  
  
4.  In der **Vorlage** Abschnitt der **SharePoint-Anpassungen** Registerkarte.  
  
5.  In der **wählen Sie eine Vorlage** wählen **SiteDefinition1**.  
  
6.  Behalten Sie die Standardwerte für die anderen Einstellungen, und wählen Sie dann die **erstellen** Schaltfläche.  
  
     Die neue Website wird angezeigt.  
  
## <a name="test-the-new-site"></a>Testen der neuen Website  
 Anschließend testen Sie den neuen Standort, um festzustellen, ob sie ordnungsgemäß funktioniert.  
  
#### <a name="to-test-the-new-site"></a>So testen Sie den neuen Standort  
  
-   Geben Sie auf die Standard-ASPX-Seite Text, und wählen Sie dann die **Änderung Bezeichnungstext** Schaltfläche neben dem Textfeld.  
  
     Der Text, die in die Bezeichnung auf der rechten Seite der Schaltfläche angezeigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)   
 [Entwickeln von SharePoint-Projektmappen](../sharepoint/developing-sharepoint-solutions.md)  
  
  