---
title: 'Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projektelementtyps | Microsoft Docs'
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e2f39fc15d73b2019e739d7695f40cf0e3fd0940
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-extending-a-sharepoint-project-item-type"></a>Exemplarische Vorgehensweise: Erweitern eines SharePoint-Elementtyps
  Sie können die **Business Data Connectivity-Modell** Projektelement ein Modell für den Business Data Connectivity (BDC)-Dienst in SharePoint erstellt. Wenn Sie mit diesem Projektelement ein Modell erstellen, werden die Daten Benutzern im Modell standardmäßig nicht angezeigt. Sie müssen zusätlzlich eine externe Liste in SharePoint erstellen, damit Benutzer die Daten einsehen können.  
  
 In dieser exemplarischen Vorgehensweise erstellen Sie eine Erweiterung für die **Business Data Connectivity-Modell** Projektelement. Entwickler können mithilfe der Erweiterung eine externe Liste in ihrem Projekt erstellen, die die Daten im BDC-Modell anzeigt. Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer Visual Studio-Erweiterung, die zwei Hauptaufgaben ausführt:  
  
    -   Es wird eine externe Liste generiert, die die Daten in einem BDC-Modell anzeigt. Die Erweiterung verwendet das Objektmodell für das SharePoint-Projektsystem, um eine Datei Elements.xml zu generieren, die die Liste definiert. Außerdem wird die Datei zum Projekt hinzugefügt, damit sie zusammen mit dem BDC-Modell bereitgestellt werden kann.  
  
    -   Es fügt ein Kontextmenüelements zu den **Business Data Connectivity-Modell** Projektelemente in **Projektmappen-Explorer**. Entwickler können auf dieses Menüelement klicken, um eine externe Liste für das BDC-Modell zu generieren.  
  
-   Erstellen eines Visual Studio-Erweiterungspakets (VSIX) zum Bereitstellen der Erweiterungsassembly.  
  
