---
title: "Walkthrough: Extending a SharePoint Project Item Type | Microsoft Docs"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 1cea4e0f-ce33-4cd7-a664-800184865456
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Walkthrough: Extending a SharePoint Project Item Type
  Mithilfe des Projektelements **Business Data Connectivity\-Modell** können Sie ein Modell für den Business Data Connectivity \(BDC\)\-Dienst in SharePoint erstellen.  Wenn Sie mit diesem Projektelement ein Modell erstellen, werden die Daten Benutzern im Modell standardmäßig nicht angezeigt.  Sie müssen zusätlzlich eine externe Liste in SharePoint erstellen, damit Benutzer die Daten einsehen können.  
  
 In dieser exemplarischen Vorgehensweise erstellen Sie eine Erweiterung für das Projektelement **Business Data Connectivity\-Modell**.  Entwickler können mithilfe der Erweiterung eine externe Liste in ihrem Projekt erstellen, die die Daten im BDC\-Modell anzeigt.  Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer Visual Studio\-Erweiterung, die zwei Hauptaufgaben ausführt:  
  
    -   Es wird eine externe Liste generiert, die die Daten in einem BDC\-Modell anzeigt.  Die Erweiterung verwendet das Objektmodell für das SharePoint\-Projektsystem, um eine Datei Elements.xml zu generieren, die die Liste definiert.  Außerdem wird die Datei zum Projekt hinzugefügt, damit sie zusammen mit dem BDC\-Modell bereitgestellt werden kann.  
  
    -   Den Projektelementen für das **Business Data Connectivity\-Modell** im **Projektmappen\-Explorer** wird ein Kontextmenüelement hinzugefügt.  Entwickler können auf dieses Menüelement klicken, um eine externe Liste für das BDC\-Modell zu generieren.  
  
-   Erstellen eines Visual Studio\-Erweiterungspakets \(VSIX\) zum Bereitstellen der Erweiterungsassembly.  
  
