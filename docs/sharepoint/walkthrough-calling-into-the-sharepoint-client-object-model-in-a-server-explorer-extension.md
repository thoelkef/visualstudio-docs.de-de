---
title: "Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
ms.assetid: 897d3798-42c1-4fff-b280-8b84b53d80c6
caps.latest.revision: 100
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 96
---
# Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension
  Diese exemplarische Vorgehensweise veranschaulicht, wie das SharePoint\-Clientobjektmodell in einer Erweiterung für den Knoten **SharePoint\-Verbindungen** im **Server\-Explorer** aufgerufen wird.  Weitere Informationen dazu, wie das SharePoint\-Clientobjektmodell, finden Sie unter [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md) verwendet.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterung, die den Knoten **SharePoint\-Verbindungen** im **Server\-Explorer** auf folgende Weise erweitert:  
  
    -   Die Erweiterung wird ein Knoten **Webpartkatalog** unter jedem SharePoint\-Websiteknoten in **Server\-Explorer** hinzu.  Dieser neue Knoten enthält untergeordnete Knoten, die jedes Webpart im Webpartkatalog auf der Website darstellen.  
  
    -   Die Erweiterung wird ein neuer Knotentyp definiert, der eine Webpart\-Instanz darstellt.  Dieser neue Knotentyp ist die Grundlage für die untergeordneten Knoten unter dem neuen Knoten **Webpartkatalog**.  Der neue Webpartknotentyp zeigt im Informationen Fenster **Eigenschaften** zum Webpart an, den der Knoten darstellt.  
  
-   Erstellen eines Visual Studio\-Erweiterungspakets \(VSIX\) zum Bereitstellen der Erweiterung.  
  
-   Debuggen und Testen der Erweiterung.  
  
