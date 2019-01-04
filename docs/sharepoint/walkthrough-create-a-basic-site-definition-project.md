---
title: 'Exemplarische Vorgehensweise: Erstellen ein einfachen Projekts Definition | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e09124e3204240f188c65e10865bbf221e15358
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958890"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Exemplarische Vorgehensweise: Erstellen eines einfachen Projekts definition
  In dieser exemplarischen Vorgehensweise veranschaulicht eine grundlegende Definition zu erstellen, die ein visuelles Webpart mit Steuerelementen darauf enthält. Aus Gründen der Klarheit hat das visuelle Webpart, das Sie erstellen nur wenige Steuerelemente. Allerdings können Sie komplexere Websitedefinitionen für SharePoint erstellen, die weitere Funktionen enthalten.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
- Erstellen eine Sitedefinition mithilfe der [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Projektvorlage.  
  
- Erstellen einer SharePoint-Websites mit einer Websitedefinition in SharePoint.  
  
- Die Lösung wird ein visuelles Webpart hinzugefügt.  
  
- Anpassen der Seite "default.aspx" der Website durch das neue visuelle Webpart hinzugefügt wird.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint. Weitere Informationen finden Sie unter Anforderungen für SharePoint-Lösungen entwickeln.  
  
-   Visual Studio.  
  
## <a name="create-a-site-definition-solution"></a>Erstellen einer Sitedefinition
 Erstellen Sie zunächst das Websiteprojekt-Definition in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-create-a-site-definition-project"></a>Sitedefinitionsprojekt erstellen  
  
1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Wenn Ihre IDE auf der Menüleiste mit Visual Basic-entwicklungseinstellungen festgelegt ist, wählen Sie **Datei** > **neues Projekt**.  
  
    Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2. Erweitern Sie die **Visual C#-** Knoten oder die **Visual Basic** Knoten erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
3. In der **Vorlagen** wählen die **SharePoint 2010-Projekt** Vorlage.  
  
4. In der **Namen** geben **"TestSiteDef" ein**, und wählen Sie dann die **OK** Schaltfläche.  
  
    Die **SharePoint Customization Wizard** angezeigt wird.  
  
5. Auf der **Geben Sie die Website und Sicherheitsebene für debugging** Seite Geben Sie die URL der SharePoint-Website, in dem Sie die Sitedefinition debuggen möchten, oder verwenden Sie den Standardspeicherort (http://<em>Systemname</em>/).  
  
6. In der **was der Vertrauensebene für diese SharePoint-Lösung ist?** Abschnitt der **als farmlösung bereitstellen** Optionsfeld aus.  
  
    Alle Projekte der Website-Definition müssen als farmlösungen bereitgestellt werden. Weitere Informationen über sandkastenlösungen im Vergleich zu farmlösungen finden Sie unter [Überlegungen zu sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
7. Wählen Sie die **Fertig stellen** Schaltfläche.  
  
    Das Projekt wird im **Projektmappen-Explorer**.  
  
8. In **Projektmappen-Explorer**, wählen Sie den Projektknoten und anschließend auf der Menüleiste die Optionen **Projekt** > **neues Element hinzufügen**.  
  
9. Entweder unter **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
10. In der **Vorlagen** Bereich Wählen Sie die **Websitedefinition** Vorlage lassen die **Namen** als **SiteDefinition1**, und wählen Sie dann die  **Hinzufügen** Schaltfläche.  
  
## <a name="create-a-visual-web-part"></a>Erstellen Sie ein visuelles Webpart
 Als Nächstes erstellen Sie ein visuelles Webpart auf der Hauptseite der Websitedefinition angezeigt werden.  
  
#### <a name="to-create-a-visual-web-part"></a>Erstellen Sie ein visuelles Webpart
  
1.  In **Projektmappen-Explorer**, wählen Sie die **alle Dateien anzeigen** Schaltfläche.  
  
2.  Wählen Sie die **SiteDefinition1** Projektknoten, und anschließend auf der Menüleiste die Optionen **Projekt** > **neues Element hinzufügen**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
3.  Erweitern Sie die **Visual C#-** Knoten oder die **Visual Basic** Knoten erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
4.  Wählen Sie in der Liste der Vorlagen, die **visuelles Webpart** Vorlage, behalten die standardmäßige Namen VisualWebPart1, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Die *VisualWebPart1.ascx* Datei wird geöffnet.  
  
5.  Am unteren Rand *VisualWebPart1.ascx*, fügen Sie das folgende Markup zum Hinzufügen von drei Steuerelementen zum Formular hinzu: ein Textfeld, eine Schaltfläche und einer Bezeichnung:  
  
    ```aspx-csharp  
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
  
6.  Unter *VisualWebPart1.ascx*öffnen die *VisualWebPart1.ascx.cs* Datei (für [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) oder *VisualWebPart1.ascx.vb* (für [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), und klicken Sie dann hinzufügen. Der folgende Code:  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     Dieser Code fügt Funktionen für das Webpart-Schaltflächen-Klickereignis hinzu.  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Hinzufügen von visuellen Webparts die ASPX-Standardseite
 Als Nächstes fügen Sie das visuelle Webpart die Websitedefinition Standard-ASPX-Seite hinzu.  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Die Standard-ASPX-Seite ein visuelles Webpart hinzu
  
1.  Öffnen Sie die Seite "default.aspx", und fügen Sie dann die folgende Zeile unter der `WebPartPages` Tag:  
  
    ```aspx-csharp  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Diese Zeile ordnet den Namen MyWebPartControls mit Webparts und den Code an. Die *Namespace* Parameter entspricht den Namespace, der verwendet wird die *VisualWebPart1.ascx* Codedatei.  
  
2.  Nach der `</asp:Content>` Element ersetzen den gesamten `ContentPlaceHolderId="PlaceHolderMain"` Abschnitt und seinen Inhalt mit dem folgenden Code:  
  
    ```aspx-csharp  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     Dieser Code erstellt einen Verweis auf das visuelle Webpart, das Sie zuvor erstellt haben.  
  
3.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SiteDefinition1** Knoten, und wählen Sie dann **als Startelement festlegen**.  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>Bereitstellen Sie und führen Sie der Sitedefinition aus
 Als Nächstes bereitstellen Sie das Projekt für SharePoint, und führen Sie das Projekt.  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>So stellen Sie die Websitedefinition bereit und führen sie aus  
  
-   Wählen Sie auf der Menüleiste **erstellen** > **bereitstellen "TestSiteDef" ein**.  
  
-   Drücken Sie die Taste **F5**.  
  
     Visual Studio wird der Code kompiliert, seine Funktionen hinzugefügt, fasst alle Dateien in einer SharePoint-Lösungsdatei (WSP) und die WSP-Datei auf SharePoint-Server bereitgestellt. SharePoint klicken Sie dann die Dateien installiert und aktiviert die Funktionen.  
  
## <a name="create-a-site-based-on-the-site-definition"></a>Erstellen einer Website, die basierend auf der Websitedefinition
 Als Nächstes erstellen Sie einen Standort mithilfe der neuen Websitedefinition.  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>Zum Erstellen einer Website unter Verwendung der Websitedefinition  
  
1.  Auf der SharePoint-Website die neue SharePoint-Website-Seite wird angezeigt.  
  
2.  In der **Titel und Beschreibung** Geben Sie im Abschnitt **meine neue Website** für den Titel und eine Beschreibung des Standorts.  
  
3.  In der **Websiteadresse** Geben Sie im Abschnitt **MeineNeueSite** in die **URL-Namen** Feld.  
  
4.  In der **Vorlage** Abschnitt der **SharePoint-Anpassungen** Registerkarte.  
  
5.  In der **wählen Sie eine Vorlage** wählen **SiteDefinition1**.  
  
6.  Behalten Sie die anderen Einstellungen die Standardwerte bei, und wählen Sie dann die **erstellen** Schaltfläche.  
  
     Die neue Website wird angezeigt.  
  
## <a name="test-the-new-site"></a>Testen der neuen Website
 Als Nächstes testen Sie den neuen Standort aus, um zu überprüfen, ob sie ordnungsgemäß funktioniert.  
  
#### <a name="to-test-the-new-site"></a>So testen Sie den neuen Standort  
  
-   Geben Sie Text, auf die Standard-ASPX-Seite, und wählen Sie dann die **Änderung Bezeichnungstext** Schaltfläche neben dem Textfeld.  
  
     Der Text wird in der Bezeichnung auf der rechten Seite der Schaltfläche angezeigt.  
  
## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)   
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)  
