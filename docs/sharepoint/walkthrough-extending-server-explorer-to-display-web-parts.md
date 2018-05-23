---
title: 'Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 688c4d8d9193ec33f0dcb63923673826a453c9be
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2018
---
# <a name="walkthrough-extending-server-explorer-to-display-web-parts"></a>Exemplarische Vorgehensweise: Erweitern des Server-Explorers für die Anzeige von Webparts
  In Visual Studio können Sie die **SharePoint-Verbindungen** Knoten **Server-Explorer** , Komponenten für SharePoint-Websites anzuzeigen. Allerdings **Server-Explorer** einige Komponenten nicht standardmäßig angezeigt. In dieser exemplarischen Vorgehensweise verlängern **Server-Explorer** , damit sie den Webpartkatalog auf zeigt jeweils die SharePoint-Website verbunden.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer Visual Studio-Erweiterung, erweitert **Server-Explorer** auf folgende Weise:  
  
    -   Fügt die Erweiterung einer **Webpartkatalog** unter jedem SharePoint-Website-Knoten im Knoten **Server-Explorer**. Dieser neue Knoten enthält untergeordnete Knoten, die jedes Webpart in den Webpartkatalog auf der Website darstellen.  
  
    -   Die Erweiterung definiert einen neuen Typ von Knoten, der eine Webpart-Instanz darstellt. Diese neuen Knotentyps bildet die Grundlage für die untergeordneten Knoten unter der neuen **Webpartkatalog** Knoten. Die neuen Knotentyps-Webpart zeigt die Informationen in den **Eigenschaften** Fenster über das Webpart, den sie darstellt. Der Knotentyp enthält auch ein benutzerdefiniertes Kontextmenüelement, das Sie als Ausgangspunkt verwenden können, für andere Aufgaben, die auf das Webpart beziehen.  
  