> [!NOTE]  
>  Die Erweiterung, die Sie in dieser exemplarischen Vorgehensweise erstellen, ähnelt der Erweiterung, die Sie in [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md) erstellen.  In dieser exemplarischen Vorgehensweise das SharePoint\-Serverobjektmodell, aber diese exemplarische Vorgehensweise verwendet, erfüllt die gleichen Aufgaben, indem es das Clientobjektmodell.  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von Windows, SharePoint und Visual Studio.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Das Visual Studio SDK.  Diese exemplarische Vorgehensweise verwendet die Vorlage **VSIX Project** im SDK, um ein VSIX\-Paket zum Bereitstellen der Erweiterung zu erstellen.  Weitere Informationen finden Sie unter [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Verwenden des SharePoint\-Clientobjektmodells.  Weitere Informationen finden Sie im Thema zum [verwalteten Clientobjektmodell](http://go.microsoft.com/fwlink/?LinkId=177797) \(möglicherweise in englischer Sprache\).  
  
-   Webparts in SharePoint.  Weitere Informationen finden Sie in der [Übersicht über Webparts](http://go.microsoft.com/fwlink/?LinkId=177803) \(möglicherweise in englischer Sprache\).  
  
## Erstellen der Projekte  
 Zum Abschließen dieser exemplarischen Vorgehensweise müssen Sie zwei Projekte erstellen:  
  
-   Ein VSIX\-Projekt für die Erstellung des VSIX\-Pakets zum Bereitstellen der **Server\-Explorer**\-Erweiterung.  
  
-   Ein Klassenbibliotheksprojekt, das die **Server\-Explorer**\-Erweiterung implementiert.  
  
 Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### So erstellen Sie das VSIX\-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
3.  Im Dialogfeld **Neues Projekt** erweitern Sie die **Visual C\#** oder Knoten **Visual Basic**, und wählen Sie dann **Erweiterungen** aus.  
  
    > [!NOTE]  
    >  Der Knoten **Erweiterungen** ist nur verfügbar, wenn Sie das Visual Studio SDK installieren.  Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.  
  
4.  am oberen Rand des Dialogfelds wählen Sie **.NET Framework 4.5** in der Liste der Versionen von .NET Framework aus.  
  
     SharePoint\-Toolerweiterungen benötigen Funktionen in dieser Version von .NET Framework.  
  
5.  Wählen Sie die Vorlage aus. **VSIX\-Projekt**  
  
6.  Im Feld wählen **Name**\-Typ **WebPartNode** und dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **WebPartNode** zum **Projektmappen\-Explorer** hinzu.  
  
#### So erstellen Sie das Erweiterungsprojekt  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** aus und wählen dann **Neues Projekt** aus.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten wird der Projektmappenknoten nur im **Projektmappen\-Explorer** angezeigt, wenn das Kontrollkästchen **Projektmappe immer anzeigen** in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/de-de/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) aktiviert ist.  
  
2.  Im Dialogfeld  **Neues Projekt** erweitern Sie die **Visual C\#** oder Knoten **Visual Basic**, und wählen Sie dann **Fenster** aus.  
  
3.  am oberen Rand des Dialogfelds wählen Sie **.NET Framework 4.5** in der Liste der Versionen von .NET Framework aus.  
  
4.  In der Liste der Projektvorlagen, wählen Sie **Klassenbibliothek** aus.  
  
5.  Im Feld geben Sie **NameWebPartNodeExtension** ein und klicken Sie dann auf die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **WebPartNodeExtension** der Projektmappe hinzu und öffnet die standardmäßige Class1\-Codedatei.  
  
6.  Löschen Sie die Class1\-Codedatei aus dem Projekt.  
  
## Konfigurieren des Erweiterungsprojekts  
 Bevor Sie Code schreiben, um die Erweiterung zu erstellen, müssen Sie Codedateien und Assemblyverweise zum Projekt hinzufügen, und Sie müssen den Standardnamespace aktualisieren.  
  
#### So konfigurieren Sie das Projekt  
  
1.  Im **WebPartNodeExtension** Projekt fügen Sie zwei Codedateien hinzu, die SiteNodeExtension und WebPartNodeTypeProvider benannt werden.  
  
2.  Öffnen Sie das Kontextmenü für das Projekt "WebPartNodeExtension", und wählen Sie dann **Verweis hinzufügen** aus.  
  
3.  Im Dialogfeld **Verweis\-Manager – WebPartNodeExtension** wählen Sie den Knoten **Framework** aus, und wählen Sie dann die Kontrollkästchen für die System.ComponentModel.Compositions\- und System.Windows.Forms aus.  
  
4.  Wählen Sie den Knoten aus **Erweiterungen**, aktivieren Sie das Kontrollkästchen für jede der folgenden Assemblys aus, und wählen Sie dann die Schaltfläche **OK** aus:  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Öffnen Sie das Kontextmenü für das **WebPartNodeExtension** Projekt, und wählen Sie dann **Eigenschaften** aus.  
  
     Der **Projekt\-Designer** wird geöffnet.  
  
6.  Wählen Sie die Registerkarte aus. **Anwendung**  
  
7.  **Standardnamespace** im Feld \(C\#\) oder in Feld **Stammnamespace** \(Visual Basic\), geben Sie **ServerExplorer.SharePointConnections.WebPartNode** ein.  
  
## Erstellen von Symbolen für die neuen Knoten  
 Erstellen Sie zwei Symbole für die **Server\-Explorer** Erweiterung: ein Symbol für den neuen Knoten **Webpartkatalog** und ein anderes Symbol für untergeordnete Webpartknoten unter dem Knoten **Webpartkatalog**.  Später in dieser exemplarischen Vorgehensweise, schreiben Sie Code, der diese Symbole den Knoten zuordnet.  
  
#### So erstellen Sie Symbole für die Knoten  
  
1.  In **Projekt\-Designer** für das Projekt "WebPartNodeExtension", wählen Sie die Registerkarte **Ressourcen** aus.  
  
2.  Wählen Sie den Link **, den dieses Projekt keine Standardressourcendatei enthält. Klicken Sie hier, um eine zu erstellen.**  
  
     Visual Studio erstellt eine Ressourcendatei und öffnet sie im Designer.  
  
3.  am oberen Rand des Designers wählen Sie den Pfeil auf dem **Ressource hinzufügen** Menübefehl aus, und wählen Sie dann **Neues Symbol hinzufügen** aus.  
  
4.  Geben Sie **WebPartsNode** für das neue Symbol ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Das neue Symbol wird in der **Bildbearbeitung** geöffnet.  
  
5.  Bearbeiten Sie die 16x16\-Version des Symbols, dass es einen Entwurf aufweist, den Sie leicht erkennen können.  
  
6.  Öffnen Sie das Kontextmenü für die 32x32\-Version des Symbols, und wählen Sie dann **Bildtyp löschen** aus.  
  
7.  Wiederholen Sie die Schritte 3 bis 7, um den Projektressourcen ebenfalls ein Symbol hinzuzufügen, und benennen Sie dieses Symbol **Webpart**.  
  
8.  In **Projektmappen\-Explorer** im Ordner **Ressourcen** für das Projekt **WebPartNodeExtension**, wählen Sie **WebPartsNode.ico** aus.  
  
9. Im Fenster **Eigenschaften** öffnen Sie die Liste **Buildvorgang**, und wählen Sie dann **Eingebettete Ressource** aus.  
  
10. Wiederholen Sie die letzten zwei Schritte für **WebPart.ico**.  
  
## Hinzufügen des Webpartkatalogknotens zum Server\-Explorer  
 Erstellen Sie eine Klasse, die jedem SharePoint\-Websiteknoten den neuen Knoten **Webpartkatalog** hinzufügt.  Zum Hinzufügen des neuen Knotens implementiert die Klasse die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>\-Schnittstelle.  Implementieren Sie diese Schnittstelle immer dann, wenn Sie das Verhalten eines vorhandenen Knotens in **Server\-Explorer** erweitern möchten, z. B. wenn Sie einen neuen untergeordneten Knoten zu einem Knoten hinzufügen.  
  
#### So fügen Sie den Webpartkatalogknoten zum Server\-Explorer hinzu  
  
1.  Fügen Sie folgenden Code in die **SiteNodeExtension** Codedatei für das **WebPartNodeExtension** Projekt ein.  
  
    > [!NOTE]  
    >  Nachdem Sie diesen Code hinzufügen, weist das Projekt mehrere Compilerfehler.  Diese Fehler werden durch Code behoben, den Sie in späteren Schritten hinzufügen.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/cs/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## Definieren eines Knotentyps, der ein Webpart darstellt  
 Erstellen Sie eine Klasse, die einen neuen Knotentyp definiert, der ein Webpart darstellt.  Visual Studio verwendet diesen neuen Knotentyp, um untergeordnete Knoten unter dem Knoten **Webpartkatalog** anzuzeigen.  Jeder dieser untergeordneten Knoten stellt ein einzelnes Webpart auf der SharePoint\-Website dar.  
  
 Um den neuen Knotentyp zu definieren, implementiert die Klasse die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>\-Schnittstelle.  Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen neuen Knotentyp im **Server\-Explorer** definieren möchten.  
  
#### So definieren Sie den Webpartknotentyp  
  
1.  Fügen Sie folgenden Code in die **WebPartNodeTypeProvider** Codedatei für das **WebPartNodeExtension** Projekt ein.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/cs/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## Checkpoint  
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte für den Knoten **Webpartkatalog** benötigte Code in das Projekt eingefügt.  Erstellen Sie das **WebPartNodeExtension** Projekt, um sicherzustellen, dass es ohne Fehler kompiliert.  
  
#### So erstellen Sie das Projekt  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für das **WebPartNodeExtension** Projekt, und wählen Sie dann **Erstellen** aus.  
  
## Erstellen eines VSIX\-Pakets zum Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX\-Projekts in der Lösung ein VSIX\-Paket.  Konfigurieren Sie zuerst das VSIX\-Paket, indem Sie die Datei "source.extension.vsixmanifest" ändern, die im Projekt enthalten ist.  Erstellen Sie anschließend das VSIX\-Paket, indem Sie die Projektmappe erstellen.  
  
#### So konfigurieren Sie das VSIX\-Paket  
  
1.  In **Projektmappen\-ExplorerWebPartNode** im Projekt, **source.extension.vsixmanifest** geöffnete Datei im Manifest\-Editor.  
  
     Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei, die alle VSIX\-Pakete benötigen.  Weitere Informationen zu dieser Datei finden Sie unter [VSIX\-Erweiterungs\-Schemareferenz](http://msdn.microsoft.com/de-de/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Im Feld geben Sie **ProduktnameWebpartkatalog\-Knoten für Server\-Explorer** ein.  
  
3.  Im Feld geben Sie **AutorContoso** ein.  
  
4.  Im Feld geben Sie **BeschreibungFügt einen benutzerdefinierten Webpartkatalogknoten dem Knoten SharePoint\-Verbindungen im Server\-Explorer hinzu** ein.  
  
5.  Klicken Sie auf der Registerkarte des Editors **Objekte**, wählen Sie die Schaltfläche **Neu** aus.  
  
6.  **Neue Anlage hinzufügen** im Dialogfeld in der Liste **Typ**, wählen Sie **Microsoft.VisualStudio.MefComponent** aus.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `MefComponent`\-Element in der Datei "extension.vsixmanifest".  Von diesem Element wird der Name einer Erweiterungsassembly im VSIX\-Paket angegeben.  Weitere Informationen finden Sie unter [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/de-de/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  In der Liste wählen Sie **QuelleEin Projekt in der aktuellen Projektmappe** aus.  
  
8.  In der Liste wählen Sie **ProjektWebPartNodeExtension** aus und wählen dann die Schaltfläche **OK** aus.  
  
9. Klicken Sie auf der Menüleiste wählen Sie **Erstellen**, **Projektmappe erstellen** aus, und überprüfen Sie, ob die Projektmappe fehlerfrei kompiliert.  
  
10. Stellen Sie sicher, dass der Buildausgabeordner für das Projekt WebPartNode jetzt die Datei WebPartNode.vsix enthält.  
  
     Standardmäßig ist der Buildausgabeordner der  Ordner "\\bin\\Debug" im Ordner mit der Projektdatei.  
  
## Testen der Erweiterung  
 Jetzt können Sie den neuen Knoten **Webpartkatalog** in **Server\-Explorer** testen.  Erstellen Sie zunächst, das Erweiterungsprojekt in einer experimentellen Instanz von Visual Studio debuggen.  Verwenden Sie dann den neuen Knoten **Webparts** in der experimentellen Instanz von Visual Studio.  
  
#### So debuggen Sie die Erweiterung  
  
1.  Starten Sie Visual Studio erneut mit Administratorrechten, und öffnen Sie dann die **WebPartNode** Projektmappe.  
  
2.  Öffnen Sie im Projekt "WebPartNodeExtension" die **SiteNodeExtension** Codedatei, und fügen Sie anschließend einen Haltepunkt startet den aus \- `NodeChildrenRequested` und `CreateWebPartNodes`\-Methoden hinzu.  
  
3.  Drücken Sie die F5\-TASTE, um das Debuggen zu starten.  
  
     Visual Studio installiert die Erweiterung in %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Web Part Gallery Node Extension for Server Explorer\\1.0 und startet eine experimentelle Instanz von Visual Studio.  Sie testen das Projektelement in dieser Instanz von Visual Studio.  
  
#### So testen Sie die Erweiterung  
  
1.  Klicken Sie in der experimentellen Instanz von Visual Studio, in der Menüleiste, wählen Sie **Ansicht**, **Server\-Explorer** aus.  
  
2.  Überprüfen Sie, ob die SharePoint\-Website, die Sie für die Tests verwenden möchten, unter dem Knoten **SharePoint\-Verbindungen** im **Server\-Explorer** angezeigt wird.  Wenn sie nicht aufgelistet ist, führen Sie folgende Schritte aus:  
  
    1.  Öffnen Sie das Kontextmenü für **SharePoint\-Verbindungen**, und wählen Sie dann **Verbindung hinzufügen** aus.  
  
    2.  Im Dialogfeld **SharePoint\-Verbindung hinzufügen** geben Sie die URL für die SharePoint\-Website, mit der Sie eine Verbindung herstellen möchten, und wählen Sie dann die Schaltfläche **OK** aus.  
  
         Um die lokale SharePoint\-Website auf dem Entwicklungscomputer anzugeben, geben Sie **http:\/\/localhost** ein.  
  
3.  Erweitern Sie den Website\-Verbindungsknoten \(den die URL der Website angezeigt wird\), und erweitern Sie dann einen untergeordneten Websiteknoten \(beispielsweise, **Teamwebsite**\).  
  
4.  Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der festgelegt `NodeChildrenRequested`\-Methode und dann die F5\-Taste auswählen, um fortfahren, um das Projekt zu debuggen.  
  
5.  Klicken Sie in der experimentellen Instanz von Visual Studio, erweitern Sie den Knoten **Webpartkatalog**, der unter dem Websiteknoten der obersten Ebene angezeigt.  
  
6.  Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der festgelegt `CreateWebPartNodes`\-Methode und dann die F5\-Taste auswählen, um fortfahren, um das Projekt zu debuggen.  
  
7.  Überprüfen Sie in der experimentellen Instanz von Visual Studio, ob alle Webparts der verbundenen Website unter dem Knoten **Webpartkatalog** im **Server\-Explorer** angezeigt werden.  
  
8.  Öffnen Sie das Kontextmenü für ein Webpart, und wählen Sie dann **Eigenschaften** aus.  
  
9. Im Fenster **Eigenschaften** überprüfen Sie, ob die Details zum Webpart angezeigt werden.  
  
10. In **Server\-Explorer** öffnen Sie das Kontextmenü für dasselbe Webpart, und wählen Sie dann **Meldung anzeigen** aus.  
  
     Klicken Sie im Meldungsfeld, das angezeigt wird, wählen Sie die Schaltfläche **OK** aus.  
  
## Deinstallieren der Erweiterung aus Visual Studio  
 Nachdem Sie beenden, die Erweiterung zu testen, deinstallieren Sie sie aus Visual Studio.  
  
#### So deinstallieren Sie die Erweiterung  
  
1.  Klicken Sie in der experimentellen Instanz von Visual Studio, in der Menüleiste, wählen Sie **Tools**, **Erweiterungen und Updates** aus.  
  
     Das Dialogfeld wird geöffnet. **Erweiterungen und Updates**  
  
2.  In der Liste der Erweiterungen, wählen Sie **Webpartkatalog\-Knoten für Server\-Explorer** aus und wählen dann die Schaltfläche **Deinstallieren** aus.  
  
3.  Im Dialogfeld, das angezeigt wird, wählen Sie die Schaltfläche **Ja** aus.  
  
4.  Wählen Sie die Schaltfläche **Jetzt neu starten**, um die Deinstallation abzuschließen.  
  
     Das Projektelement wird ebenfalls deinstalliert.  
  
5.  Schließen Sie beide Instanzen von Visual Studio \(die experimentelle Instanz und die Instanz von Visual Studio, in der die Projektmappe "WebPartNode" geöffnet ist\).  
  
## Siehe auch  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  