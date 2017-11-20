---
title: 'Exemplarische Vorgehensweise: Aufrufe in die SharePoint-Clientobjektmodell innerhalb einer Server-Explorererweiterung | Microsoft Docs'
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
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
ms.assetid: 897d3798-42c1-4fff-b280-8b84b53d80c6
caps.latest.revision: "100"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 489a11c215fe590b85e9dfaf5cbd815fdc43acb3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Exemplarische Vorgehensweise: Aufrufe in das SharePoint-Clientobjektmodell innerhalb einer Server-Explorererweiterung
  Diese exemplarische Vorgehensweise veranschaulicht, wie aus einer Erweiterung für das SharePoint-Clientobjektmodell Aufrufen der **SharePoint-Verbindungen** Knoten **Server-Explorer**. Weitere Informationen zur Verwendung des SharePoint-Clientobjektmodells finden Sie unter [Aufrufe in die SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung, die erweitert die **SharePoint-Verbindungen** Knoten **Server-Explorer** auf folgende Weise:  
  
    -   Fügt die Erweiterung einer **Webpartkatalog** unter jedem SharePoint-Website-Knoten im Knoten **Server-Explorer**. Dieser neue Knoten enthält untergeordnete Knoten, die jedes Webpart in den Webpartkatalog auf der Website darstellen.  
  
    -   Die Erweiterung definiert einen neuen Typ von Knoten, der eine Webpart-Instanz darstellt. Diese neuen Knotentyps bildet die Grundlage für die untergeordneten Knoten unter der neuen **Webpartkatalog** Knoten. Die neuen Knotentyps-Webpart zeigt die Informationen in den **Eigenschaften** Fenster über das Webpart, das der Knoten darstellt.  
  
-   Erstellen eines Visual Studio-Erweiterung (VSIX) zum Bereitstellen der Erweiterung.  
  
-   Debuggen und Testen der Erweiterung.  
  
> [!NOTE]  
>  Die Erweiterung, die Sie in dieser exemplarischen Vorgehensweise erstellen, ähnelt der Erweiterung, die Sie in erstellen [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). Diese exemplarische Vorgehensweise verwendet das SharePoint-Serverobjektmodell, während diese exemplarische Vorgehensweise führt dieselben Aufgaben mithilfe des Clientobjektmodells.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von Windows, SharePoint und Visual Studio. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Das Visual Studio SDK. Diese exemplarische Vorgehensweise verwendet die **VSIX-Projekt** Vorlage im SDK, um ein VSIX-Paket zum Bereitstellen der Erweiterung zu erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Verwenden das SharePoint-Clientobjektmodell. Weitere Informationen finden Sie unter [verwaltetes Clientobjektmodell](http://go.microsoft.com/fwlink/?LinkId=177797).  
  
-   Webparts in SharePoint. Weitere Informationen finden Sie unter [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="creating-the-projects"></a>Erstellen der Projekte  
 Zum Durchführen dieser exemplarischen Vorgehensweise müssen Sie zwei Projekte erstellen:  
  
-   Ein VSIX-Projekt so erstellen das VSIX-Paket zum Bereitstellen der **Server-Explorer** Erweiterung.  
  
-   Ein Klassenbibliotheksprojekt, das implementiert die **Server-Explorer** Erweiterung.  
  
 Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
3.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann **Erweiterbarkeit**.  
  
    > [!NOTE]  
    >  Die **Erweiterbarkeit** Knoten ist nur verfügbar, wenn Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.  
  
4.  Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 4.5** in der Liste der Versionen von .NET Framework.  
  
     SharePoint-Tools-Erweiterungen werden Funktionen in dieser Version von .NET Framework erfordern.  
  
5.  Wählen Sie die **VSIX-Projekt** Vorlage.  
  
6.  In der **Namen** geben **WebPartNode**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Fügt der **WebPartNode** Projekt **Projektmappen-Explorer**.  
  
#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen Sie **hinzufügen**, und wählen Sie dann **neues Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann **Windows**.  
  
3.  Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 4.5** in der Liste der Versionen von .NET Framework.  
  
4.  Wählen Sie in der Liste der Projektvorlagen **-Klassenbibliothek**.  
  
5.  In der **Namen** geben **WebPartNodeExtension**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Fügt der **WebPartNodeExtension** Projekt der Projektmappe und öffnet die Class1-Codedatei.  
  
6.  Löschen Sie die Class1-Codedatei aus dem Projekt.  
  
## <a name="configuring-the-extension-project"></a>Konfigurieren des Erweiterungsprojekts  
 Bevor Sie Code zum Erstellen der Erweiterung schreiben, müssen Sie Codedateien und Assemblyverweise zu Ihrem Projekt hinzufügen und müssen Sie den Standardnamespace aktualisieren.  
  
#### <a name="to-configure-the-project"></a>So konfigurieren Sie das Projekt  
  
1.  In der **WebPartNodeExtension** Projekt, fügen Sie zwei Codedateien mit den Namen SiteNodeExtension und WebPartNodeTypeProvider hinzu.  
  
2.  Öffnen Sie das Kontextmenü für das Projekt WebPartNodeExtension, und wählen Sie dann **Verweis hinzufügen**.  
  
3.  In der **Verweis-Manager - WebPartNodeExtension** Dialogfeld Wählen Sie die **Framework** Knoten, und wählen Sie dann die Kontrollkästchen für System.ComponentModel.Composition und "System.Windows.Forms" Assemblys.  
  
4.  Wählen Sie die **Erweiterungen** Knoten, wählen Sie das Kontrollkästchen für jede der folgenden Assemblys, und wählen Sie dann die **OK** Schaltfläche:  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Öffnen Sie das Kontextmenü für die **WebPartNodeExtension** Projekt, und wählen Sie dann **Eigenschaften**.  
  
     Der **Projekt-Designer** wird geöffnet.  
  
6.  Wählen Sie die Registerkarte **Anwendung** aus.  
  
7.  In der **Standardnamespace** Feld (c#) oder **Stammnamespace** (Visual Basic) Geben Sie **Wert ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="creating-icons-for-the-new-nodes"></a>Erstellen von Symbolen für die neuen Knoten  
 Erstellen Sie zwei Symbole für die **Server-Explorer** Erweiterung: ein Symbol für die neue **Webpartkatalog** Knoten und ein anderes Symbol für jeden untergeordneten Webpart Knoten unter dem **Webpartkatalog** Knoten. Weiter unten in dieser exemplarischen Vorgehensweise fügen Sie Code schreiben, die diese Symbole Knoten zuordnet.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Zum Erstellen von Symbolen für die Knoten  
  
1.  In der **Projekt-Designer** für das Projekt WebPartNodeExtension wählen Sie die **Ressourcen** Registerkarte.  
  
2.  Wählen Sie den Link **dieses Projekt enthält keine Standarddatei für die Ressourcen. Klicken Sie hier, um eine zu erstellen.**  
  
     Visual Studio erstellt eine Ressourcendatei und im Designer geöffnet.  
  
3.  Am oberen Rand des Designers, wählen Sie auf den Pfeil auf der **Ressource hinzufügen** Menü Befehl, und wählen Sie dann **Symbol "Neu" hinzufügen**.  
  
4.  Geben Sie **WebPartsNode als Namen** für das Symbol "Neu" nennen, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Das Symbol "neue" wird geöffnet, der **Bildbearbeitung**.  
  
5.  Bearbeiten Sie die 16 x 16-Version des Symbols, sodass sie einen Entwurf aufweist, den Sie leicht erkennen können.  
  
6.  Öffnen Sie das Kontextmenü für die 32 x 32-Version des Symbols, und wählen Sie dann **Bildtyp löschen**.  
  
7.  Wiederholen Sie die Schritte 3 bis 7 der Projektressourcen ein Symbol hinzu, und nennen Sie dieses Symbol **WebPart**.  
  
8.  In **Projektmappen-Explorer**in der **Ressourcen** Ordner für die **WebPartNodeExtension** Projekts **Datei WebPartsNode.ico**.  
  
9. In der **Eigenschaften** geöffnete Fenster die **Buildvorgang** aus, und wählen Sie dann **eingebettete Ressource**.  
  
10. Wiederholen Sie die letzten beiden Schritte für **WebPart.ico**.  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>Server-Explorer hinzufügen den Knoten Webpartkatalog  
 Erstellen Sie eine Klasse, die die neue fügt **Webpartkatalog** Knoten für jeden Knoten des SharePoint-Website. Zum Hinzufügen des neuen Knotens, die Klasse implementiert die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Schnittstelle. Diese Schnittstelle implementieren, wenn Sie das Verhalten in einen vorhandenen Knoten erweitern möchten **Server-Explorer**, z. B. Hinzufügen eines Knotens einen neuen untergeordneten Knoten.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Server-Explorer den Knoten Webpartkatalog hinzu  
  
1.  Fügen Sie den folgenden Code in die **SiteNodeExtension** Codedatei für die **WebPartNodeExtension** Projekt.  
  
    > [!NOTE]  
    >  Nach dem Hinzufügen dieses Codes weist das Projekt einige Kompilierungsfehler auf. Diese Fehler werden durch Code behoben, den Sie in späteren Schritten hinzufügen.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>Definieren einen Knotentyp, das ein Webpart darstellt.  
 Erstellen Sie eine Klasse, die einen neuen Typ des Knotens definiert, das ein Webpart darstellt. Visual Studio verwendet diese neuen Knotentyps anzuzeigenden untergeordneten Knoten unter dem **Webpartkatalog** Knoten. Jedes dieser untergeordneten Knoten stellt ein einzelnes Webpart auf der SharePoint-Website.  
  
 Definieren Sie den neuen Knotentyp, implementiert die Klasse der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Schnittstelle. Diese Schnittstelle implementieren, wenn Sie einen neuen Typ des Knotens im definieren möchten **Server-Explorer**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Zum Definieren des Webpart-Knotentyp  
  
1.  Fügen Sie den folgenden Code in die **WebPartNodeTypeProvider** Codedatei für die **WebPartNodeExtension** Projekt.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## <a name="checkpoint"></a>Checkpoint  
 An diesem Punkt in der exemplarischen Vorgehensweise wurde der Code für die **Webpartkatalog** Knoten befindet sich jetzt im Projekt. Erstellen der **WebPartNodeExtension** Projekt, um sicherzustellen, dass sie fehlerfrei kompiliert wird.  
  
#### <a name="to-build-the-project"></a>So erstellen Sie das Projekt  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **WebPartNodeExtension** Projekt, und wählen Sie dann **erstellen**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Erstellen ein VSIX-Paket zum Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX-Projekts in der Lösung ein VSIX-Paket. Konfigurieren Sie zuerst das VSIX-Paket, durch Ändern der Datei "Source.Extension.vsixmanifest", die im Projekt enthalten ist. Dann erstellen Sie das VSIX-Paket, indem Sie beim Erstellen der Projektmappe.  
  
#### <a name="to-configure-the-vsix-package"></a>So konfigurieren Sie das VSIX-Paket  
  
1.  In **Projektmappen-Explorer**in der **WebPartNode** geöffneten Projekts **"Source.Extension.vsixmanifest"** Datei im manifest-Editor.  
  
     Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie unter [VSIX-Erweiterung Schemareferenz 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  In der **Produktname** geben **Web Part Gallery Node für Server-Explorer**.  
  
3.  In der **Autor** geben **Contoso**.  
  
4.  In der **Beschreibung** geben **des SharePoint-Verbindungsknotens im Server-Explorer einen benutzerdefinierten Webpartkatalog Knoten hinzugefügt**.  
  
5.  Auf der **Bestand** Registerkarte im Editor wählen Sie die **neu** Schaltfläche.  
  
6.  In der **neue Anlage hinzufügen** Dialogfeld die **Typ** wählen **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.  
  
8.  In der **Projekt** wählen **WebPartNodeExtension**, und wählen Sie dann die **OK** Schaltfläche.  
  
9. Wählen Sie in der Menüleiste **erstellen**, **Projektmappe**, und stellen Sie sicher, dass die Lösung ohne Fehler kompiliert wird.  
  
10. Stellen Sie sicher, dass der Buildausgabeordner für das Projekt WebPartNode jetzt die Datei WebPartNode.VSIX enthält.  
  
     Standardmäßig handelt es sich beim Buildausgabeordner um den Ordner "...\bin\Debug" in dem Ordner mit der Projektdatei.  
  
## <a name="testing-the-extension"></a>Testen der Erweiterung  
 Sie können nun den neuen test **Webpartkatalog** Knoten **Server-Explorer**. Starten Sie das Erweiterungsprojekt in einer experimentellen Instanz von Visual Studio debuggen. Verwenden Sie die neue **Webparts** Knoten in der experimentellen Instanz von Visual Studio.  
  
#### <a name="to-start-debugging-the-extension"></a>So debuggen Sie die Erweiterung  
  
1.  Starten Sie Visual Studio mit Administratorrechten, und öffnen Sie die **WebPartNode** Lösung.  
  
2.  Öffnen Sie im Projekt WebPartNodeExtension der **SiteNodeExtension** Codedatei, und fügen Sie einen Haltepunkt auf die ersten Zeilen des Codes in der `NodeChildrenRequested` und `CreateWebPartNodes` Methoden.  
  
3.  Drücken Sie die F5-TASTE, um das Debuggen zu starten.  
  
     Visual Studio die Erweiterung %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Teil Knoten Katalogerweiterung für Server Explorer\1.0 und eine experimentelle Instanz von Visual Studio wird gestartet. Sie testen das Projektelement in dieser Instanz von Visual Studio.  
  
#### <a name="to-test-the-extension"></a>So testen Sie die Erweiterung  
  
1.  Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **Ansicht**, **Server-Explorer**.  
  
2.  Stellen Sie sicher, dass die SharePoint-Website, die Sie zum Testen verwenden möchten unter angezeigt wird der **SharePoint-Verbindungen** Knoten **Server-Explorer**. Wenn es nicht aufgeführt ist, gehen Sie folgendermaßen vor:  
  
    1.  Öffnen Sie das Kontextmenü für **SharePoint-Verbindungen**, und wählen Sie dann **Verbindung hinzufügen**.  
  
    2.  In der **SharePoint-Verbindung hinzufügen** Dialogfeld Geben Sie die URL für die SharePoint-Website, die Sie möchten eine Verbindung herstellen, und wählen Sie dann die **OK** Schaltfläche.  
  
         Geben Sie die SharePoint-Website auf dem Entwicklungscomputer an, indem **http://localhost**.  
  
3.  Erweitern Sie den Website-Verbindungsknoten (in der die URL Ihrer Website angezeigt werden), und dann einen untergeordneten Standort Knoten (z. B. **Teamwebsite**).  
  
4.  Stellen Sie sicher, dass der Code in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, die Sie zuvor im Festlegen der `NodeChildrenRequested` -Methode, und wählen Sie dann die F5-Taste, um das Debuggen des Projekts fortzusetzen.  
  
5.  Erweitern Sie in der experimentellen Instanz von Visual Studio die **Webpartkatalog** Knoten, die unter dem Knoten der Standort der obersten Ebene angezeigt wird.  
  
6.  Stellen Sie sicher, dass der Code in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, die Sie zuvor im Festlegen der `CreateWebPartNodes` -Methode, und wählen Sie dann die F5-Taste, um das Debuggen des Projekts fortzusetzen.  
  
7.  In der experimentellen Instanz von Visual Studio, überprüfen Sie, ob alle Webparts auf die verbundene Website unter der **Webpartkatalog** Knoten **Server-Explorer**.  
  
8.  Öffnen Sie das Kontextmenü für ein Webpart, und wählen Sie dann **Eigenschaften**.  
  
9. In der **Eigenschaften** Fenster, stellen Sie sicher, dass die Details zum Webpart angezeigt.  
  
10. In **Server-Explorer**, öffnen Sie das Kontextmenü für das gleiche Webpart, und wählen Sie dann **angezeigte Meldung**.  
  
     Klicken Sie im Meldungsfeld, das angezeigt wird, wählen Sie die **OK** Schaltfläche.  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>Deinstallieren die Erweiterung von Visual Studio  
 Nachdem Sie das Testen der Erweiterung abgeschlossen haben, deinstallieren Sie es in Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>So deinstallieren Sie die Erweiterung  
  
1.  Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **Tools**, **Erweiterungen und Updates**.  
  
     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.  
  
2.  Wählen Sie in der Liste der Erweiterungen, **Web Part Gallery Node für Server-Explorer**, und wählen Sie dann die **Deinstallieren** Schaltfläche.  
  
3.  Wählen Sie im angezeigten Dialogfeld die **Ja** Schaltfläche.  
  
4.  Wählen Sie die **jetzt neu starten** Schaltfläche, um die Deinstallation abzuschließen.  
  
     Das Projektelement wird ebenfalls deinstalliert.  
  
5.  Schließen Sie beide Instanzen von Visual Studio (die experimentelle Instanz und die Instanz von Visual Studio in der die Projektmappe WebPartNode geöffnet ist).  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufe in die SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Bildbearbeitung für Symbole](/cpp/windows/image-editor-for-icons)   
 [Erstellen ein Symbol oder anderen Bilds &#40; Bildbearbeitung für Symbole &#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  