-   Erstellen zwei benutzerdefinierte SharePoint-Befehle, die die Erweiterung Assembly aufrufen. SharePoint-Befehle sind Methoden, die von Erweiterungsassemblys APIs in das Serverobjektmodell für SharePoint verwendet aufgerufen werden können. In dieser exemplarischen Vorgehensweise erstellen Sie Befehle, die Webpart-Informationen aus der lokalen SharePoint-Website auf dem Entwicklungscomputer abrufen. Weitere Informationen finden Sie unter [Aufrufe in die SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Erstellen eines Visual Studio-Erweiterung (VSIX) zum Bereitstellen der Erweiterung.  
  
-   Debuggen und Testen der Erweiterung.  
  
> [!NOTE]  
>  Eine alternative Version dieser exemplarischen Vorgehensweise, die das Clientobjektmodell für SharePoint anstelle dessen Serverobjektmodell verwendet, finden Sie unter [Exemplarische Vorgehensweise: Aufrufen von in der SharePoint-Clientobjektmodell innerhalb einer Server-Explorererweiterung](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von Windows, SharePoint und Visual Studio. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Das Visual Studio SDK. Diese exemplarische Vorgehensweise verwendet die **VSIX-Projekt** Vorlage im SDK, um ein VSIX-Paket zum Bereitstellen des Projektelements zu erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Verwenden das Serverobjektmodell für SharePoint. Weitere Informationen finden Sie unter [mithilfe des Objektmodells von SharePoint Foundation serverseitige](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Webparts in SharePoint-Lösungen. Weitere Informationen finden Sie unter [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="creating-the-projects"></a>Erstellen der Projekte  
 Zum Durchführen dieser exemplarischen Vorgehensweise müssen Sie drei Projekte erstellen:  
  
-   Ein VSIX-Projekt, um das VSIX-Paket zum Bereitstellen der Erweiterung zu erstellen.  
  
-   Ein Klassenbibliotheksprojekt, das die Erweiterung implementiert. Dieses Projekt muss .NET Framework 4.5 als Zielversion.  
  
-   Ein Klassenbibliotheksprojekt, das die benutzerdefinierten SharePoint-Befehle definiert. Für dieses Projekt muss .NET Framework 3.5 als Zielversion verwendet werden.  
  
 Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.  
  
3.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann die **Erweiterbarkeit** Knoten.  
  
    > [!NOTE]  
    >  Die **Erweiterbarkeit** Knoten ist nur verfügbar, wenn Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.  
  
4.  Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 4.5** in der Liste der Versionen von .NET Framework.  
  
5.  Wählen Sie die **VSIX-Projekt** Vorlage, nennen Sie das Projekt **WebPartNode**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **WebPartNode** Projekt **Projektmappen-Explorer**.  
  
#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen Sie **hinzufügen**, und wählen Sie dann **neues Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** Knoten oder **Visual Basic** Knoten, und wählen Sie dann **Windows** Knoten.  
  
3.  Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 4.5** in der Liste der Versionen von .NET Framework.  
  
4.  Wählen Sie in der Liste der Projektvorlagen **-Klassenbibliothek**, nennen Sie das Projekt **WebPartNodeExtension**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **WebPartNodeExtension** Projekt der Projektmappe und öffnet die Class1-Codedatei.  
  
5.  Löschen Sie die Class1-Codedatei aus dem Projekt.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>So erstellen Sie das SharePoint-Befehlsprojekt  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen Sie **hinzufügen**, und wählen Sie dann **neues Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** Knoten oder **Visual Basic** Knoten, und wählen Sie dann die **Windows** Knoten.  
  
3.  Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 3.5** in der Liste der Versionen von .NET Framework.  
  
4.  Wählen Sie in der Liste der Projektvorlagen **-Klassenbibliothek**, nennen Sie das Projekt **WebPartCommands**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **WebPartCommands** Projekt der Projektmappe und öffnet die Class1-Codedatei.  
  
5.  Löschen Sie die Class1-Codedatei aus dem Projekt.  
  
## <a name="configuring-the-projects"></a>Konfigurieren der Projekte  
 Vor dem Schreiben von Code zum Erstellen der Erweiterung müssen Sie Codedateien und Assemblyverweise hinzufügen und Konfigurieren der Einstellungen für Projektdateien.  
  
#### <a name="to-configure-the-webpartnodeextension-project"></a>So konfigurieren Sie das Projekt WebPartNodeExtension  
  
1.  Fügen Sie im Projekt WebPartNodeExtension vier Codedateien, die mit den folgenden Namen benötigt:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Öffnen Sie das Kontextmenü für die **WebPartNodeExtension** Projekt, und wählen Sie dann **Verweis hinzufügen**.  
  
3.  In der **Verweis-Manager - WebPartNodeExtension** Dialogfeld Wählen Sie die **Framework** Registerkarte, und klicken Sie dann das Kontrollkästchen für jede der folgenden Assemblys:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  Wählen Sie die **Erweiterungen** Registerkarte das Kontrollkästchen für die Microsoft.VisualStudio.SharePoint-Assembly, und wählen Sie dann die **OK** Schaltfläche.  
  
5.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **WebPartNodeExtension** Projektknoten, und wählen Sie dann **Eigenschaften**.  
  
     Der **Projekt-Designer** wird geöffnet.  
  
6.  Wählen Sie die Registerkarte **Anwendung** aus.  
  
7.  In der **Standardnamespace** Feld (c#) oder **Stammnamespace** Feld ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), geben Sie **Wert ServerExplorer.SharePointConnections.WebPartNode**.  
  
#### <a name="to-configure-the-webpartcommands-project"></a>So konfigurieren Sie das Projekt WebPartCommands  
  
1.  Fügen Sie im Projekt eine Codedatei, die Namen hinzu.  
  
2.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **WebPartCommands** Projektknoten, wählen Sie **hinzufügen**, und wählen Sie dann **vorhandenes Element**.  
  
3.  In der **vorhandenes Element hinzufügen** (Dialogfeld), navigieren Sie zu dem Ordner, der die Codedateien für das Projekt WebPartNodeExtension enthält, und wählen Sie dann die Codedateien WebPartNodeInfo und WebPartCommandIds aus.  
  
4.  Wählen Sie den Pfeil neben der **hinzufügen** aus, und klicken Sie dann **als Link hinzufügen** im angezeigten Menü.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt die Codedateien zum Projekt WebPartCommands als Links. Daher befinden sich die Codedateien im Projekt WebPartNodeExtension, aber der Code in den Dateien ebenfalls Projekt kompiliert.  
  
5.  Öffnen Sie das Kontextmenü für die **WebPartCommands** Projekt erneut, und wählen **Verweis hinzufügen**.  
  
6.  In der **Verweis-Manager - WebPartCommands** Dialogfeld Wählen Sie die **Erweiterungen** Registerkarte das Kontrollkästchen für jede der folgenden Assemblys, und wählen Sie dann die **OK** Schaltfläche:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **WebPartCommands** erneut aus, und wählen Sie dann **Eigenschaften**.  
  
     Der **Projekt-Designer** wird geöffnet.  
  
8.  Wählen Sie die Registerkarte **Anwendung** aus.  
  
9. In der **Standardnamespace** Feld (c#) oder **Stammnamespace** Feld ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), geben Sie **Wert ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="creating-icons-for-the-new-nodes"></a>Erstellen von Symbolen für die neuen Knoten  
 Erstellen Sie zwei Symbole für die **Server-Explorer** Erweiterung: ein Symbol für die neue **Webpartkatalog** Knoten, und ein anderes Symbol für jeden untergeordneten Webpart Knoten unter dem **Webpartkatalog** Knoten. Weiter unten in dieser exemplarischen Vorgehensweise werden Sie Code schreiben, die diese Symbole Knoten zuordnet.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Zum Erstellen von Symbolen für die Knoten  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **WebPartNodeExtension** Projekt, und wählen Sie dann **Eigenschaften**.  
  
2.  Der **Projekt-Designer** wird geöffnet.  
  
3.  Wählen Sie die **Ressourcen** Registerkarte, und wählen Sie dann die **dieses Projekt enthält keine Standarddatei für die Ressourcen. Klicken Sie hier zum Erstellen eines** Link.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt eine Ressourcendatei, und klicken Sie im Designer geöffnet.  
  
4.  Wählen Sie im oberen Bereich des Designers den Pfeil neben der **Ressource hinzufügen** Menü Befehl, und wählen Sie dann **Symbol "Neu" hinzufügen** im angezeigten Menü.  
  
5.  In der **neue Ressource hinzufügen** Dialogfeld Feld "Name" das Symbol "Neu" **WebPartsNode als Namen**, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Das Symbol "neue" wird geöffnet, der **Bildbearbeitung**.  
  
6.  Bearbeiten Sie die 16 x 16-Version des Symbols, sodass sie einen Entwurf aufweist, den Sie leicht erkennen können.  
  
7.  Öffnen Sie das Kontextmenü für die 32 x 32-Version des Symbols, und wählen Sie dann **Bildtyp löschen**.  
  
8.  Wiederholen Sie die Schritte 5 bis 8 der Projektressourcen ein Symbol hinzu, und nennen Sie dieses Symbol **WebPart**.  
  
9. In **Projektmappen-Explorer**unter der **Ressourcen** Ordner für die **WebPartNodeExtension** Projekt, öffnen Sie das Kontextmenü für **Datei WebPartsNode.ico**.  
  
10. In der **Eigenschaften** Fenster, wählen Sie den Pfeil neben **Buildvorgang**, und wählen Sie dann **eingebettete Ressource** auf das Menü, das angezeigt wird.  
  
11. Wiederholen Sie die letzten beiden Schritte für **WebPart.ico**.  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>Server-Explorer hinzufügen den Knoten Webpartkatalog  
 Erstellen Sie eine Klasse, die die neue fügt **Webpartkatalog** Knoten für jeden Knoten des SharePoint-Website. Zum Hinzufügen des neuen Knotens, die Klasse implementiert die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Schnittstelle. Diese Schnittstelle implementieren, wenn Sie das Verhalten in einen vorhandenen Knoten erweitern möchten **Server-Explorer**, z. B. ein Knoten einen untergeordneter Knoten hinzugefügt.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Server-Explorer den Knoten Webpartkatalog hinzu  
  
1.  Klicken Sie im Projekt WebPartNodeExtension öffnen Sie SiteNodeExtension-Codedatei, und fügen Sie den folgenden Code hinein.  
  
    > [!NOTE]  
    >  Nachdem Sie diesen Code hinzufügen, muss das Projekt einige Kompilierungsfehler, aber natürlich werden hinzugefügt, wenn Code in späteren Schritten.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>Definieren einen Knotentyp, das ein Webpart darstellt.  
 Erstellen Sie eine Klasse, die einen neuen Typ des Knotens definiert, das ein Webpart darstellt. Visual Studio verwendet diese neuen Knotentyps anzuzeigenden untergeordneten Knoten unter dem **Webpartkatalog** Knoten. Jeder untergeordnete Knoten stellt ein einzelnes Webpart auf der SharePoint-Website.  
  
 Definieren Sie den neuen Knotentyp, implementiert die Klasse der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Schnittstelle. Diese Schnittstelle implementieren, wenn Sie einen neuen Typ des Knotens im definieren möchten **Server-Explorer**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Zum Definieren des Webpart-Knotentyp  
  
1.  Klicken Sie im Projekt WebPartNodeExtension öffnen Sie WebPartNodeTypeProvder-Codedatei, und fügen Sie den folgenden Code hinein.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]  
  
## <a name="defining-the-web-part-data-class"></a>Die Web-Teilklasse Daten definieren  
 Definieren Sie eine Klasse, die Daten über ein einzelnes Webpart auf der SharePoint-Website enthält. Weiter unten in dieser exemplarischen Vorgehensweise erstellen Sie einen benutzerdefinierten SharePoint-Befehl, der Abrufen von Daten über jedes Webpart auf der Website, und weist dann die Daten zu Instanzen dieser Klasse.  
  
#### <a name="to-define-the-web-part-data-class"></a>So definieren Sie das Webpart Daten-Klasse  
  
1.  Klicken Sie im Projekt WebPartNodeExtension öffnen Sie WebPartNodeInfo-Codedatei, und fügen Sie den folgenden Code hinein.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]  
  
## <a name="defining-the-ids-for-the-sharepoint-command"></a>Definieren die IDs für den SharePoint-Befehl  
 Definieren von mehreren Zeichenfolgen, die die benutzerdefinierten SharePoint-Befehle zu identifizieren. Implementieren Sie diese Befehle später in dieser exemplarischen Vorgehensweise.  
  
#### <a name="to-define-the-command-ids"></a>Definieren Sie die Befehls-IDs  
  
1.  Klicken Sie im Projekt WebPartNodeExtension öffnen Sie WebPartCommandIds-Codedatei, und fügen Sie den folgenden Code hinein.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>Erstellen der benutzerdefinierten SharePoint-Befehle  
 Erstellen Sie benutzerdefinierte Befehle, die das Serverobjektmodell für SharePoint zum Abrufen von Daten zu den den Webparts auf der SharePoint-Website aufrufen. Jeder Befehl ist eine Methode mit dem <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> angewendet wird.  
  
#### <a name="to-define-the-sharepoint-commands"></a>So definieren Sie die SharePoint-Befehle  
  
1.  Klicken Sie im Projekt öffnen Sie WebPartCommands-Codedatei, und fügen Sie den folgenden Code hinein.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]  
  
## <a name="checkpoint"></a>Checkpoint  
 An diesem Punkt in der exemplarischen Vorgehensweise wurde der Code für die **Webpartkatalog** Knoten und die SharePoint-Befehle sind jetzt in den Projekten. Erstellen Sie die Projektmappe, um sicherzustellen, dass beide Projekte fehlerfrei kompiliert werden.  
  
#### <a name="to-build-the-solution"></a>So erstellen Sie die Projektmappe  
  
1.  Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
    > [!WARNING]  
    >  An diesem Punkt kann das Projekt WebPartNode einen Buildfehler haben, da die VSIX-manifest-Datei einen Wert für Autor nicht. Dieser Fehler wird behoben, wenn Sie einen Wert in späteren Schritten hinzufügen.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Erstellen ein VSIX-Paket zum Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX-Projekts in der Lösung ein VSIX-Paket. Konfigurieren Sie zuerst das VSIX-Paket, indem der Datei source.extension.vsixmanifest im VSIX-Projekts ändern. Erstellen Sie anschließend das VSIX-Paket, indem Sie die Lösung erstellen.  
  
#### <a name="to-configure-the-vsix-package"></a>So konfigurieren Sie das VSIX-Paket  
  
1.  In **Projektmappen-Explorer**, unter dem Projekt WebPartNode öffnen die **"Source.Extension.vsixmanifest"** Datei im manifest-Editor.  
  
     Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie unter [VSIX-Erweiterung Schemareferenz 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  In der **Produktname** geben **Web Part Gallery Node für Server-Explorer**.  
  
3.  In der **Autor** geben **Contoso**.  
  
4.  In der **Beschreibung** geben **des SharePoint-Verbindungsknotens im Server-Explorer einen benutzerdefinierten Webpartkatalog Knoten hinzugefügt. Diese Erweiterung verwendet einen benutzerdefinierten SharePoint-Befehl, um das Serverobjektmodell aufrufen.**  
  
5.  Wählen Sie die **Bestand** Registerkarte im Editor, und wählen Sie dann die **neu** Schaltfläche.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.  
  
6.  In der **Typ** wählen **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.  
  
8.  In der **Projekt** wählen **WebPartNodeExtension** und wählen Sie dann die **OK** Schaltfläche.  
  
9. Wählen Sie im manifest-Editor die **neu** erneut.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.  
  
10. In der **Typ** geben **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Dieses Element gibt eine benutzerdefinierte Erweiterung, die Sie in der Visual Studio-Erweiterung einschließen möchten. Weitere Informationen finden Sie unter [Asset-Element (VSX-Schema)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. In der **Quelle** wählen Sie die **ein Projekt in der aktuellen Projektmappe** Listenelement.  
  
12. In der **Projekt** wählen **WebPartCommands**, und wählen Sie dann die **OK** Schaltfläche.  
  
13. Wählen Sie in der Menüleiste **erstellen**, **Projektmappe**, und stellen Sie sicher, dass die Lösung ohne Fehler kompiliert wird.  
  
14. Stellen Sie sicher, dass der Buildausgabeordner für das Projekt WebPartNode jetzt die Datei WebPartNode.VSIX enthält.  
  
     Standardmäßig handelt es sich beim Buildausgabeordner um den Ordner "...\bin\Debug" in dem Ordner mit der Projektdatei.  
  
## <a name="testing-the-extension"></a>Testen der Erweiterung  
 Sie können jetzt mit den neuen test **Webpartkatalog** Knoten **Server-Explorer**. Debuggen Sie zunächst die Erweiterung in einer experimentellen Instanz von Visual Studio. Verwenden Sie dann auf die neue **Webparts** Knoten in der experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-start-debugging-the-extension"></a>So debuggen Sie die Erweiterung  
  
1.  Starten Sie neu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit Administratoranmeldeinformationen, und öffnen Sie die Projektmappe WebPartNode.  
  
2.  Klicken Sie im Projekt WebPartNodeExtension SiteNodeExtension-Codedatei öffnen, und fügen Sie einen Haltepunkt an der ersten Codezeile in der `NodeChildrenRequested` und `CreateWebPartNodes` Methoden.  
  
3.  Drücken Sie die F5-TASTE, um das Debuggen zu starten.  
  
     Visual Studio die Erweiterung %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Teil Knoten Katalogerweiterung für Server Explorer\1.0 und eine experimentelle Instanz von Visual Studio wird gestartet. Sie testen das Projektelement in dieser Instanz von Visual Studio.  
  
#### <a name="to-test-the-extension"></a>So testen Sie die Erweiterung  
  
1.  In der experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wählen Sie in der Menüleiste **Ansicht**, **Server-Explorer**.  
  
2.  Führen Sie die folgenden Schritte aus, wenn die SharePoint-Website, die Sie zum Testen verwenden möchten nicht, unter angezeigt wird dem **SharePoint-Verbindungen** Knoten **Server-Explorer**:  
  
    1.  In **Server-Explorer**, öffnen Sie das Kontextmenü für **SharePoint-Verbindungen**, und wählen Sie dann **Verbindung hinzufügen**.  
  
    2.  In der **SharePoint-Verbindung hinzufügen** Dialogfeld Geben Sie die URL für die SharePoint-Website, die Sie möchten eine Verbindung herstellen, und wählen Sie dann die **OK** Schaltfläche.  
  
         Geben Sie zum Angeben der SharePoint-Website auf dem Entwicklungscomputer **http://localhost**.  
  
3.  Erweitern Sie den Website-Verbindungsknoten (in der die URL Ihrer Website angezeigt werden), und dann einen untergeordneten Standort Knoten (z. B. **Teamwebsite**).  
  
4.  Überprüfen Sie, ob der Code in der anderen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] beendet wird, an dem Haltepunkt an, die Sie zuvor im Festlegen der `NodeChildrenRequested` -Methode, und wählen Sie dann F5, um das Debuggen des Projekts fortzusetzen.  
  
5.  In der experimentellen Instanz von Visual Studio, stellen Sie sicher, dass ein neuer Knoten namens **Webpartkatalog** unter dem Standort der obersten Ebene Knoten angezeigt, und erweitern Sie dann die **Webpartkatalog** Knoten.  
  
6.  Stellen Sie sicher, dass der Code in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, die Sie zuvor im Festlegen der `CreateWebPartNodes` -Methode, und wählen Sie dann die F5-Taste, um das Debuggen des Projekts fortzusetzen.  
  
7.  In der experimentellen Instanz von Visual Studio, überprüfen Sie, ob alle Webparts auf die verbundene Website unter der **Webpartkatalog** Knoten **Server-Explorer**.  
  
8.  In **Server-Explorer**, öffnen Sie das Kontextmenü für eines der Webparts, und wählen Sie dann **Eigenschaften**.  
  
9. In der Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , die Sie Debuggen, stellen Sie sicher, dass in Details zum Webpart angezeigt werden die **Eigenschaften** Fenster.  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>Deinstallieren die Erweiterung von Visual Studio  
 Klicken Sie nach dem Testen der Erweiterung deinstallieren der Erweiterung von Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>So deinstallieren Sie die Erweiterung  
  
1.  In der experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wählen Sie in der Menüleiste **Tools**, **Erweiterungen und Updates**.  
  
     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.  
  
2.  Wählen Sie in der Liste der Erweiterungen, **Web Teil Knoten Katalogerweiterung für Server-Explorer**, und wählen Sie dann die **Deinstallieren** Schaltfläche.  
  
3.  Wählen Sie im angezeigten Dialogfeld die **Ja** , um zu bestätigen, dass Sie verwenden möchten, deinstallieren Sie die Erweiterung aus, und wählen Sie dann die **jetzt neu starten** Schaltfläche, um die Deinstallation abzuschließen.  
  
4.  Schließen Sie beide Instanzen von Visual Studio (die experimentelle Instanz und die Instanz von Visual Studio in der die Projektmappe WebPartNode geöffnet ist).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Exemplarische Vorgehensweise: Aufrufe in die SharePoint-Clientobjektmodell innerhalb einer Server-Explorererweiterung](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Bildbearbeitung für Symbole](/cpp/windows/image-editor-for-icons)   
 [Erstellen eines Symbols oder anderen Bilds &#40;Bildbearbeitung für Symbole&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  