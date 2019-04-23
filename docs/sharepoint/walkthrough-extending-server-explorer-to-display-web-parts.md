---
title: 'Exemplarische Vorgehensweise: Erweitern des Server-Explorers zur Anzeige von Webparts | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 29fcd40a2fc64a12ed7b29845b0a9f0ea3db5589
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040571"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Exemplarische Vorgehensweise: Erweitern Sie Server-Explorer, um die Anzeige von Webparts
  In Visual Studio können Sie die **SharePoint-Verbindungen** Knoten **Server-Explorer** um Komponenten auf SharePoint-Websites anzuzeigen. Allerdings **Server-Explorer** nicht einige Komponenten werden standardmäßig angezeigt. Erweitern Sie in dieser exemplarischen Vorgehensweise **Server-Explorer** , damit es den Webpartkatalog auf zeigt jeweils die SharePoint-Website verbunden.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen einer Visual Studio-Erweiterung, erweitert **Server-Explorer** auf folgende Weise:

    - Fügt die Erweiterung eine **Webpartkatalog** Knoten unter jeder SharePoint-Websiteknoten im **Server-Explorer**. Dieser neue Knoten enthält untergeordnete Knoten, die jedes Webpart in der Webpart-Katalog auf der Website darstellen.

    - Die Erweiterung definiert eine neue Art von Knoten, der eine Webpart-Instanz darstellt. Diese neuen Knotentyp ist die Grundlage für die untergeordneten Knoten unter der neuen **Webpartkatalog** Knoten. Die neue Webpart-Knotentyp zeigt Informationen auf der **Eigenschaften** Fenster über das Webpart, das es darstellt. Der Knotentyp hinaus ein benutzerdefinierten Kontextmenüelements, mit denen Sie als Ausgangspunkt für andere Aufgaben, die zum Webpart beziehen.

