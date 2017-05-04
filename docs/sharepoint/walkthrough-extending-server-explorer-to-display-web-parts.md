---
title: "Walkthrough: Extending Server Explorer to Display Web Parts | Microsoft Docs"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 5b1f104a-0eaf-4929-9f1f-d7afcfc8b707
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Walkthrough: Extending Server Explorer to Display Web Parts
  In Visual Studio können Sie den Knoten **SharePoint\-Verbindungen** von **Server\-Explorer** verwenden, um Komponenten auf SharePoint\-Websites anzuzeigen.  wird jedoch nicht **Server\-Explorer** einige Komponenten standardmäßig an.  In dieser exemplarischen Vorgehensweise erweitern Sie **Server\-Explorer**, dass es den Webpartkatalog jeder verbundenen SharePoint\-Website angezeigt wird.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer Visual Studio\-Erweiterung, die den **Server\-Explorer** auf folgende Weise erweitert:  
  
    -   Die Erweiterung wird ein Knoten **Webpartkatalog** unter jedem SharePoint\-Websiteknoten in **Server\-Explorer** hinzu.  Dieser neue Knoten enthält untergeordnete Knoten, die jedes Webpart im Webpartkatalog auf der Website darstellen.  
  
    -   Die Erweiterung wird ein neuer Knotentyp definiert, der eine Webpart\-Instanz darstellt.  Dieser neue Knotentyp ist die Grundlage für die untergeordneten Knoten unter dem neuen Knoten **Webpartkatalog**.  Der neue Webpartknotentyp zeigt im **Eigenschaftenfenster** Informationen zum zugehörigen Webpart an.  Der Knotentyp umfasst auch ein benutzerdefiniertes Kontextmenüelement, das Sie als Ausgangspunkt zum Ausführen anderer Aufgaben verwenden können, die dem Webpart verknüpfen.  
  