-   Testen der Erweiterung.  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von Microsoft Windows, SharePoint und Visual Studio.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  Diese exemplarische Vorgehensweise verwendet die Vorlage **VSIX Project** im SDK, um ein VSIX\-Paket zum Bereitstellen des Projektelements zu erstellen.  Weitere Informationen finden Sie unter [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Den BDC\-Dienst in [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)].  Weitere Informationen finden Sie unter [BDC\-Architektur](http://go.microsoft.com/fwlink/?LinkId=177798).  
  
-   Das XML\-Schema für BDC\-Modelle.  Weitere Informationen finden Sie unter [Infrastruktur des BDC\-Modells](http://go.microsoft.com/fwlink/?LinkId=177799).  
  
## Erstellen der Projekte  
 Zum Abschließen dieser exemplarischen Vorgehensweise müssen Sie zwei Projekte erstellen:  
  
-   Ein VSIX\-Projekt für die Erstellung des VSIX\-Pakets zum Bereitstellen der Projektelementerweiterung  
  
-   Ein Klassenbibliotheksprojekt, das die Projektelementerweiterung implementiert  
  
 Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### So erstellen Sie das VSIX\-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
3.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C\#** oder **Visual Basic**, und wählen Sie dann den Knoten **Erweiterungen** aus.  
  
    > [!NOTE]  
    >  Der Knoten **Erweiterungen** ist nur verfügbar, wenn Sie das Visual Studio SDK installieren.  Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.  
  
4.  Wählen Sie in der Liste am oberen Rand des Dialogfelds **Neues Projekt** den Eintrag **.NET Framework 4.5** aus.  
  
     Für SharePoint\-Tools\-Erweiterungen werden Funktionen aus dieser .NET Framework\-Version benötigt.  
  
5.  Wählen Sie die Vorlage **VSIX\-Projekt** aus.  
  
6.  Geben Sie im Feld **Name** die Zeichenfolge **GenerateExternalDataLists** ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt dem **Projektmappen\-Explorer** das Projekt **GenerateExternalDataLists** hinzu.  
  
7.  Wenn die Datei "source.extension.vsixmanifest" nicht automatisch geöffnet wird, öffnen Sie im Projekt "GenerateExternalDataLists" das zugehörige Kontextmenü, und wählen Sie dann **Öffnen** aus.  
  
8.  Stellen Sie sicher, dass im Feld "Autor" der Datei "source.extension.vsixmanifest" ein Eintrag vorhanden ist \(geben Sie "Contoso" ein\), und speichern und schließen Sie dann die Datei.  
  
#### So erstellen Sie das Erweiterungsprojekt  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den Projektmappenknoten **GenerateExternalDataLists**, und wählen Sie **Hinzufügen** sowie anschließend **Neues Projekt** aus.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten wird der Projektmappenknoten nur im **Projektmappen\-Explorer** angezeigt, wenn das Kontrollkästchen **Projektmappe immer anzeigen** in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/de-de/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) aktiviert ist.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt hinzufügen** den Knoten **Visual C\#** oder **Visual Basic**, und wählen Sie dann den Knoten **Windows** aus.  
  
3.  Wählen Sie in der Liste am oberen Rand des Dialogfelds den Eintrag **.NET Framework 4.5** aus.  
  
4.  Wählen Sie in der Liste der Projektvorlagen **Klassenbibliothek** aus.  
  
5.  Geben Sie im Feld **Name** die Zeichenfolge **BdcProjectItemExtension** ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **BdcProjectItemExtension** der Projektmappe hinzu und öffnet die Class1\-Codedatei.  
  
6.  Löschen Sie die Class1\-Codedatei aus dem Projekt.  
  
## Konfigurieren des Erweiterungsprojekts  
 Bevor Sie Code zum Erstellen der Projektelementerweiterung schreiben, fügen Sie dem Erweiterungsprojekt Codedateien und Assemblyverweise hinzu.  
  
#### So konfigurieren Sie das Projekt  
  
1.  Fügen Sie im Projekt "BdcProjectItemExtension" zwei Codedateien mit den folgenden Namen hinzu:  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  Wählen Sie das Projekt "BdcProjectItemExtension" und anschließend in der Menüleiste **Projekt** sowie **Verweis hinzufügen** aus.  
  
3.  Wählen Sie unter dem Knoten **Assemblys** den Knoten **Framework** aus, und aktivieren Sie das Kontrollkästchen für jede der folgenden Assemblys:  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  Wählen Sie unter dem Knoten **Assemblys** den Knoten **Erweiterungen** aus, und aktivieren Sie dann das Kontrollkästchen für die folgende Assembly:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Klicken Sie auf die Schaltfläche **OK**.  
  
## Definieren der Projektelementerweiterung  
 Erstellen Sie eine Klasse, die die Erweiterung für das Projektelement **Business Data Connectivity\-Modell** definiert.  Die Klasse implementiert die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>\-Schnittstelle, um die Erweiterung zu definieren.  Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen vorhandenen Projektelementtyp erweitern möchten.  
  
#### So definieren Sie eine Projektelementerweiterung  
  
1.  Fügen Sie in der Codedatei "ProjectItemExtension" folgenden Code ein.  
  
    > [!NOTE]  
    >  Nach dem Hinzufügen dieses Codes weist das Projekt einige Kompilierungsfehler auf.  Diese Fehler werden durch Code behoben, den Sie in späteren Schritten hinzufügen.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/cs/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/vb/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## Erstellen der externen Datenlisten  
 Fügen Sie eine partielle Definition der `GenerateExternalDataListsExtension`\-Klasse hinzu, die im BDC\-Modell eine externe Datenliste für jede Entität erstellt.  Um die externe Datenliste zu erstellen, werden im Code zuerst die Entitätsdaten aus dem BDC\-Modell gelesen, indem die XML\-Daten in der BDC\-Modelldatei analysiert werden.  Anschließend wird eine Listeninstanz basierend auf dem BDC\-Modell erstellt und zum Projekt hinzugefügt.  
  
#### So erstellen Sie die externen Datenlisten  
  
1.  Fügen Sie in der Codedatei "GenerateExternalDataLists" folgenden Code ein.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/cs/bdcprojectitemextension/generateexternaldatalists.cs#2)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/vb/bdcprojectitemextension/generateexternaldatalists.vb#2)]  
  
## Checkpoint  
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte für die Projektelementerweiterung benötigte Code in das Projekt eingefügt.  Erstellen Sie die Projektmappe, um sicherzustellen, dass das Projekt ohne Fehler kompiliert wird.  
  
#### So erstellen Sie die Projektmappe  
  
1.  Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
## Erstellen eines VSIX\-Pakets, um die Projektelementerweiterung bereitzustellen  
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX\-Projekts in der Lösung ein VSIX\-Paket.  Konfigurieren Sie zuerst das VSIX\-Paket, indem Sie die im VSIX\-Projekt enthaltene Datei "source.extension.vsixmanifest" ändern.  Erstellen Sie anschließend das VSIX\-Paket, indem Sie die Lösung erstellen.  
  
#### So erstellen und konfigurieren Sie das VSIX\-Paket  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** im Projekt "GenerateExternalDataLists" das Kontextmenü der Datei "source.extension.vsixmanifest", und wählen Sie dann **Öffnen**aus.  
  
     Die Datei wird von Visual Studio im Manifest\-Editor geöffnet.  Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX\-Pakete erforderlich ist.  Weitere Informationen zu dieser Datei finden Sie unter [VSIX\-Erweiterungs\-Schemareferenz](http://msdn.microsoft.com/de-de/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Geben Sie im Feld **Produktname** den Namen **External Data List Generator** ein.  
  
3.  Geben Sie im Feld **Autor** den Namen **Contoso** ein.  
  
4.  Geben Sie im Feld **Beschreibung** die Beschreibung **Eine Erweiterung für Projektelemente des Business Data Connectivity\-Modells zum Generieren externer Datenlisten** ein.  
  
5.  Wählen Sie im Editor auf der Registerkarte **Objekte** die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld **Neue Anlage hinzufügen** wird geöffnet.  
  
6.  Wählen Sie in der Liste **Typ** den Eintrag **Microsoft.VisualStudio.MefComponent** aus.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `MefComponent`\-Element in der Datei "extension.vsixmanifest".  Von diesem Element wird der Name einer Erweiterungsassembly im VSIX\-Paket angegeben.  Weitere Informationen finden Sie unter [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/de-de/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Wählen Sie in der Liste **Quelle** die Option **Ein Projekt in der aktuellen Projektmappe** aus.  
  
8.  Wählen Sie in der Liste **Projekt** die Option **BdcProjectItemExtension** und dann die Schaltfläche **OK** aus.  
  
9. Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
10. Stellen Sie sicher, dass das Projekt fehlerfrei kompiliert und erstellt wird.  
  
11. Überprüfen Sie, ob im Buildausgabeordner des Projekts "GenerateExternalDataLists" jetzt die Datei "GenerateExternalDataLists.vsix" vorhanden ist.  
  
     Standardmäßig handelt es sich beim Buildausgabeordner um den Ordner "...\\bin\\Debug" in dem Ordner mit der Projektdatei.  
  
## Testen der Projektelementerweiterung  
 Jetzt können Sie die Projektelementerweiterung testen.  Debuggen Sie das Erweiterungsprojekt zunächst in der experimentellen Instanz von Visual Studio.  Verwenden Sie die Erweiterung dann in der experimentellen Instanz von Visual Studio, um eine externe Liste für ein BDC\-Modell zu generieren.  Öffnen Sie abschließend die externe Liste auf der SharePoint\-Website, um sicherzustellen, dass die Liste einwandfrei funktioniert.  
  
#### So debuggen Sie die Erweiterung  
  
1.  Starten Sie ggf. Visual Studio mit Administratoranmeldeinformationen neu, und öffnen Sie dann die Projektmappe "GenerateExternalDataLists".  
  
2.  Öffnen Sie im Projekt "BdcProjectItemExtension" die Codedatei "ProjectItemExtension", und fügen Sie dann der Codezeile in der `Initialize`\-Methode einen Haltepunkt hinzu.  
  
3.  Öffnen Sie die Codedatei "GenerateExternalDataLists", und fügen Sie dann der ersten Codezeile in der `GenerateExternalDataLists_Execute`\-Methode einen Haltepunkt hinzu.  
  
4.  Drücken Sie die F5\-Taste, oder wählen Sie in der Menüleiste **Debuggen** und **Debugging starten** aus, um das Debuggen zu starten.  
  
     Die Erweiterung wird unter "%UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\External Data List Generator\\1.0" installiert, und eine experimentelle Instanz von Visual Studio wird gestartet.  Sie testen das Projektelement in dieser Instanz von Visual Studio.  
  
#### So testen Sie die Erweiterung  
  
1.  Wählen Sie in der experimentellen Visual Studio\-Instanz in der Menüleiste **Datei**, **Neu** und **Projekt** aus.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt** die Knoten **Vorlagen**, **Visual C\#** sowie **SharePoint**, und wählen Sie dann **2010** aus.  
  
3.  Stellen Sie in der Liste am oberen Rand des Dialogfelds sicher, dass **.NET Framework 3.5** ausgewählt ist.  Projekte für [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] erfordern diese Version von .NET Framework.  
  
4.  Wählen Sie in der Liste der Projektvorlagen **SharePoint 2010\-Projekt** aus.  
  
5.  Geben Sie im Feld **Name** die Zeichenfolge **SharePointProjectTestBDC** ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
6.  Geben Sie im Assistent zum Anpassen von SharePoint die URL der Website ein, die Sie zum Debuggen verwenden möchten, und wählen Sie **Als Farmlösung bereitstellen** sowie anschließend die Schaltfläche **Fertig stellen** aus.  
  
7.  Öffnen Sie das Kontextmenü des Projekts "SharePointProjectTestBDC", und wählen Sie **Hinzufügen** sowie anschließend **Neues Element** aus.  
  
8.  Erweitern Sie im Dialogfeld **Neues Element hinzufügen – SharePointProjectTestBDC** den installierten Sprachknoten und den Knoten **SharePoint**.  
  
9. Wählen Sie den Knoten **2010** und dann die Vorlage **Business Data Connectivity\-Modell \(nur Farmlösung\)** aus.  
  
10. Geben Sie im Feld **Name** die Zeichenfolge **TestBDCModel** ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
11. Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie in der `Initialize`\-Methode der Codedatei "ProjectItemExtension" festgelegt haben.  
  
12. Drücken Sie in der angehaltenen Visual Studio\-Instanz die **F5**\-Taste, oder wählen Sie in der Menüleiste **Debuggen** und **Weiter** aus, um das Debuggen des Projekts fortzusetzen.  
  
13. Drücken Sie in der experimentellen Visual Studio\-Instanz die **F5**\-Taste, oder wählen Sie in der Menüleiste **Debuggen** und **Debugging starten** aus, um das Projekt **TestBDCModel** zu erstellen, bereitzustellen und auszuführen.  
  
     Im Webbrowser wird die Standardseite der für das Debugging angegebenen SharePoint\-Website geöffnet.  
  
14. Überprüfen Sie, dass im Abschnitt **Listen** des Schnellstartbereichs noch keine auf dem BDC\-Standardmodell des Projekts basierende Liste vorhanden ist.  Sie müssen zuerst eine externe Datenliste erstellen, entweder mit der SharePoint\-Benutzeroberfläche oder mit der Projektelementerweiterung.  
  
15. Schließen Sie den Webbrowser.  
  
16. Öffnen Sie in der Visual Studio\-Instanz mit dem geöffneten Projekt "TestBDCModel" im **Projektmappen\-Explorer** das Kontextmenü des Knotens **TestBDCModel**, und wählen Sie dann **GenerateExternalDataLists** aus.  
  
17. Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie in der `GenerateExternalDataLists_Execute`\-Methode festgelegt haben.  Drücken Sie die **F5**\-Taste, oder wählen Sie in der Menüleiste **Debuggen** und **Fortsetzen** aus, um das Debuggen des Projekts fortzusetzen.  
  
18. Von der experimentellen Visual Studio\-Instanz wird dem Projekt "TestBDCModel" eine Listeninstanz mit dem Namen **Entity1DataList** hinzugefügt und außerdem eine Funktion mit dem Namen **Feature2** für die Listeninstanz generiert.  
  
19. Drücken Sie die **F5**\-Taste, oder wählen Sie in der Menüleiste **Debuggen** und **Debugging starten** aus, um das Projekt "TestBDCModel" zu erstellen, bereitzustellen und auszuführen.  
  
     Im Webbrowser wird die Standardseite der SharePoint\-Website geöffnet, die zum Debugging verwendet wird.  
  
20. Wählen Sie im Abschnitt **Listen** des Schnellstartbereichs die Liste **Entity1DataList** aus.  
  
21. Überprüfen Sie, ob die Liste neben den Spalten "Identifier1" und "Message" ebenfalls ein Element mit dem Wert "0" für "Identifier1" und dem Wert "Hello World" für "Message" enthält.  
  
     Das BDC\-Standardmodell zum Bereitstellen all dieser Daten wird von der Projektvorlage **Business Data Connectivity\-Modell** generiert.  
  
22. Schließen Sie den Webbrowser.  
  
## Bereinigen des Entwicklungscomputers  
 Nachdem Sie die Tests der Projektelementerweiterung abgeschlossen haben, entfernen Sie die externe Liste und das BDC\-Modell von der SharePoint\-Website, und entfernen Sie die Projektelementerweiterung aus Visual Studio.  
  
#### So entfernen Sie die externe Datenliste von der SharePoint\-Website  
  
1.  Wählen Sie im Schnellstartbereich der SharePoint\-Website die Liste **Entity1DataList** aus.  
  
2.  Wählen Sie auf der SharePoint\-Website im Menüband die Registerkarte **Liste** aus.  
  
3.  Wählen Sie auf der Registerkarte **Liste** in der Gruppe **Einstellungen** die Option **Listeneinstellungen** aus.  
  
4.  Wählen Sie unter **Berechtigungen und Verwaltung** die Option **Diese Liste löschen** und dann **OK** aus, um zu bestätigen, dass die Liste in den Papierkorb verschoben werden soll.  
  
5.  Schließen Sie den Webbrowser.  
  
#### So entfernen Sie das BDC\-Modell von der SharePoint\-Website  
  
1.  Wählen Sie in der experimentellen Visual Studio\-Instanz in der Menüleiste **Erstellen** und **Zurückziehen** aus.  
  
     Das BDC\-Modell wird aus der SharePoint\-Website entfernt.  
  
#### So entfernen Sie die Projektelementerweiterung aus Visual Studio  
  
1.  Wählen Sie in der experimentellen Visual Studio\-Instanz in der Menüleiste **Erstellen** und **Erweiterungen und Update** aus.  
  
     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.  
  
2.  Wählen Sie in der Liste der Erweiterungen **External Data List Generator** und anschließend die Schaltfläche **Deinstallieren** aus.  
  
3.  Wählen Sie im angezeigten Dialogfeld **Ja** aus, um zu bestätigen, dass die Erweiterung deinstalliert werden soll.  
  
4.  Wählen Sie **Jetzt neu starten** aus, um die Deinstallation abzuschließen.  
  
5.  Schließen Sie beide Visual Studio\-Instanzen \(sowohl die experimentelle als auch die Instanz mit der geöffneten Projektmappe "GenerateExternalDataLists"\).  
  
## Siehe auch  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  