- Erstellen Sie zwei benutzerdefinierte SharePoint-Befehle, die die Erweiterungsassembly aufruft. SharePoint-Befehle sind Methoden, die von Erweiterungsassemblys APIs im Server-Objektmodell für SharePoint verwenden aufgerufen werden können. In dieser exemplarischen Vorgehensweise erstellen Sie die Befehle, die aus der lokalen SharePoint-Website auf dem Entwicklungscomputer Webpart-Informationen abgerufen werden. Weitere Informationen finden Sie unter [rufen Sie in der SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Erstellen eines Visual Studio-Erweiterung (VSIX) zum Bereitstellen der Erweiterung.

- Das Debuggen und Testen der Erweiterung.

> [!NOTE]
>  Eine andere Version der in dieser exemplarischen Vorgehensweise, die das Clientobjektmodell statt dessen das Serverobjektmodell für SharePoint verwendet werden soll, finden Sie unter [Exemplarische Vorgehensweise: Rufen Sie in der SharePoint-Clientobjektmodell innerhalb einer Server-explorererweiterung](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:

- Unterstützte Editionen von Windows, SharePoint und Visual Studio.

- Das Visual Studio SDK. Diese exemplarische Vorgehensweise verwendet die **VSIX-Projekt** Vorlage in das SDK zum Erstellen eines VSIX-Pakets zum Bereitstellen des Projektelements. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- Verwenden das Serverobjektmodell für SharePoint. Weitere Informationen finden Sie unter [mithilfe des Objektmodells von SharePoint Foundation Server-Side](http://go.microsoft.com/fwlink/?LinkId=177796).

- Webparts in SharePoint-Lösungen. Weitere Informationen finden Sie unter [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803).

## <a name="create-the-projects"></a>Erstellen Sie die Projekte
 Um diese exemplarische Vorgehensweise abzuschließen, müssen Sie drei Projekte erstellen:

- Ein VSIX-Projekt zum Erstellen des VSIX-Pakets zum Bereitstellen der Erweiterung.

- Ein Klassenbibliotheksprojekt, das die Erweiterung implementiert. Dieses Projekt muss .NET Framework 4.5 als Ziel.

- Ein Klassenbibliotheksprojekt, das die benutzerdefinierten SharePoint-Befehle definiert. Für dieses Projekt muss .NET Framework 3.5 als Zielversion verwendet werden.

  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.

#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann die **Erweiterbarkeit** Knoten.

    > [!NOTE]
    >  Die **Erweiterbarkeit** Knoten ist nur verfügbar, wenn Sie Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.

4. Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 4.5** in der Liste der Versionen von .NET Framework.

5. Wählen Sie die **VSIX-Projekt** Vorlage, nennen Sie das Projekt **WebPartNode**, und wählen Sie dann die **OK** Schaltfläche.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **WebPartNode** Projekt **Projektmappen-Explorer**.

#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen **hinzufügen**, und wählen Sie dann **neues Projekt**.

2. In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** Knoten oder **Visual Basic** Knoten, und klicken Sie dann wählen Sie dann **Windows** Knoten.

3. Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 4.5** in der Liste der Versionen von .NET Framework.

4. Wählen Sie in der Liste der Projektvorlagen das Projekt **Klassenbibliothek**, nennen Sie das Projekt **WebPartNodeExtension**, und wählen Sie dann die **OK** Schaltfläche.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **WebPartNodeExtension** -Projekt zur Projektmappe und öffnet die Class1-Codedatei.

5. Löschen Sie die Class1-Codedatei aus dem Projekt.

#### <a name="to-create-the-sharepoint-commands-project"></a>So erstellen Sie das SharePoint-Befehlsprojekt

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen **hinzufügen**, und wählen Sie dann **neues Projekt**.

2. In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** Knoten oder **Visual Basic** Knoten, und wählen Sie dann die **Windows** Knoten.

3. Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 3.5** in der Liste der Versionen von .NET Framework.

4. Wählen Sie in der Liste der Projektvorlagen das Projekt **Klassenbibliothek**, nennen Sie das Projekt **WebPartCommands**, und wählen Sie dann die **OK** Schaltfläche.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **WebPartCommands** -Projekt zur Projektmappe und öffnet die Class1-Codedatei.

5. Löschen Sie die Class1-Codedatei aus dem Projekt.

## <a name="configure-the-projects"></a>Konfigurieren Sie die Projekte
 Bevor Sie Code zum Erstellen der Erweiterung schreiben, müssen Sie Codedateien und Assemblyverweise hinzufügen und konfigurieren die projekteinstellungen.

#### <a name="to-configure-the-webpartnodeextension-project"></a>So konfigurieren Sie das Projekt WebPartNodeExtension

1. Fügen Sie in das Projekt WebPartNodeExtension vier Codedateien mit den folgenden Namen:

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. Öffnen Sie das Kontextmenü für die **WebPartNodeExtension** Projekt, und wählen Sie dann **Verweis hinzufügen**.

3. In der **Verweis-Manager - WebPartNodeExtension** Dialogfeld auf die **Framework** Registerkarte, und klicken Sie dann das Kontrollkästchen für jede der folgenden Assemblys:

    - System.ComponentModel.Composition

    - System.Windows.Forms

4. Wählen Sie die **Erweiterungen** Registerkarte aktivieren Sie das Kontrollkästchen für die der Microsoft.VisualStudio.SharePoint-Assembly, und wählen Sie dann die **OK** Schaltfläche.

5. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **WebPartNodeExtension** Projektknoten, und wählen Sie dann **Eigenschaften**.

     Der **Projekt-Designer** wird geöffnet.

6. Wählen Sie die Registerkarte **Anwendung** aus.

7. In der **Standardnamespace** Kontrollkästchen (c#) oder **Stammnamespace** Feld ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), geben Sie **Wert ServerExplorer.SharePointConnections.WebPartNode**.

#### <a name="to-configure-the-webpartcommands-project"></a>So konfigurieren Sie das Projekt WebPartCommands

1. Fügen Sie im Projekt eine Codedatei, die Namen aus.

2. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **WebPartCommands** Projektknoten, wählen **hinzufügen**, und wählen Sie dann **vorhandenes Element**.

3. In der **vorhandenes Element hinzufügen** Dialogfeld, navigieren Sie zu dem Ordner, der die Codedateien für das Projekt WebPartNodeExtension enthält, und wählen Sie dann die Codedateien WebPartNodeInfo und WebPartCommandIds aus.

4. Wählen Sie den Pfeil neben der **hinzufügen** Schaltfläche, und wählen Sie dann **als Link hinzufügen** im Menü, das angezeigt wird.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt die Codedateien für das Projekt WebPartCommands als Links an. Daher befinden sich die Codedateien im Projekt WebPartNodeExtension, aber der Code in den Dateien auch Projekt kompiliert werden.

5. Öffnen Sie das Kontextmenü für die **WebPartCommands** Projekt erneut, und wählen **Verweis hinzufügen**.

6. In der **Verweis-Manager - WebPartCommands** Dialogfeld auf die **Erweiterungen** Registerkarte aktivieren Sie das Kontrollkästchen für jede der folgenden Assemblys, und wählen Sie dann die **OK** Schaltfläche:

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

7. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **WebPartCommands** Projekt erneut, und wählen Sie dann **Eigenschaften**.

     Der **Projekt-Designer** wird geöffnet.

8. Wählen Sie die Registerkarte **Anwendung** aus.

9. In der **Standardnamespace** Kontrollkästchen (c#) oder **Stammnamespace** Feld ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), geben Sie **Wert ServerExplorer.SharePointConnections.WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Symbole für den neuen Knoten erstellen
 Erstellen Sie zwei Symbole für die **Server-Explorer** Erweiterung: ein Symbol für das neue **Webpartkatalog** Knoten, und ein anderes Symbol für jeden untergeordneten Webpart-Knoten unter dem **Webpartkatalog** Knoten. Weiter unten in dieser exemplarischen Vorgehensweise werden Sie Code schreiben, die diese Symbole mit den Knoten zuordnet.

#### <a name="to-create-icons-for-the-nodes"></a>Symbole für die Knoten zu erstellen

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **WebPartNodeExtension** Projekt, und wählen Sie dann **Eigenschaften**.

2. Der **Projekt-Designer** wird geöffnet.

3. Wählen Sie die **Ressourcen** Registerkarte, und wählen Sie dann die **dieses Projekt enthält keine Standardressourcendatei. Klicken Sie hier, um Informationen zur Erstellung** Link.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt eine Ressourcendatei aus, und es im Designer geöffnet.

4. Am oberen Rand des Designers, wählen Sie den Pfeil neben der **Ressource hinzufügen** Menü Befehl aus, und wählen Sie dann **neues Symbol hinzufügen** im Menü, das angezeigt wird.

5. In der **neue Ressource hinzufügen** Dialogfeld Namen das Symbol "Neu" **WebPartsNode als Namen**, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Das Symbol "Neu" geöffnet, der **Bildbearbeitung**.

6. Bearbeiten Sie die 16 x 16-Version des Symbols, sodass sie einen Entwurf aufweist, den Sie leicht erkennen können.

7. Öffnen Sie das Kontextmenü für die 32 x 32-Version des Symbols, und wählen Sie dann **Bildtyp löschen**.

8. Wiederholen Sie die Schritte 5 bis 8, um ein Symbol den Projektressourcen hinzuzufügen, und nennen Sie dieses Symbol **WebPart**.

9. In **Projektmappen-Explorer**unter der **Ressourcen** Ordner für die **WebPartNodeExtension** Projekt, öffnen Sie das Kontextmenü für **Datei WebPartsNode.ico**.

10. In der **Eigenschaften** Fenster, wählen Sie den Pfeil neben **Buildvorgang**, und wählen Sie dann **eingebettete Ressource** auf das Menü, das angezeigt wird.

11. Wiederholen Sie die letzten beiden Schritte für **WebPart.ico**.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Fügen Sie den Webpartkatalog-Knoten zum Server-Explorer
 Erstellen Sie eine Klasse, die die neue hinzufügt **Webpartkatalog** Knoten aus, um jede SharePoint-Websiteknoten. Zum Hinzufügen des neuen Knotens, der die Klasse implementiert die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Schnittstelle. Diese Schnittstelle implementieren, wenn Sie das Verhalten von einem vorhandenen Knoten in erweitern möchten **Server-Explorer**, z. B. einen untergeordneten Knoten auf einen Knoten hinzufügen.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Um den Webpartkatalog-Knoten zum Server-Explorer hinzuzufügen.

1. Klicken Sie im Projekt WebPartNodeExtension öffnen Sie SiteNodeExtension-Codedatei, und fügen Sie den folgenden Code hinein.

    > [!NOTE]
    >  Nachdem Sie diesen Code hinzufügen, muss das Projekt einige Kompilierungsfehler, aber allerdings verschwinden fügen Sie Code bei in späteren Schritten fest.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Definieren Sie einen Knotentyp, der ein Webpart darstellt.
 Erstellen Sie eine Klasse, die eine neue Art von Knoten definiert, die ein Webpart darstellt. Visual Studio verwendet diesen neuen Knotentyp zum Anzeigen der untergeordneten Knoten unter dem **Webpartkatalog** Knoten. Jeder untergeordnete Knoten stellt ein einzelnes Webpart auf der SharePoint-Website.

 Definieren Sie den neuen Knotentyp, die Klasse implementiert die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Schnittstelle. Diese Schnittstelle implementieren, wenn Sie eine neue Art von Knoten in definieren möchten **Server-Explorer**.

#### <a name="to-define-the-web-part-node-type"></a>Definiert den Webpart-Knotentyp

1. Klicken Sie im Projekt WebPartNodeExtension öffnen Sie WebPartNodeTypeProvder-Codedatei, und fügen Sie den folgenden Code hinein.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]

## <a name="define-the-web-part-data-class"></a>Definieren Sie die Webpart-Daten-Klasse
 Definieren Sie eine Klasse, die Daten über einen einzelnen Webparts auf der SharePoint-Website enthält. Weiter unten in dieser exemplarischen Vorgehensweise erstellen Sie einen benutzerdefinierten SharePoint-Befehl, der Abrufen von Daten über jedes Webpart auf der Website, und weist dann die Daten, um Instanzen dieser Klasse.

#### <a name="to-define-the-web-part-data-class"></a>Der Webpart-Datenklasse definieren.

1. Klicken Sie im Projekt WebPartNodeExtension öffnen Sie die WebPartNodeInfo Codedatei, und fügen Sie den folgenden Code hinein.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]

## <a name="define-the-ids-for-the-sharepoint-commands"></a>Definieren Sie die IDs für die SharePoint-Befehle
 Definieren Sie mehrere Zeichenfolgen, die die benutzerdefinierten SharePoint-Befehle zu identifizieren. Weiter unten in dieser exemplarischen Vorgehensweise implementieren Sie diese Befehle.

#### <a name="to-define-the-command-ids"></a>Definieren Sie die Befehls-IDs

1. Klicken Sie im Projekt WebPartNodeExtension öffnen Sie WebPartCommandIds-Codedatei, und fügen Sie den folgenden Code hinein.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]

## <a name="create-the-custom-sharepoint-commands"></a>Erstellen Sie die benutzerdefinierten SharePoint-Befehle
 Erstellen Sie benutzerdefinierte Befehle, die das Serverobjektmodell für SharePoint zum Abrufen von Daten zu den den Webparts auf der SharePoint-Website aufrufen. Jeder Befehl ist eine Methode mit dem <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> angewendet wird.

#### <a name="to-define-the-sharepoint-commands"></a>So definieren Sie die SharePoint-Befehle

1. Klicken Sie im Projekt öffnen Sie die Codedatei WebPartCommands, und fügen Sie den folgenden Code hinein.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]

## <a name="checkpoint"></a>Checkpoint
 An diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte Code für die **Webpartkatalog** Knoten und die SharePoint-Befehle sind jetzt in den Projekten. Erstellen Sie die Projektmappe aus, um sicherzustellen, dass beide Projekte ohne Fehler kompiliert.

#### <a name="to-build-the-solution"></a>So erstellen Sie die Projektmappe

1. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

    > [!WARNING]
    >  An diesem Punkt möglicherweise das Projekt WebPartNode einen Buildfehler, da die VSIX-manifest-Datei einen Wert für Autor hat. Dieser Fehler verschwindet, wenn Sie einen Wert in späteren Schritten hinzufügen.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Erstellen Sie ein VSIX-Paket zum Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX-Projekts in der Lösung ein VSIX-Paket. Konfigurieren Sie zuerst das VSIX-Paket durch Ändern der Datei source.extension.vsixmanifest im VSIX-Projekt ein. Erstellen Sie anschließend das VSIX-Paket, indem Sie die Lösung erstellen.

#### <a name="to-configure-the-vsix-package"></a>So konfigurieren Sie das VSIX-Paket

1. In **Projektmappen-Explorer**, öffnen Sie unter dem Projekt WebPartNode der **"Source.Extension.vsixmanifest"** Datei im manifest-Editor.

     Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie unter [Referenz zum VSIX-Erweiterungsschema 1.0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. In der **Produktname** geben **Web Part Gallery Node für Server-Explorer**.

3. In der **Autor** geben **Contoso**.

4. In der **Beschreibung** geben **des SharePoint-Verbindungsknotens im Server-Explorer einen benutzerdefinierten Webpartkatalog Knoten hinzugefügt. Diese Erweiterung verwendet einen benutzerdefinierten SharePoint-Befehl, um das Serverobjektmodell aufrufen.**

5. Wählen Sie die **Assets** Registerkarte des Editors, und wählen Sie dann die **neu** Schaltfläche.

     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.

6. In der **Typ** wählen **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    >  Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.

8. In der **Projekt** wählen **WebPartNodeExtension** und wählen Sie dann die **OK** Schaltfläche.

9. Wählen Sie im manifest-Editor die **neu** erneut.

     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.

10. In der **Typ** geben **SharePoint.Commands.v4**.

    > [!NOTE]
    >  Dieses Element gibt eine benutzerdefinierte Erweiterung, die in der Visual Studio-Erweiterung enthalten sein sollen. Weitere Informationen finden Sie unter [Asset-Element (VSX-Schema)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

11. In der **Quelle** wählen die **ein Projekt in der aktuellen Projektmappe** Listenelement.

12. In der **Projekt** wählen **WebPartCommands**, und wählen Sie dann die **OK** Schaltfläche.

13. Wählen Sie auf der Menüleiste **erstellen** > **Projektmappe**, und klicken Sie dann stellen Sie sicher, dass die Projektmappe ohne Fehler kompiliert wird.

14. Stellen Sie sicher, dass der Buildausgabeordner für das Projekt WebPartNode jetzt die Datei WebPartNode.VSIX enthält.

     Standardmäßig handelt es sich beim Buildausgabeordner um den Ordner "...\bin\Debug" in dem Ordner mit der Projektdatei.

## <a name="test-the-extension"></a>Testen Sie die Erweiterung
 Sie können nun so testen Sie das neue **Webpartkatalog** Knoten **Server-Explorer**. Debuggen Sie zunächst die Erweiterung in einer experimentellen Instanz von Visual Studio. Verwenden Sie dann auf die neue **Webparts** Knoten in der experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

#### <a name="to-start-debugging-the-extension"></a>So debuggen Sie die Erweiterung

1. Starten Sie neu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit Administratoranmeldeinformationen, und öffnen Sie die Projektmappe WebPartNode.

2. Öffnen Sie die Codedatei SiteNodeExtension WebPartNodeExtension im Projekt und dann fügen Sie einen Haltepunkt auf der ersten Zeile des Codes in der `NodeChildrenRequested` und `CreateWebPartNodes` Methoden.

3. Wählen Sie die **F5** Schlüssel mit dem Debuggen beginnen.

     Visual Studio wird die Erweiterung installiert wird, um %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Part Gallery-Knoten-Erweiterung für Server Explorer\1.0 und eine experimentelle Instanz von Visual Studio. Sie testen das Projektelement in dieser Instanz von Visual Studio.

#### <a name="to-test-the-extension"></a>So testen Sie die Erweiterung

1. In der experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wählen Sie auf der Menüleiste **Ansicht** > **Server-Explorer**.

2. Führen Sie die folgenden Schritte aus, wenn die SharePoint-Website, die für Tests verwendet werden sollen nicht, unter angezeigt wird dem **SharePoint-Verbindungen** Knoten **Server-Explorer**:

    1. In **Server-Explorer**, öffnen Sie das Kontextmenü für **SharePoint-Verbindungen**, und wählen Sie dann **Verbindung hinzufügen**.

    2. In der **SharePoint-Verbindung hinzufügen** Dialogfeld Geben Sie die URL für die SharePoint-Website, die Sie möchten eine Verbindung herstellen, und wählen Sie dann die **OK** Schaltfläche.

         Geben Sie zum Angeben der SharePoint-Website auf Ihrem Entwicklungscomputer **http://localhost**.

3. Erweitern Sie den Website-Verbindungsknoten (in der die URL Ihrer Website angezeigt wird), und klicken Sie dann einen untergeordneten Standort Knoten (z. B. **Teamwebsite**).

4. Überprüfen Sie, ob der Code in der anderen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] beendet wird, an dem Haltepunkt, die Sie zuvor im Festlegen der `NodeChildrenRequested` -Methode, und wählen Sie dann **F5** , um das Debuggen des Projekts fortzusetzen.

5. In der experimentellen Instanz von Visual Studio, stellen Sie sicher, dass ein neuer Knoten namens **Webpartkatalog** unter dem Knoten für Standort der obersten Ebene angezeigt wird, und erweitern Sie dann die **Webpartkatalog** Knoten.

6. Stellen Sie sicher, dass die codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, die Sie zuvor im Festlegen der `CreateWebPartNodes` -Methode, und wählen Sie dann die **F5** Schlüssel, um das Debuggen des Projekts fortzusetzen.

7. In der experimentellen Instanz von Visual Studio, überprüfen Sie, ob alle Webparts auf der verbundenen-Website unter der **Webpartkatalog** Knoten **Server-Explorer**.

8. In **Server-Explorer**, öffnen Sie das Kontextmenü für eines der Webparts, und wählen Sie dann **Eigenschaften**.

9. In der Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , die Sie Debuggen, überprüfen Sie, ob Details zu das Webpart in der **Eigenschaften** Fenster.

## <a name="uninstall-the-extension-from-visual-studio"></a>Deinstallieren Sie die Erweiterung von Visual Studio
 Nachdem Sie das Testen der Erweiterung abgeschlossen haben, deinstallieren Sie die Erweiterung von Visual Studio.

#### <a name="to-uninstall-the-extension"></a>So deinstallieren Sie die Erweiterung

1. In der experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wählen Sie auf der Menüleiste **Tools** > **Erweiterungen und Updates**.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2. Wählen Sie in der Liste der Erweiterungen, **Web Part Gallery-Node-Extension für Server-Explorer**, und wählen Sie dann die **Deinstallieren** Schaltfläche.

3. Wählen Sie in das Dialogfeld, das angezeigt wird, die **Ja** , um zu bestätigen, dass Sie verwenden möchten, deinstallieren Sie die Erweiterung aus, und wählen Sie dann die **jetzt neu starten** Schaltfläche, um die Deinstallation abzuschließen.

4. Schließen Sie beide Instanzen von Visual Studio (die experimentelle Instanz und die Instanz von Visual Studio, in dem die Projektmappe WebPartNode geöffnet ist).

## <a name="see-also"></a>Siehe auch
- [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Exemplarische Vorgehensweise: Rufen Sie in der SharePoint-Clientobjektmodell innerhalb einer Server-explorererweiterung](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [Bildbearbeitung für Symbole](/cpp/windows/image-editor-for-icons)
- [Erstellen eines Symbols oder anderen Bilds &#40;Bildbearbeitung für Symbole&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