-   Zwei benutzerdefinierte SharePoint\-Befehle erstellen, die die Erweiterungsassembly aufruft.  SharePoint\-Befehle sind Methoden, die von Erweiterungsassemblys aufgerufen werden können, um APIs im Serverobjektmodell für SharePoint zu verwenden.  In dieser exemplarischen Vorgehensweise erstellen Sie Befehle, die Webpartinformationen von der lokalen SharePoint\-Website auf dem Entwicklungscomputer abrufen.  Weitere Informationen finden Sie unter [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Erstellen eines Visual Studio\-Erweiterungspakets \(VSIX\) zum Bereitstellen der Erweiterung.  
  
-   Debuggen und Testen der Erweiterung.  
  
> [!NOTE]  
>  Eine alternative Version dieser exemplarischen Vorgehensweise, die das Clientobjektmodell für SharePoint anstelle des Serverobjektmodells verwendet, finden Sie unter [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von Windows, SharePoint und Visual Studio.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Das Visual Studio SDK.  Bei dieser exemplarischen Vorgehensweise wird mithilfe der Vorlage **VSIX Project** aus dem SDK ein VSIX\-Paket zum Bereitstellen des Projektelements erstellt.  Weitere Informationen finden Sie unter [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Verwenden des Serverobjektmodells für SharePoint.  Weitere Informationen finden Sie im Thema zur [Verwendung des serverseitigen SharePoint Foundation\-Objektmodells](http://go.microsoft.com/fwlink/?LinkId=177796) \(möglicherweise in englischer Sprache\).  
  
-   Webparts in SharePoint\-Lösungen.  Weitere Informationen finden Sie in der [Übersicht über Webparts](http://go.microsoft.com/fwlink/?LinkId=177803) \(möglicherweise in englischer Sprache\).  
  
## Erstellen der Projekte  
 Um diese exemplarische Vorgehensweise abzuschließen, müssen Sie drei Projekte erstellen:  
  
-   Ein VSIX\-Projekt für die Erstellung des VSIX\-Pakets zum Bereitstellen der Erweiterung.  
  
-   Ein Klassenbibliotheksprojekt, von dem die Erweiterung implementiert wird.  Dieses Projekt muss .NET Framework 4.5 abzielen.  
  
-   Ein Klassenbibliotheksprojekt, das die benutzerdefinierten SharePoint\-Befehle definiert.  Für dieses Projekt muss .NET Framework 3.5 als Zielversion verwendet werden.  
  
 Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### So erstellen Sie das VSIX\-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
3.  Im Dialogfeld  **Neues Projekt** erweitern Sie die **Visual C\#** oder Knoten **Visual Basic**, und wählen Sie dann den Knoten **Erweiterungen** aus.  
  
    > [!NOTE]  
    >  Der Knoten **Erweiterungen** ist nur verfügbar, wenn Sie das Visual Studio SDK installieren.  Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.  
  
4.  am oberen Rand des Dialogfelds wählen Sie **.NET Framework 4.5** in der Liste der Versionen von .NET Framework aus.  
  
5.  Wählen Sie die **VSIX\-Projekt** Vorlage aus, geben Sie das Projekt **WebPartNode**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **WebPartNode** zum **Projektmappen\-Explorer** hinzu.  
  
#### So erstellen Sie das Erweiterungsprojekt  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** aus und wählen dann **Neues Projekt** aus.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten wird der Projektmappenknoten nur im **Projektmappen\-Explorer** angezeigt, wenn das Kontrollkästchen **Projektmappe immer anzeigen** in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/de-de/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) aktiviert ist.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C\#** oder den Knoten **Visual Basic**, und wählen Sie dann den Knoten **Windows** aus.  
  
3.  am oberen Rand des Dialogfelds wählen Sie **.NET Framework 4.5** in der Liste der Versionen von .NET Framework aus.  
  
4.  In der Liste der Projektvorlagen, wählen Sie **Klassenbibliothek** aus, nennen Sie das Projekt **WebPartNodeExtension**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **WebPartNodeExtension** der Projektmappe hinzu und öffnet die standardmäßige Class1\-Codedatei.  
  
5.  Löschen Sie die Class1\-Codedatei aus dem Projekt.  
  
#### So erstellen Sie das SharePoint\-Befehlsprojekt  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** aus und wählen dann **Neues Projekt** aus.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten wird der Projektmappenknoten nur im **Projektmappen\-Explorer** angezeigt, wenn das Kontrollkästchen **Projektmappe immer anzeigen** in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/de-de/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) aktiviert ist.  
  
2.  Im Dialogfeld  **Neues Projekt** erweitern Sie den Knoten **Visual C\#** oder Knoten **Visual Basic**, und wählen Sie dann den Knoten **Fenster** aus.  
  
3.  am oberen Rand des Dialogfelds wählen Sie **.NET Framework 3.5** in der Liste der Versionen von .NET Framework aus.  
  
4.  In der Liste der Projektvorlagen, wählen Sie **Klassenbibliothek** aus, nennen Sie das Projekt **WebPartCommands**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **WebPartCommands** zur aktuellen Projektmappe hinzu und öffnet die Class1\-Codedatei.  
  
5.  Löschen Sie die Class1\-Codedatei aus dem Projekt.  
  
## Konfigurieren der Projekte  
 Bevor Sie Code schreiben, um die Erweiterung zu erstellen, müssen Sie Codedateien und Assemblyverweise hinzufügen und konfigurieren.  
  
#### So konfigurieren Sie das Projekt "WebPartNodeExtension"  
  
1.  Fügen Sie im Projekt "WebPartNodeExtension" vier Codedateien hinzu, die die folgenden Namen aufweisen:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Öffnen Sie das Kontextmenü für das **WebPartNodeExtension** Projekt, und wählen Sie dann **Verweis hinzufügen** aus.  
  
3.  Im Dialogfeld **Verweis\-Manager – WebPartNodeExtensionFramework** wählen Sie die Registerkarte aus, und aktivieren Sie dann das Kontrollkästchen für jede der folgenden Assemblys aus:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  Wählen Sie die Registerkarte aus **Erweiterungen**, aktivieren Sie das Kontrollkästchen für die Microsoft.VisualStudio.SharePoint\-Assembly aus, und wählen Sie dann die Schaltfläche **OK** aus.  
  
5.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für den **WebPartNodeExtension** Projektknoten, und wählen Sie dann **Eigenschaften** aus.  
  
     Der **Projekt\-Designer** wird geöffnet.  
  
6.  Wählen Sie die Registerkarte aus. **Anwendung**  
  
7.  **Standardnamespace** im Feld \(C\#\) oder in Feld **Stammnamespace** \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\), geben Sie **ServerExplorer.SharePointConnections.WebPartNode** ein.  
  
#### So konfigurieren Sie das Projekt WebPartCommands  
  
1.  Fügen Sie im Projekt WebPartCommands eine Codedatei hinzu, die WebPartCommands ".  
  
2.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für den **WebPartCommands** Projektknoten, wählen Sie **Hinzufügen** aus und wählen dann **Vorhandenes Element** aus.  
  
3.  Im Dialogfeld **Vorhandenes Element hinzufügen** navigieren Sie zu dem Ordner, der die Codedateien für das Projekt "WebPartNodeExtension" enthält, und wählen Sie dann die Codedateien WebPartNodeInfo und WebPartCommandIds aus.  
  
4.  Wählen Sie den Pfeil neben der Schaltfläche **Hinzufügen** aus, und wählen Sie dann **Als Link hinzufügen** im Menü aus, das angezeigt wird.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt dem Projekt WebPartCommands die Codedateien als Links hinzu.  Folglich sind die Codedateien im Projekt "WebPartNodeExtension", der Code aus den Dateien aber auch im Projekt WebPartCommands kompiliert.  
  
5.  Öffnen Sie das Kontextmenü für das **WebPartCommands** Projekt erneut, und wählen Sie **Verweis hinzufügen** aus.  
  
6.  Im Dialogfeld **Verweis\-Manager – WebPartCommands** wählen Sie die Registerkarte aus **Erweiterungen**, aktivieren Sie das Kontrollkästchen für jede der folgenden Assemblys aus, und wählen Sie dann die Schaltfläche **OK** aus:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für das **WebPartCommands** Projekt erneut, und wählen Sie dann **Eigenschaften** aus.  
  
     Der **Projekt\-Designer** wird geöffnet.  
  
8.  Wählen Sie die Registerkarte aus. **Anwendung**  
  
9. **Standardnamespace** im Feld \(C\#\) oder in Feld **Stammnamespace** \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\), geben Sie **ServerExplorer.SharePointConnections.WebPartNode** ein.  
  
## Erstellen von Symbolen für die neuen Knoten  
 Erstellen Sie zwei Symbole für die **Server\-Explorer**\-Erweiterung: ein Symbol für den neuen Knoten **Webpartkatalog** und ein anderes Symbol für untergeordnete Webpartknoten unter dem Knoten **Webpartkatalog**.  Später in dieser exemplarischen Vorgehensweise schreiben Sie Code, der diese Symbole den Knoten zuordnet.  
  
#### So erstellen Sie Symbole für die Knoten  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für das **WebPartNodeExtension** Projekt, und wählen Sie dann **Eigenschaften** aus.  
  
2.  Der **Projekt\-Designer** wird geöffnet.  
  
3.  Wählen Sie die Registerkarte **Ressourcen** aus, und wählen Sie dann den Link **Dieses Projekt enthält keine Standardressourcendatei. Klicken Sie hier, um eine zu erstellen** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt eine Ressourcendatei und öffnet sie im Designer.  
  
4.  am oberen Rand des Designers wählen Sie den Pfeil neben dem **Ressource hinzufügen** Menübefehl aus, und wählen Sie dann **Neues Symbol hinzufügen** im Menü aus, das angezeigt wird.  
  
5.  Im Dialogfeld **Neue Ressource hinzufügen** geben Sie das neue Symbol **WebPartsNode**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Das neue Symbol wird in der **Bildbearbeitung** geöffnet.  
  
6.  Bearbeiten Sie die 16x16\-Version des Symbols, dass es einen Entwurf aufweist, den Sie leicht erkennen können.  
  
7.  Öffnen Sie das Kontextmenü für die 32x32\-Version des Symbols, und wählen Sie dann **Bildtyp löschen** aus.  
  
8.  Wiederholen Sie die Schritte 5 bis 8, um den Projektressourcen ebenfalls ein Symbol hinzuzufügen, und benennen Sie dieses Symbol **Webpart**.  
  
9. In **Projektmappen\-ExplorerRessourcen** unter dem Ordner für das Projekt **WebPartNodeExtension**, öffnen Sie das Kontextmenü für **WebPartsNode.ico**.  
  
10. Im **Eigenschaften** Sie im auf den Pfeil neben **Buildvorgang** aus, und wählen Sie dann **Eingebettete Ressource** im Menü aus, das angezeigt wird.  
  
11. Wiederholen Sie die letzten zwei Schritte für **WebPart.ico**.  
  
## Hinzufügen des Webpartkatalogknotens zum Server\-Explorer  
 Erstellen Sie eine Klasse, die jedem SharePoint\-Websiteknoten den neuen Knoten **Webpartkatalog** hinzufügt.  Zum Hinzufügen des neuen Knotens implementiert die Klasse die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>\-Schnittstelle.  Implementieren Sie diese Schnittstelle immer dann, wenn Sie das Verhalten eines vorhandenen Knotens in **Server\-Explorer** erweitern möchten, wie Hinzufügen eines untergeordneten Knoten zu einem Knoten.  
  
#### So fügen Sie den Webpartkatalogknoten zum Server\-Explorer hinzu  
  
1.  Öffnen Sie im Projekt "WebPartNodeExtension" die SiteNodeExtension\-Codedatei, und fügen Sie dann den folgenden Code in die ein.  
  
    > [!NOTE]  
    >  Nachdem Sie diesen Code hinzufügen, weist das Projekt mehrere Compilerfehler, aber sie wechseln weg, wenn Sie Code in späteren Schritten hinzufügen.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## Definieren eines Knotentyps, der ein Webpart darstellt  
 Erstellen Sie eine Klasse, die einen neuen Knotentyp definiert, der ein Webpart darstellt.  Visual Studio verwendet diesen neuen Knotentyp, um untergeordnete Knoten unter dem Knoten **Webpartkatalog** anzuzeigen.  Jeder untergeordnete Knoten stellt ein einzelnes Webpart auf der SharePoint\-Website.  
  
 Um den neuen Knotentyp zu definieren, implementiert die Klasse die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>\-Schnittstelle.  Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen neuen Knotentyp im **Server\-Explorer** definieren möchten.  
  
#### So definieren Sie den Webpartknotentyp  
  
1.  Öffnen Sie im Projekt "WebPartNodeExtension" die WebPartNodeTypeProvder\-Codedatei, und fügen Sie dann den folgenden Code in die ein.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## Definieren der Webpart\-Datenklasse  
 Definieren Sie eine Klasse, die die Daten für ein einzelnes Webpart auf der SharePoint\-Website enthält.  Später in dieser exemplarischen Vorgehensweise, erstellen Sie einen benutzerdefinierten SharePoint\-Befehl, der Daten zu jedem Webpart auf der Website abruft und die Daten anschließend Instanzen dieser Klasse zuweist.  
  
#### So definieren Sie die Webpart\-Datenklasse  
  
1.  Öffnen Sie im Projekt "WebPartNodeExtension" die WebPartNodeInfo\-Codedatei, und fügen Sie dann den folgenden Code in die ein.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodeinfo.cs#3)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodeinfo.vb#3)]  
  
## Definieren der IDs für den SharePoint\-Befehl  
 Definieren Sie mehrere Zeichenfolgen, die die benutzerdefinierten SharePoint\-Befehle identifizieren.  Sie implementieren die Befehle später in dieser exemplarischen Vorgehensweise.  
  
#### So definieren Sie die Befehls\-IDs  
  
1.  Öffnen Sie im Projekt "WebPartNodeExtension" die WebPartCommandIds\-Codedatei, und fügen Sie dann den folgenden Code in die ein.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartcommandids.vb#4)]  
  
## Erstellen der benutzerdefinierten SharePoint\-Befehle  
 Erstellen Sie benutzerdefinierte Befehle, die in das Serverobjektmodell aufrufen, damit SharePoint Daten über die Webparts auf der SharePoint\-Website abruft.  Jeder Befehl ist eine Methode, auf die das <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> angewendet wurde.  
  
#### So definieren Sie die SharePoint\-Befehle  
  
1.  Öffnen Sie im Projekt WebPartCommands die WebPartCommands\-Codedatei, und fügen Sie dann den folgenden Code in die ein.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartcommands/webpartcommands.vb#6)]  
  
## Checkpoint  
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der ganze für den Knoten **Webpartkatalog** und die SharePoint\-Befehle benötigte Code in das Projekt eingefügt.  Erstellen Sie die Projektmappe, um sicherzustellen, dass beide Projekte ohne Fehler kompiliert werden.  
  
#### So erstellen Sie die Projektmappe  
  
1.  Klicken Sie auf der Menüleiste wählen Sie **Erstellen**, **Projektmappe erstellen** aus.  
  
    > [!WARNING]  
    >  Zu diesem Zeitpunkt enthält das Projekt WebPartNode möglicherweise einen Buildfehler, da die VSIX\-Manifestdatei keinen Wert für Autor verfügt.  Dieser Fehler wird weg, wenn Sie einen Wert in späteren Schritten hinzufügen.  
  
## Erstellen eines VSIX\-Pakets zum Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX\-Projekts in der Lösung ein VSIX\-Paket.  Konfigurieren Sie zuerst das VSIX\-Paket, indem Sie die source.extension.vsixmanifest\-Datei im VSIX\-Projekt ändern.  Erstellen Sie anschließend das VSIX\-Paket, indem Sie die Lösung erstellen.  
  
#### So konfigurieren Sie das VSIX\-Paket  
  
1.  In **Projektmappen\-Explorer** unter dem Knoten, öffnen Sie die Datei **source.extension.vsixmanifest** im Manifest\-Editor.  
  
     Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei, die alle VSIX\-Pakete benötigen.  Weitere Informationen zu dieser Datei finden Sie unter [VSIX\-Erweiterungs\-Schemareferenz](http://msdn.microsoft.com/de-de/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Im Feld geben Sie **ProduktnameWebpartkatalog\-Knoten für Server\-Explorer** ein.  
  
3.  Im Feld geben Sie **AutorContoso** ein.  
  
4.  Im Feld **Beschreibung** geben Sie **Fügt dem Knoten SharePoint\-Verbindungen im Server\-Explorer einen benutzerdefinierten Webpartkatalogknoten hinzu ein. This extension uses a custom SharePoint command to call into the server object model**.  
  
5.  Wählen Sie die Registerkarte des Editors **Objekte** aus, und wählen Sie dann die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld wird angezeigt. **Neue Anlage hinzufügen**  
  
6.  In der Liste wählen Sie **TypMicrosoft.VisualStudio.MefComponent** aus.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `MefComponent`\-Element in der Datei "extension.vsixmanifest".  Von diesem Element wird der Name einer Erweiterungsassembly im VSIX\-Paket angegeben.  Weitere Informationen finden Sie unter [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/de-de/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  In der Liste wählen Sie **QuelleEin Projekt in der aktuellen Projektmappe** aus.  
  
8.  In der Liste wählen Sie **ProjektWebPartNodeExtension** aus und wählen dann die Schaltfläche **OK** aus.  
  
9. im Manifest\-Editor wählen Sie die Schaltfläche **Neu** erneut aus.  
  
     Das Dialogfeld wird angezeigt. **Neue Anlage hinzufügen**  
  
10. Im Feld geben Sie **TypSharePoint.Commands.v4** ein.  
  
    > [!NOTE]  
    >  Dieses Element gibt eine benutzerdefinierte Erweiterung an, die Sie in die Visual Studio\-Erweiterung einschließen möchten.  Weitere Informationen finden Sie unter [Vermögensteil \(VSX Schema\)](http://msdn.microsoft.com/de-de/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. In der Liste **Quelle** wählen Sie das **Ein Projekt in der aktuellen Projektmappe** Listeneintrag aus.  
  
12. In der Liste wählen Sie **ProjektWebPartCommands** aus und wählen dann die Schaltfläche **OK** aus.  
  
13. Klicken Sie auf der Menüleiste wählen Sie **Erstellen**, **Projektmappe erstellen** aus, und überprüfen Sie, ob die Projektmappe fehlerfrei kompiliert.  
  
14. Stellen Sie sicher, dass der Buildausgabeordner für das Projekt WebPartNode jetzt die Datei WebPartNode.vsix enthält.  
  
     Standardmäßig ist der Buildausgabeordner der  Ordner "\\bin\\Debug" im Ordner mit der Projektdatei.  
  
## Testen der Erweiterung  
 Sie sind nun bereit, den neuen Knoten **Webpartkatalog** in **Server\-Explorer** zu testen.  Debuggen Sie die Erweiterung zunächst in einer experimentellen Instanz von Visual Studio.  Verwenden Sie dann den neuen Knoten **Webparts** in der experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### So debuggen Sie die Erweiterung  
  
1.  Starten Sie neu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit Administratorrechten, und öffnen Sie dann die öffnen.  
  
2.  Öffnen Sie im Projekt "WebPartNodeExtension" die SiteNodeExtension\-Codedatei, und fügen Sie anschließend einen Haltepunkt der ersten Codezeile in den `NodeChildrenRequested` und `CreateWebPartNodes`\-Methoden hinzu.  
  
3.  Drücken Sie die F5\-TASTE, um das Debuggen zu starten.  
  
     Visual Studio installiert die Erweiterung in %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Web Part Gallery Node Extension for Server Explorer\\1.0 und startet eine experimentelle Instanz von Visual Studio.  Sie testen das Projektelement in dieser Instanz von Visual Studio.  
  
#### So testen Sie die Erweiterung  
  
1.  Klicken Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], auf der Menüleiste, wählen Sie **Ansicht**, **Server\-Explorer** aus.  
  
2.  Führen Sie die folgenden Schritte aus, wenn die SharePoint\-Website, die Sie für die Tests verwenden möchten, nicht unter dem Knoten in **SharePoint\-VerbindungenServer\-Explorer** angezeigt:  
  
    1.  In **Server\-Explorer** öffnen Sie das Kontextmenü für **SharePoint\-Verbindungen**, und wählen Sie dann **Verbindung hinzufügen** aus.  
  
    2.  Im Dialogfeld **SharePoint\-Verbindung hinzufügen** geben Sie die URL für die SharePoint\-Website, mit der Sie eine Verbindung herstellen möchten, und wählen Sie dann die Schaltfläche **OK** aus.  
  
         Um die SharePoint\-Website auf dem Entwicklungscomputer anzugeben, geben Sie **http:\/\/localhost** ein.  
  
3.  Erweitern Sie den Website\-Verbindungsknoten \(den die URL der Website angezeigt wird\), und erweitern Sie dann einen untergeordneten Websiteknoten \(beispielsweise, **Teamwebsite**\).  
  
4.  Überprüfen Sie, ob die Codeausführung in der anderen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] auf dem Haltepunkt festgelegt wird, den Sie zuvor in der `NodeChildrenRequested`\-Methode und dann F5 auswählen, um fortfahren, um das Projekt zu debuggen.  
  
5.  Klicken Sie in der experimentellen Instanz von Visual Studio, überprüfen Sie, ob ein neuer Knoten, der **Webpartkatalog** genannt wird, unter dem Websiteknoten der obersten Ebene angezeigt, und erweitern Sie dann den Knoten **Webpartkatalog**.  
  
6.  Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der festgelegt `CreateWebPartNodes`\-Methode und dann die F5\-Taste auswählen, um fortfahren, um das Projekt zu debuggen.  
  
7.  Klicken Sie in der experimentellen Instanz von Visual Studio, stellen Sie sicher, dass alle Webparts der verbundenen Website unter dem Knoten in **WebpartkatalogServer\-Explorer** angezeigt werden.  
  
8.  In **Server\-Explorer** öffnen Sie das Kontextmenü für eines der Webparts, und wählen Sie dann **Eigenschaften** aus.  
  
9. In der Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], die Sie debuggen, überprüfen Sie, ob die Details zum Webpart im **Eigenschaften** angezeigt werden.  
  
## Deinstallieren der Erweiterung aus Visual Studio  
 Nach dem Testen der Erweiterung deinstallieren Sie die Erweiterung aus Visual Studio.  
  
#### So deinstallieren Sie die Erweiterung  
  
1.  Klicken Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], auf der Menüleiste, wählen Sie **Tools**, **Erweiterungen und Updates** aus.  
  
     Das Dialogfeld wird geöffnet. **Erweiterungen und Updates**  
  
2.  In der Liste der Erweiterungen, wählen Sie **Webpartkatalog\-Knoten\-Erweiterung für Server\-Explorer** aus und wählen dann die Schaltfläche **Deinstallieren** aus.  
  
3.  Im Dialogfeld, das angezeigt wird, wählen Sie die Schaltfläche **Ja**, um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten, und wählen Sie dann die Schaltfläche **Jetzt neu starten**, um die Deinstallation abzuschließen.  
  
4.  Schließen Sie beide Instanzen von Visual Studio \(die experimentelle Instanz und die Instanz von Visual Studio, in der die Projektmappe "WebPartNode" geöffnet ist\).  
  
## Siehe auch  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  