---
title: 'Exemplarische Vorgehensweise: Aufrufe in der SharePoint-Clientobjektmodell innerhalb einer Server-Explorererweiterung | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b140a1dcadd86ed8d4c3634669ecf753ad84e25e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873599"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Exemplarische Vorgehensweise: Aufrufe in der SharePoint-Clientobjektmodell innerhalb einer Server-explorererweiterung
  Diese exemplarische Vorgehensweise veranschaulicht, wie Sie das SharePoint-Clientobjektmodell von eine Erweiterung für die **SharePoint-Verbindungen** Knoten **Server-Explorer**. Weitere Informationen zur Verwendung des SharePoint-Clientobjektmodells finden Sie unter [rufen Sie in der SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung, die erweitert die **SharePoint-Verbindungen** Knoten **Server-Explorer** auf folgende Weise:  
  
    -   Fügt die Erweiterung eine **Webpartkatalog** Knoten unter jeder SharePoint-Websiteknoten im **Server-Explorer**. Dieser neue Knoten enthält untergeordnete Knoten, die jedes Webpart in der Webpart-Katalog auf der Website darstellen.  
  
    -   Die Erweiterung definiert eine neue Art von Knoten, der eine Webpart-Instanz darstellt. Diese neuen Knotentyp ist die Grundlage für die untergeordneten Knoten unter der neuen **Webpartkatalog** Knoten. Die neue Webpart-Knotentyp zeigt Informationen auf der **Eigenschaften** Fenster über das Webpart, das den Knoten darstellt.  
  
-   Erstellen eines Visual Studio-Erweiterung (VSIX) zum Bereitstellen der Erweiterung.  
  
-   Das Debuggen und Testen der Erweiterung.  
  
> [!NOTE]  
>  Die Erweiterung, die Sie in dieser exemplarischen Vorgehensweise erstellen, ähnelt der Erweiterung, die Sie, in erstellen [Exemplarische Vorgehensweise: Erweitern Sie Server-Explorer, um die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). Diese exemplarische Vorgehensweise verwendet das SharePoint-Serverobjektmodell, aber in dieser exemplarischen Vorgehensweise führt dieselben Aufgaben mithilfe des Clientobjektmodells.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von Windows, SharePoint und Visual Studio.
  
-   Das Visual Studio SDK. Diese exemplarische Vorgehensweise verwendet die **VSIX-Projekt** Vorlage in das SDK zum Erstellen eines VSIX-Pakets zum Bereitstellen der Erweiterung. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Verwenden das SharePoint-Clientobjektmodell. Weitere Informationen finden Sie unter [verwaltetes Clientobjektmodell](http://go.microsoft.com/fwlink/?LinkId=177797).  
  
-   Webparts in SharePoint. Weitere Informationen finden Sie unter [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="create-the-projects"></a>Erstellen Sie die Projekte
 Um diese exemplarische Vorgehensweise abzuschließen, müssen Sie zwei Projekte erstellen:  
  
- Ein VSIX-Projekt zum Erstellen von VSIX-Paket zum Bereitstellen der **Server-Explorer** Erweiterung.  
  
- Ein Klassenbibliotheksprojekt, das implementiert die **Server-Explorer** Erweiterung.  
  
  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.  
  
3.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann **Erweiterbarkeit**.  
  
    > [!NOTE]  
    >  Die **Erweiterbarkeit** Knoten ist nur verfügbar, wenn Sie Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.  
  
4.  Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 4.5** in der Liste der Versionen von .NET Framework.  
  
     SharePoint-Tools-Erweiterungen werden die Funktionen in dieser Version von .NET Framework erfordern.  
  
5.  Wählen Sie die **VSIX-Projekt** Vorlage.  
  
6.  In der **Namen** geben **WebPartNode**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **WebPartNode** Projekt **Projektmappen-Explorer**.  
  
#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen **hinzufügen**, und wählen Sie dann **neues Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann **Windows**.  
  
3.  Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 4.5** in der Liste der Versionen von .NET Framework.  
  
4.  Wählen Sie in der Liste der Projektvorlagen das Projekt **Klassenbibliothek**.  
  
5.  In der **Namen** geben **WebPartNodeExtension**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **WebPartNodeExtension** -Projekt zur Projektmappe und öffnet die Class1-Codedatei.  
  
6.  Löschen Sie die Class1-Codedatei aus dem Projekt.  
  
## <a name="configure-the-extension-project"></a>Konfigurieren Sie das Erweiterungsprojekt
 Bevor Sie Code zum Erstellen der Erweiterung schreiben, müssen Sie Codedateien und Assemblyverweise in Ihrem Projekt hinzufügen und müssen Sie den Standardnamespace aktualisieren.  
  
#### <a name="to-configure-the-project"></a>So konfigurieren Sie das Projekt  
  
1.  In der **WebPartNodeExtension** fügen zwei Codedateien, die SiteNodeExtension und WebPartNodeTypeProvider benannt sind.  
  
2.  Öffnen Sie das Kontextmenü für das Projekt WebPartNodeExtension, und wählen Sie dann **Verweis hinzufügen**.  
  
3.  In der **Verweis-Manager - WebPartNodeExtension** Dialogfeld auf die **Framework** Knoten, und wählen Sie dann die Kontrollkästchen für System.ComponentModel.Composition und "System.Windows.Forms" Assemblys.  
  
4.  Wählen Sie die **Erweiterungen** Knoten, wählen Sie das Kontrollkästchen für jede der folgenden Assemblys, und wählen Sie dann die **OK** Schaltfläche:  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Öffnen Sie das Kontextmenü für die **WebPartNodeExtension** Projekt, und wählen Sie dann **Eigenschaften**.  
  
     Der **Projekt-Designer** wird geöffnet.  
  
6.  Wählen Sie die Registerkarte **Anwendung** aus.  
  
7.  In der **Standardnamespace** Kontrollkästchen (c#) oder **Stammnamespace** (Visual Basic) Geben Sie **Wert ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="create-icons-for-the-new-nodes"></a>Symbole für den neuen Knoten erstellen
 Erstellen Sie zwei Symbole für die **Server-Explorer** Erweiterung: ein Symbol für das neue **Webpartkatalog** Knoten und ein anderes Symbol für jeden untergeordneten Webpart-Knoten unter dem **Webpartkatalog** Knoten. Weiter unten in dieser exemplarischen Vorgehensweise schreiben Sie Code, der diese Symbole mit den Knoten zuordnet.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Symbole für die Knoten zu erstellen  
  
1.  In der **Projekt-Designer** wählen Sie für das Projekt WebPartNodeExtension der **Ressourcen** Registerkarte.  
  
2.  Wählen Sie den Link **dieses Projekt enthält keine Standardressourcendatei. Klicken Sie hier, um eine zu erstellen.**  
  
     Visual Studio erstellt eine Ressourcendatei und öffnet es im Designer.  
  
3.  Am oberen Rand des Designers, wählen Sie den Pfeil auf der **Ressource hinzufügen** Menü Befehl aus, und wählen Sie dann **neues Symbol hinzufügen**.  
  
4.  Geben Sie **WebPartsNode als Namen** für das Symbol "Neu" nennen, und klicken Sie dann auf die **hinzufügen** Schaltfläche.  
  
     Das Symbol "Neu" geöffnet, der **Bildbearbeitung**.  
  
5.  Bearbeiten Sie die 16 x 16-Version des Symbols, sodass sie einen Entwurf aufweist, den Sie leicht erkennen können.  
  
6.  Öffnen Sie das Kontextmenü für die 32 x 32-Version des Symbols, und wählen Sie dann **Bildtyp löschen**.  
  
7.  Wiederholen Sie Schritte 3 bis 7, um ein Symbol den Projektressourcen hinzuzufügen, und nennen Sie dieses Symbol **WebPart**.  
  
8.  In **Projektmappen-Explorer**in die **Ressourcen** Ordner für die **WebPartNodeExtension** Projekts *Datei WebPartsNode.ico*.  
  
9. In der **Eigenschaften** geöffnete Fenster die **Buildvorgang** aus, und klicken Sie dann auf **eingebettete Ressource**.  
  
10. Wiederholen Sie die letzten beiden Schritte für *WebPart.ico*.  
  
## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Fügen Sie den Webpart Gallery-Knoten zum Server-Explorer
 Erstellen Sie eine Klasse, die die neue hinzufügt **Webpartkatalog** Knoten aus, um jede SharePoint-Websiteknoten. Zum Hinzufügen des neuen Knotens, der die Klasse implementiert die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Schnittstelle. Diese Schnittstelle implementieren, wenn Sie das Verhalten von einem vorhandenen Knoten in erweitern möchten **Server-Explorer**, z. B. einen neuen untergeordneten Knoten auf einen Knoten hinzufügen.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Server-Explorer den Webpart Gallery-Knoten hinzu
  
1.  Fügen Sie den folgenden Code in die **SiteNodeExtension** Codedatei für die **WebPartNodeExtension** Projekt.  
  
    > [!NOTE]  
    >  Nach dem Hinzufügen dieses Codes weist das Projekt einige Kompilierungsfehler auf. Diese Fehler werden durch Code behoben, den Sie in späteren Schritten hinzufügen.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="define-a-node-type-that-represents-a-web-part"></a>Definieren Sie einen Knotentyp, der ein Webpart darstellt.
 Erstellen Sie eine Klasse, die eine neue Art von Knoten definiert, die ein Webpart darstellt. Visual Studio verwendet diesen neuen Knotentyp zum Anzeigen der untergeordneten Knoten unter dem **Webpartkatalog** Knoten. Jeder dieser untergeordnete Knoten stellt ein einzelnes Webpart auf der SharePoint-Website.  
  
 Definieren Sie den neuen Knotentyp, die Klasse implementiert die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Schnittstelle. Diese Schnittstelle implementieren, wenn Sie eine neue Art von Knoten in definieren möchten **Server-Explorer**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Definiert den Webpart-Knotentyp
  
1.  Fügen Sie den folgenden Code in die **WebPartNodeTypeProvider** Codedatei für die **WebPartNodeExtension** Projekt.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## <a name="checkpoint"></a>Checkpoint  
 An diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte Code für die **Webpartkatalog** Knoten befindet sich jetzt im Projekt. Erstellen der **WebPartNodeExtension** Projekt, um sicherzustellen, dass es ohne Fehler kompiliert wird.  
  
#### <a name="to-build-the-project"></a>So erstellen Sie das Projekt  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **WebPartNodeExtension** Projekt, und wählen Sie dann **erstellen**.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Erstellen Sie ein VSIX-Paket zum Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX-Projekts in der Lösung ein VSIX-Paket. Konfigurieren Sie zuerst das VSIX-Paket durch Ändern der Datei "Source.Extension.vsixmanifest", die im Projekt enthalten ist. Klicken Sie dann erstellen Sie das VSIX-Paket, indem Sie beim Erstellen der Projektmappe.  
  
#### <a name="to-configure-the-vsix-package"></a>So konfigurieren Sie das VSIX-Paket  
  
1.  In **Projektmappen-Explorer**in die **WebPartNode** geöffneten Projekt **"Source.Extension.vsixmanifest"** Datei im manifest-Editor.  
  
     Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie unter [Referenz zum VSIX-Erweiterungsschema 1.0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  In der **Produktname** geben **Web Part Gallery Node für Server-Explorer**.  
  
3.  In der **Autor** geben **Contoso**.  
  
4.  In der **Beschreibung** geben **Fügt einen benutzerdefinierten Webpartkatalog-Knoten auf der SharePoint-Verbindungsknotens im Server-Explorer**.  
  
5.  Auf der **Assets** Registerkarte des Editors wählen Sie die **neu** Schaltfläche.  
  
6.  In der **neue Anlage hinzufügen** Dialogfeld die **Typ** wählen **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.  
  
8.  In der **Projekt** wählen **WebPartNodeExtension**, und wählen Sie dann die **OK** Schaltfläche.  
  
9. Wählen Sie auf der Menüleiste **erstellen** > **Projektmappe**, und klicken Sie dann stellen Sie sicher, dass die Projektmappe ohne Fehler kompiliert wird.  
  
10. Stellen Sie sicher, dass der Buildausgabeordner für das Projekt WebPartNode jetzt die Datei WebPartNode.VSIX enthält.  
  
     Standardmäßig handelt es sich beim Buildausgabeordner um den Ordner "...\bin\Debug" in dem Ordner mit der Projektdatei.  
  
## <a name="test-the-extension"></a>Testen Sie die Erweiterung
 Sie können nun den neuen test **Webpartkatalog** Knoten **Server-Explorer**. Starten Sie zunächst das Erweiterungsprojekt in einer experimentellen Instanz von Visual Studio zu debuggen. Verwenden Sie dann auf die neue **Webparts** Knoten in der experimentellen Instanz von Visual Studio.  
  
#### <a name="to-start-debugging-the-extension"></a>So debuggen Sie die Erweiterung  
  
1.  Starten Sie Visual Studio mit Administratorrechten, und öffnen Sie die **WebPartNode** Lösung.  
  
2.  Öffnen Sie in das Projekt WebPartNodeExtension der **SiteNodeExtension** Codedatei, und fügen Sie einen Haltepunkt klicken Sie dann auf die ersten Zeilen des Codes in der `NodeChildrenRequested` und `CreateWebPartNodes` Methoden.  
  
3.  Wählen Sie die **F5** Schlüssel mit dem Debuggen beginnen.  
  
     Visual Studio wird die Erweiterung installiert wird, um %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Part Gallery-Knoten-Erweiterung für Server Explorer\1.0 und eine experimentelle Instanz von Visual Studio. Sie testen das Projektelement in dieser Instanz von Visual Studio.  
  
#### <a name="to-test-the-extension"></a>So testen Sie die Erweiterung  
  
1.  Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste **Ansicht** > **Server-Explorer**.  
  
2.  Stellen Sie sicher, dass die SharePoint-Website, die Sie für Tests verwenden möchten, die unter angezeigt wird der **SharePoint-Verbindungen** Knoten **Server-Explorer**. Wenn sie nicht aufgeführt ist, gehen Sie wie folgt vor:  
  
    1.  Öffnen Sie das Kontextmenü für **SharePoint-Verbindungen**, und wählen Sie dann **Verbindung hinzufügen**.  
  
    2.  In der **SharePoint-Verbindung hinzufügen** Dialogfeld Geben Sie die URL für die SharePoint-Website, die Sie möchten eine Verbindung herstellen, und wählen Sie dann die **OK** Schaltfläche.  
  
         Geben Sie zum Angeben der SharePoint-Website auf Ihrem Entwicklungscomputer **http://localhost**.  
  
3.  Erweitern Sie den Website-Verbindungsknoten (in der die URL Ihrer Website angezeigt wird), und klicken Sie dann einen untergeordneten Standort Knoten (z. B. **Teamwebsite**).  
  
4.  Stellen Sie sicher, dass die codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, die Sie zuvor im Festlegen der `NodeChildrenRequested` -Methode, und wählen Sie dann die **F5** Schlüssel, um das Debuggen des Projekts fortzusetzen.  
  
5.  Erweitern Sie in der experimentellen Instanz von Visual Studio die **Webpartkatalog** Knoten, der unter dem Knoten für Standort der obersten Ebene angezeigt wird.  
  
6.  Stellen Sie sicher, dass die codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, die Sie zuvor im Festlegen der `CreateWebPartNodes` -Methode, und wählen Sie dann die **F5** Schlüssel, um das Debuggen des Projekts fortzusetzen.  
  
7.  In der experimentellen Instanz von Visual Studio, stellen Sie sicher, dass alle Webparts der verbundenen Website angezeigt, unter werden dem **Webpartkatalog** Knoten **Server-Explorer**.  
  
8.  Öffnen Sie das Kontextmenü für ein Webpart ein, und wählen Sie dann **Eigenschaften**.  
  
9. In der **Eigenschaften** Fenster, stellen Sie sicher, dass Informationen über das Webpart angezeigt werden.  
  
10. In **Server-Explorer**, öffnen Sie das Kontextmenü für das gleiche Webpart ein, und wählen Sie dann **Meldung anzeigen**.  
  
     Wählen Sie in das Meldungsfeld wird angezeigt, die **OK** Schaltfläche.  
  
## <a name="uninstall-the-extension-from-visual-studio"></a>Deinstallieren Sie die Erweiterung von Visual Studio
 Nach dem Testen der Erweiterungs, deinstallieren Sie es in Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>So deinstallieren Sie die Erweiterung  
  
1.  Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste **Tools** > **Erweiterungen und Updates**.  
  
     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.  
  
2.  Wählen Sie in der Liste der Erweiterungen, **Web Part Gallery Node für Server-Explorer**, und wählen Sie dann die **Deinstallieren** Schaltfläche.  
  
3.  Wählen Sie in das Dialogfeld, das angezeigt wird, die **Ja** Schaltfläche.  
  
4.  Wählen Sie die **jetzt neu starten** Schaltfläche, um die Deinstallation abzuschließen.  
  
     Das Projektelement wird ebenfalls deinstalliert.  
  
5.  Schließen Sie beide Instanzen von Visual Studio (die experimentelle Instanz und die Instanz von Visual Studio, in dem die Projektmappe WebPartNode geöffnet ist).  
  
## <a name="see-also"></a>Siehe auch
 [Rufen Sie in der SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Exemplarische Vorgehensweise: Erweitern Sie Server-Explorer, um die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Bildbearbeitung für Symbole](/cpp/windows/image-editor-for-icons)   
 [Erstellen eines Symbols oder anderen Bilds &#40;Bildbearbeitung für Symbole&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)