-   Testen der Erweiterung.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von Microsoft Windows, SharePoint und Visual Studio. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Die [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Diese exemplarische Vorgehensweise verwendet die **VSIX-Projekt** Vorlage im SDK, um ein VSIX-Paket zum Bereitstellen des Projektelements zu erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Den BDC-Dienst in [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]. Weitere Informationen finden Sie unter [BDC-Architektur](http://go.microsoft.com/fwlink/?LinkId=177798).  
  
-   Das XML-Schema für BDC-Modelle. Weitere Informationen finden Sie unter [BDC-Modell Infrastruktur](http://go.microsoft.com/fwlink/?LinkId=177799).  
  
## <a name="creating-the-projects"></a>Erstellen der Projekte  
 Zum Abschließen dieser exemplarischen Vorgehensweise müssen Sie zwei Projekte erstellen:  
  
-   Ein VSIX-Projekt für die Erstellung des VSIX-Pakets zum Bereitstellen der Projektelementerweiterung  
  
-   Ein Klassenbibliotheksprojekt, das die Projektelementerweiterung implementiert  
  
 Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
3.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann die **Erweiterbarkeit** Knoten.  
  
    > [!NOTE]  
    >  Die **Erweiterbarkeit** Knoten ist nur verfügbar, wenn Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.  
  
4.  In der Liste am oberen Rand der **neues Projekt** Dialogfeld Wählen Sie **.NET Framework 4.5**.  
  
     Für SharePoint-Tools-Erweiterungen werden Funktionen aus dieser .NET Framework-Version benötigt.  
  
5.  Wählen Sie die **VSIX-Projekt** Vorlage.  
  
6.  In der **Namen** geben **"GenerateExternalDataLists"**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Fügt der **"GenerateExternalDataLists"** Projekt **Projektmappen-Explorer**.  
  
7.  Wenn die Datei "Source.Extension.vsixmanifest" nicht automatisch geöffnet wird, öffnen Sie das Kontextmenü im Projekt "GenerateExternalDataLists", und wählen Sie dann **öffnen**  
  
8.  Stellen Sie sicher, dass im Feld "Autor" der Datei "source.extension.vsixmanifest" ein Eintrag vorhanden ist (geben Sie "Contoso" ein), und speichern und schließen Sie dann die Datei.  
  
#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **"GenerateExternalDataLists"** Projektmappenknoten, wählen Sie **hinzufügen**, und wählen Sie dann **neues Projekt**.  
  
2.  In der **neues Projekt hinzufügen** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann die **Windows** Knoten.  
  
3.  Wählen Sie in der Liste am oberen Rand des Dialogfelds "" **.NET Framework 4.5**.  
  
4.  Wählen Sie in der Liste der Projektvorlagen **-Klassenbibliothek**.  
  
5.  In der **Namen** geben **"BdcProjectItemExtension"**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Fügt der **"BdcProjectItemExtension"** Projekt der Projektmappe und öffnet die Class1-Codedatei.  
  
6.  Löschen Sie die Class1-Codedatei aus dem Projekt.  
  
## <a name="configuring-the-extension-project"></a>Konfigurieren des Erweiterungsprojekts  
 Bevor Sie Code zum Erstellen der Projektelementerweiterung schreiben, fügen Sie dem Erweiterungsprojekt Codedateien und Assemblyverweise hinzu.  
  
#### <a name="to-configure-the-project"></a>So konfigurieren Sie das Projekt  
  
1.  Fügen Sie im Projekt "BdcProjectItemExtension" zwei Codedateien mit den folgenden Namen hinzu:  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  Wählen Sie das Projekt "BdcProjectItemExtension" und anschließend auf der Menüleiste die Optionen **Projekt**, **Verweis hinzufügen**.  
  
3.  Klicken Sie unter der **Assemblys** Knoten, wählen Sie die **Framework** Knoten, und aktivieren Sie das Kontrollkästchen für jede der folgenden Assemblys:  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  Klicken Sie unter der **Assemblys** Knoten, wählen Sie die **Erweiterungen** Knoten, und wählen Sie dann das Kontrollkästchen für die folgende Assembly:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Klicken Sie auf die Schaltfläche **OK** .  
  
## <a name="defining-the-project-item-extension"></a>Definieren der Projektelementerweiterung  
 Erstellen Sie eine Klasse, die die Erweiterung definiert die **Business Data Connectivity-Modell** Projektelement. Die Klasse implementiert die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>-Schnittstelle, um die Erweiterung zu definieren. Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen vorhandenen Projektelementtyp erweitern möchten.  
  
#### <a name="to-define-the-project-item-extension"></a>So definieren Sie eine Projektelementerweiterung  
  
1.  Fügen Sie in der Codedatei "ProjectItemExtension" folgenden Code ein.  
  
    > [!NOTE]  
    >  Nach dem Hinzufügen dieses Codes weist das Projekt einige Kompilierungsfehler auf. Diese Fehler werden durch Code behoben, den Sie in späteren Schritten hinzufügen.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## <a name="creating-the-external-data-lists"></a>Erstellen der externen Datenlisten  
 Fügen Sie eine partielle Definition der `GenerateExternalDataListsExtension`-Klasse hinzu, die im BDC-Modell eine externe Datenliste für jede Entität erstellt. Um die externe Datenliste zu erstellen, werden im Code zuerst die Entitätsdaten aus dem BDC-Modell gelesen, indem die XML-Daten in der BDC-Modelldatei analysiert werden. Anschließend wird eine Listeninstanz basierend auf dem BDC-Modell erstellt und zum Projekt hinzugefügt.  
  
#### <a name="to-create-the-external-data-lists"></a>So erstellen Sie die externen Datenlisten  
  
1.  Fügen Sie in der Codedatei "GenerateExternalDataLists" folgenden Code ein.  
  
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte für die Projektelementerweiterung benötigte Code in das Projekt eingefügt. Erstellen Sie die Projektmappe, um sicherzustellen, dass das Projekt ohne Fehler kompiliert wird.  
  
#### <a name="to-build-the-solution"></a>So erstellen Sie die Projektmappe  
  
1.  Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item-extension"></a>Erstellen eines VSIX-Pakets, um die Projektelementerweiterung bereitzustellen  
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX-Projekts in der Lösung ein VSIX-Paket. Konfigurieren Sie zuerst das VSIX-Paket, indem Sie die im VSIX-Projekt enthaltene Datei "source.extension.vsixmanifest" ändern. Erstellen Sie anschließend das VSIX-Paket, indem Sie die Lösung erstellen.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>So erstellen und konfigurieren Sie das VSIX-Paket  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die Datei "Source.Extension.vsixmanifest" im Projekt "GenerateExternalDataLists", und wählen Sie dann **öffnen**.  
  
     Die Datei wird von Visual Studio im Manifest-Editor geöffnet. Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie unter [VSIX-Erweiterung Schemareferenz 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  In der **Produktname** geben **External Data List Generator**.  
  
3.  In der **Autor** geben **Contoso**.  
  
4.  In der **Beschreibung** geben **eine Erweiterung für Projektelemente des Business Data Connectivity-Modell, die verwendet werden können, zum Generieren externer Datenlisten**.  
  
5.  Auf der **Bestand** Registerkarte im Editor wählen Sie die **neu** Schaltfläche.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.  
  
6.  In der **Typ** wählen **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.  
  
8.  In der **Projekt** wählen **"BdcProjectItemExtension"**, und wählen Sie dann die **OK** Schaltfläche.  
  
9. Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
10. Stellen Sie sicher, dass das Projekt fehlerfrei kompiliert und erstellt wird.  
  
11. Überprüfen Sie, ob im Buildausgabeordner des Projekts "GenerateExternalDataLists" jetzt die Datei "GenerateExternalDataLists.vsix" vorhanden ist.  
  
     Standardmäßig handelt es sich beim Buildausgabeordner um den Ordner "...\bin\Debug" in dem Ordner mit der Projektdatei.  
  
## <a name="testing-the-project-item-extension"></a>Testen der Projektelementerweiterung  
 Jetzt können Sie die Projektelementerweiterung testen. Debuggen Sie das Erweiterungsprojekt zunächst in der experimentellen Instanz von Visual Studio. Verwenden Sie die Erweiterung dann in der experimentellen Instanz von Visual Studio, um eine externe Liste für ein BDC-Modell zu generieren. Öffnen Sie abschließend die externe Liste auf der SharePoint-Website, um sicherzustellen, dass die Liste einwandfrei funktioniert.  
  
#### <a name="to-start-debugging-the-extension"></a>So debuggen Sie die Erweiterung  
  
1.  Starten Sie ggf. Visual Studio mit Administratoranmeldeinformationen neu, und öffnen Sie dann die Projektmappe "GenerateExternalDataLists".  
  
2.  Öffnen Sie im Projekt "BdcProjectItemExtension" die Codedatei "ProjectItemExtension", und fügen Sie dann der Codezeile in der `Initialize`-Methode einen Haltepunkt hinzu.  
  
3.  Öffnen Sie die Codedatei "GenerateExternalDataLists", und fügen Sie dann der ersten Codezeile in der `GenerateExternalDataLists_Execute`-Methode einen Haltepunkt hinzu.  
  
4.  Starten Sie durch Auswählen der F5-Taste, oder, in der Menüleiste **Debuggen**, **Debuggen**.  
  
     Die Erweiterung wird unter "%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Data List Generator\1.0" installiert, und eine experimentelle Instanz von Visual Studio wird gestartet. Sie testen das Projektelement in dieser Instanz von Visual Studio.  
  
#### <a name="to-test-the-extension"></a>So testen Sie die Erweiterung  
  
1.  Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **Datei**, **neu**, **Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie die **Vorlagen** Knoten, erweitern Sie die **Visual C#-** Knoten, erweitern Sie die **SharePoint** Knoten, und dann Wählen Sie **2010**.  
  
3.  Stellen Sie in der Liste am oberen Rand des Dialogfelds sicher, dass **.NET Framework 3.5** ausgewählt ist. Projekte für [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] erfordern diese Version von .NET Framework.  
  
4.  Wählen Sie in der Liste der Projektvorlagen **SharePoint 2010-Projekt**.  
  
5.  In der **Namen** geben **SharePointProjectTestBDC**, und wählen Sie dann die **OK** Schaltfläche.  
  
6.  Geben Sie die URL der Site, die Sie verwenden möchten, zum Debuggen verwenden, wählen im Assistent zum Anpassen von SharePoint **als farmlösung bereitstellen**, und wählen Sie dann die **Fertig stellen**Schaltfläche.  
  
7.  Öffnen Sie das Kontextmenü für die Projekts "sharepointprojecttestbdc", wählen Sie **hinzufügen**, und wählen Sie dann **neues Element**.  
  
8.  In der **neues Element hinzufügen – SharePointProjectTestBDC** Dialogfeld Feld, erweitern Sie den installierten Sprachknoten und den **SharePoint** Knoten.  
  
9. Wählen Sie die **2010** Knoten, und wählen Sie dann die **Business Data Connectivity-Modell (nur Farmlösung)** Vorlage.  
  
10. In der **Namen** geben **"TestBDCModel"**, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
11. Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie in der `Initialize`-Methode der Codedatei "ProjectItemExtension" festgelegt haben.  
  
12. In der beendeten Instanz von Visual Studio, wählen Sie die **F5** Taste, oder wählen Sie in der Menüleiste **Debuggen**, **Fortfahren** , um das Debuggen des Projekts fortzusetzen.  
  
13. Wählen Sie in der experimentellen Instanz von Visual Studio die **F5** Taste, oder wählen Sie in der Menüleiste **Debuggen**, **Debuggen** zum Erstellen, bereitstellen und Ausführen der  **"TestBDCModel"** Projekt.  
  
     Im Webbrowser wird die Standardseite der für das Debugging angegebenen SharePoint-Website geöffnet.  
  
14. Überprüfen Sie, ob die **listet** Abschnitt im Schnellstartbereich nicht noch eine Liste, die basierend auf dem BDC-Standardmodell im Projekt enthalten. Sie müssen zuerst eine externe Datenliste erstellen, entweder mit der SharePoint-Benutzeroberfläche oder mit der Projektelementerweiterung.  
  
15. Schließen Sie den Webbrowser.  
  
16. In der Instanz von Visual Studio, die das Projekt "TestBDCModel" geöffnet ist, öffnen Sie das Kontextmenü für die **"TestBDCModel"** Knoten **Projektmappen-Explorer**, und wählen Sie dann **externe Daten generieren Liste**.  
  
17. Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie in der `GenerateExternalDataLists_Execute`-Methode festgelegt haben. Wählen Sie die **F5** Taste, oder wählen Sie in der Menüleiste **Debuggen**, **Fortfahren** , um das Debuggen des Projekts fortzusetzen.  
  
18. Die experimentelle Instanz von Visual Studio fügt eine Listeninstanz mit dem Namen **Entity1DataList** der "TestBDCModel"-Projekt, und die Instanz generiert außerdem eine Funktion mit dem Namen **Feature2** Liste -Instanz.  
  
19. Wählen Sie die **F5** Taste, oder wählen Sie in der Menüleiste **Debuggen**, **Debuggen** zum Erstellen, bereitstellen, und führen Sie das Projekt "TestBDCModel".  
  
     Im Webbrowser wird die Standardseite der SharePoint-Website geöffnet, die zum Debugging verwendet wird.  
  
20. In der **listet** Abschnitt der Schnellstartbereich, wählen Sie die **Entity1DataList** Liste.  
  
21. Überprüfen Sie, ob die Liste neben den Spalten "Identifier1" und "Message" ebenfalls ein Element mit dem Wert "0" für "Identifier1" und dem Wert "Hello World" für "Message" enthält.  
  
     Die **Business Data Connectivity-Modell** -Projektvorlage generiert das BDC-Standardmodell, die dieser Daten bereitstellt.  
  
22. Schließen Sie den Webbrowser.  
  
## <a name="cleaning-up-the-development-computer"></a>Bereinigen des Entwicklungscomputers  
 Nachdem Sie die Tests der Projektelementerweiterung abgeschlossen haben, entfernen Sie die externe Liste und das BDC-Modell von der SharePoint-Website, und entfernen Sie die Projektelementerweiterung aus Visual Studio.  
  
#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>So entfernen Sie die externe Datenliste von der SharePoint-Website  
  
1.  Wählen Sie im Schnellstartbereich der SharePoint-Website, die **Entity1DataList** Liste.  
  
2.  Wählen Sie im Menüband auf der SharePoint-Website, die **Liste** Registerkarte.  
  
3.  Auf der **Liste** Registerkarte die **Einstellungen** Gruppe **Listeneinstellungen**.  
  
4.  Klicken Sie unter **Berechtigungen und Verwaltung**, wählen Sie **diese Liste löschen**, und wählen Sie dann **OK** zu bestätigen, dass Sie die Liste an den Papierkorb senden möchten.  
  
5.  Schließen Sie den Webbrowser.  
  
#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>So entfernen Sie das BDC-Modell von der SharePoint-Website  
  
1.  Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **erstellen**, **zurückziehen**.  
  
     Das BDC-Modell wird aus der SharePoint-Website entfernt.  
  
#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>So entfernen Sie die Projektelementerweiterung aus Visual Studio  
  
1.  Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **Tools**, **Erweiterungen und Updates**.  
  
     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.  
  
2.  Wählen Sie in der Liste der Erweiterungen, **External Data List Generator**, und wählen Sie dann die **Deinstallieren** Schaltfläche.  
  
3.  Wählen Sie im angezeigten Dialogfeld **Ja** zu bestätigen, dass Sie die Erweiterung deinstallieren möchten.  
  
4.  Wählen Sie **jetzt neu starten** um die Deinstallation abzuschließen.  
  
5.  Schließen Sie beide Visual Studio-Instanzen (sowohl die experimentelle als auch die Instanz mit der geöffneten Projektmappe "GenerateExternalDataLists").  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  