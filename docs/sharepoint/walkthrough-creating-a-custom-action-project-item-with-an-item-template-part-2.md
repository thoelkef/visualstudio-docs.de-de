---
title: 'Exemplarische Vorgehensweise: Erstellen eines Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 2 | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 264decc53d8ba2d818562a9513ecfa2aab6f882c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2"></a>Exemplarische Vorgehensweise: Erstellen eines Projektelements "Benutzerdefinierte Aktion" mit einer Elementvorlage, Teil 2
  Nachdem Sie einen benutzerdefinierten Typ des SharePoint-Projektelements definiert und ordnen es mit einer Elementvorlage in Visual Studio, möchten Sie möglicherweise auch einen Assistenten für die Vorlage bereitzustellen. Sie können den Assistenten verwenden, Informationen von Benutzern sammeln, wenn sie Ihre Vorlage verwenden, um eine neue Instanz des Projektelements zu einem Projekt hinzuzufügen. Mit den gesammelten Informationen kann das Projektelement initialisiert werden.  
  
 In dieser exemplarischen Vorgehensweise fügen Sie einen Assistenten, in der die benutzerdefinierte Aktion-Projektelement, die in gezeigt [Exemplarische Vorgehensweise: Erstellen einer Custom Action Project Item mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Wenn ein Benutzer einem SharePoint-Projekt ein Projektelement für die benutzerdefinierte Aktion hinzufügt, wird der Assistent sammelt Informationen zu der benutzerdefinierten Aktion (z. B. den Speicherort und die URL, zu der navigiert werden soll, wenn ein Endbenutzer er wählt) und fügt diese Informationen in der Datei "Elements.xml" in der neuen Projektelement.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einen Assistenten für einen benutzerdefinierten SharePoint-Projektelementtyp, dem eine Elementvorlage zugeordnet ist.  
  
-   Definieren eine benutzerdefinierte Assistenten-Benutzeroberfläche, die die integrierten Assistenten für SharePoint-Projektelemente in Visual Studio ähnelt.  
  
-   Initialisieren von SharePoint-Projektdateien mit im Assistenten gesammelten Daten mithilfe von ersetzbaren Parametern  
  
-   Debuggen und Testen des Assistenten  
  
> [!NOTE]  
>  Sie können eine Stichprobe, die die abgeschlossene Projekte, Code und andere Dateien in dieser exemplarischen Vorgehensweise von folgendem Speicherort herunterladen: [Projektdateien für Erweiterbarkeit Exemplarische Vorgehensweisen zu SharePoint-Tools](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um diese exemplarische Vorgehensweise durchführen zu können, müssen Sie zuerst die Projektmappe CustomActionProjectItem abschließen, indem erstellen [Exemplarische Vorgehensweise: Erstellen einer Custom Action Project Item mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer außerdem die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von Windows, SharePoint und Visual Studio. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Das Visual Studio SDK. Diese exemplarische Vorgehensweise verwendet die **VSIX-Projekt** Vorlage im SDK, um ein VSIX-Paket zum Bereitstellen des Projektelements zu erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Assistenten für Projekt- und Elementvorlagen in Visual Studio. Weitere Informationen finden Sie unter [wie: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md) und <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstelle.  
  
-   Benutzerdefinierte Aktionen in SharePoint. Weitere Informationen finden Sie unter [benutzerdefinierte Aktion](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
## <a name="creating-the-wizard-project"></a>Das Assistentenprojekt erstellen  
 Zum Durchführen dieser exemplarischen Vorgehensweise müssen Sie ein Projekt hinzufügen, um die Projektmappe CustomActionProjectItem, die Sie in erstellt [Exemplarische Vorgehensweise: Erstellen einer Custom Action Project Item mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). In diesem Projekt implementieren Sie die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>-Schnittstelle, und Sie definieren die Assistenten-Benutzeroberfläche.  
  
#### <a name="to-create-the-wizard-project"></a>So erstellen die Assistenten-Projekt  
  
1.  Öffnen Sie in Visual Studio die Projektmappe CustomActionProjectItem  
  
2.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen Sie **hinzufügen**, und wählen Sie dann **neues Projekt**.  
  
3.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann die **Windows** Knoten.  
  
4.  Am oberen Rand der **neues Projekt** Dialogfeld Feld, stellen Sie sicher, dass **.NET Framework 4.5** ist in der Liste der Versionen von .NET Framework ausgewählt wurde.  
  
5.  Wählen Sie die **WPF-Benutzersteuerelementbibliothek** -Projektvorlage aus, nennen Sie das Projekt **ItemTemplateWizard**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **ItemTemplateWizard** Projekt der Projektmappe.  
  
6.  Löschen Sie das Element "UserControl1" aus dem Projekt ein.  
  
## <a name="configuring-the-wizard-project"></a>Konfigurieren die Assistenten-Projekt  
 Bevor Sie den Assistenten zum Erstellen, müssen Sie ein Windows Presentation Foundation (WPF)-Fenster, eine Codedatei und Assemblyverweise zum Projekt hinzufügen.  
  
#### <a name="to-configure-the-wizard-project"></a>So konfigurieren Sie ein Assistentenprojekt  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü von der **ItemTemplateWizard** Projektknoten, und wählen Sie dann **Eigenschaften**.  
  
2.  In der **Projekt-Designer**, stellen Sie sicher, dass das Zielframework auf .NET Framework 4.5 festgelegt ist.  
  
     Für Visual C#-Projekten können Sie diesen Wert festlegen, auf die **Anwendung** Registerkarte. Für Visual Basic-Projekten können Sie diesen Wert festlegen, auf die **Kompilieren** Registerkarte. Weitere Informationen finden Sie unter [Vorgehensweise: .NET Framework-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
3.  In der **ItemTemplateWizard** Projekt, fügen Sie eine **Fenster (WPF)** Element zum Projekt, und nennen Sie das Element **WizardWindow**.  
  
4.  Fügen Sie zwei Codedateien mit den Namen CustomActionWizard und Zeichenfolgen hinzu.  
  
5.  Öffnen Sie das Kontextmenü für die **ItemTemplateWizard** Projekt, und wählen Sie dann **Verweis hinzufügen**.  
  
6.  In der **Verweis-Manager - ItemTemplateWizard** Dialogfeld unter die **Assemblys** Knoten, wählen Sie die **Erweiterungen** Knoten.  
  
7.  Wählen Sie die Kontrollkästchen neben den folgenden Assemblys, und wählen Sie dann die **OK** Schaltfläche:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  In **Projektmappen-Explorer**in der **Verweise** Ordner für das Projekt ItemTemplateWizard wählen Sie die **EnvDTE** Verweis.  
  
9. In der **Eigenschaften** Fenster, ändern Sie den Wert von der **Interop-Typen einbetten** Eigenschaft **"false"**.  
  
## <a name="defining-the-default-location-and-id-strings-for-custom-actions"></a>Definieren den Standardspeicherort und ID-Zeichenfolgen für benutzerdefinierte Aktionen  
 Jede benutzerdefinierte Aktion verfügt über einen Speicherort und die ID, die im angegebenen der `GroupID` und `Location` Attribute der `CustomAction` Element in der Datei "Elements.xml". In diesem Schritt definieren Sie einige der für diese Attribute im Projekt ItemTemplateWizard gültigen Zeichenfolgen. Beim Durchführen dieser exemplarischen Vorgehensweise werden diese Zeichenfolgen in die Datei "Elements.xml" im Projektelement benutzerdefinierte Aktion geschrieben, wenn Benutzer einen Speicherort und eine ID im Assistenten angeben.  
  
 Der Einfachheit halber unterstützt dieses Beispiel nur eine Teilmenge der verfügbaren Standardspeicherorte und IDs. Eine vollständige Liste finden Sie unter [Standardspeicherorte für benutzerdefinierte-Aktion und IDs](http://go.microsoft.com/fwlink/?LinkId=181964).  
  
#### <a name="to-define-the-default-location-and-id-strings"></a>Zum Definieren der Standardspeicherort und ID-Zeichenfolgen  
  
1.  Öffnen.  
  
2.  In der **ItemTemplateWizard** Projekt, ersetzen Sie den Code in der Codedatei Zeichenfolgen durch den folgenden Code.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]  
  
## <a name="creating-the-wizard-ui"></a>Erstellen der Assistenten-Benutzeroberfläche  
 XAML-Code, um die Definition der Benutzeroberfläche des Assistenten hinzu, und fügen Sie Code zum einige Steuerelemente im Assistenten auf die ID-Zeichenfolgen zu binden. Der erstellte Assistent ähnelt dem integrierten Assistenten für SharePoint-Projekte in Visual Studio.  
  
#### <a name="to-create-the-wizard-ui"></a>So erstellen die Assistenten-Benutzeroberfläche  
  
1.  In der **ItemTemplateWizard** Projekt, öffnen Sie das Kontextmenü für die **WizardWindow.xaml** , und wählen Sie dann **öffnen** um das Fenster im Designer zu öffnen.  
  
2.  Ersetzen Sie in der XAML-Ansicht das aktuelle durch folgendes XAML. Der XAML-Code definiert eine Benutzeroberfläche, die eine Überschrift enthält, die zum Angeben des Verhaltens der benutzerdefinierten Aktion und die Navigationsschaltflächen am unteren Rand des Fensters steuert.  
  
    > [!NOTE]  
    >  Nachdem Sie diesen Code hinzufügen, müssen das Projekt einige Kompilierungsfehler. Diese Fehler werden durch Code behoben, den Sie in späteren Schritten hinzufügen.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  Das Fenster, das dieser XAML erstellte ist stammt aus dem <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> Basisklasse. Wenn Sie Visual Studio ein benutzerdefiniertes WPF-Dialogfeld hinzufügen, wird empfohlen, dass Sie das Dialogfeld von dieser Klasse, um ein einheitliches Aussehen mit anderen Dialogfeldern in Visual Studio und Probleme zu vermeiden, die andernfalls sollten Sie modale Dialogfelder auftreten abzuleiten. Weitere Informationen finden Sie unter [erstellen und Verwalten von modalen Dialogfeldern](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Wenn Sie ein Visual Basic-Projekt entwickeln, entfernen Sie die `ItemTemplateWizard` Namespace aus der `WizardWindow` Klassennamen in der `x:Class` Attribut des der `Window` Element. Dieses Element befindet sich in der ersten XAML-Zeile. Wenn Sie fertig sind, sollte die erste Zeile den folgenden Code ähneln:  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Ersetzen Sie in der CodeBehind-Datei für die Datei "WizardWindow.xaml" den aktuellen Code durch den folgenden Code ein.  
  
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]  
  
## <a name="implementing-the-wizard"></a>Implementieren des Assistenten  
 Definieren Sie die Funktionalität des Assistenten durch das Implementieren der <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstelle.  
  
#### <a name="to-implement-the-wizard"></a>So implementieren Sie den Assistenten  
  
1.  In der **ItemTemplateWizard** -Projekt, öffnen die **CustomActionWizard** Codedatei, und klicken Sie dann den aktuellen Code in dieser Datei durch den folgenden Code ersetzen:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte für den Assistenten benötigte Code in das Projekt eingefügt. Erstellen Sie das Projekt, um sicherzustellen, dass es ohne Fehler kompiliert wird.  
  
#### <a name="to-build-your-project"></a>So erstellen Sie das Projekt  
  
1.  Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
## <a name="associating-the-wizard-with-the-item-template"></a>Die Elementvorlage Zuordnen des Assistenten  
 Nun, dass Sie den Assistenten implementiert haben, müssen Sie diese mit Zuordnen der **benutzerdefinierte Aktion** Elementvorlage nach Abschluss von drei Hauptschritte:  
  
1.  Signieren der Assistenten-Assembly mit einem starkem Namen  
  
2.  Abrufen des öffentlichen Schlüsseltokens der Assistenten-Assembly  
  
3.  Fügen Sie einen Verweis auf die Assistenten-Assembly in der VSTEMPLATE-Datei für die **benutzerdefinierte Aktion** Elementvorlage.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>So signieren Sie die Assistenten-Assembly mit einem starkem Namen  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü von der **ItemTemplateWizard** Projektknoten, und wählen Sie dann **Eigenschaften**.  
  
2.  Auf der **Signierung** Registerkarte die **zum Signieren der Assembly** Kontrollkästchen.  
  
3.  In der **Schlüsseldatei mit starkem Namen auswählen** wählen  **\<neu... >**.  
  
4.  In der **Schlüssel für einen starken Namen erstellen** Dialogfeld Geben Sie einen Namen, Deaktivieren der **Schlüsseldatei mit Kennwort schützen** Kontrollkästchen, und wählen Sie dann die **OK** Schaltfläche.  
  
5.  Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>So rufen Sie das öffentliche Schlüsseltoken der Assistenten-Assembly ab  
  
1.  Führen Sie in einem Fenster Visual Studio-Eingabeaufforderung den folgenden Befehl, und Ersetzen Sie dabei *PathToWizardAssembly* durch den vollständigen Pfad zu der Assembly ItemTemplateWizard.dll für das Projekt ItemTemplateWizard auf die Entwicklung Computer.  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Das Token des öffentliche Schlüssels für die Assembly ItemTemplateWizard.dll wird in der Visual Studio-Eingabeaufforderungsfenster geschrieben.  
  
2.  Lassen Sie das Fenster der Visual Studio-Eingabeaufforderung geöffnet. Sie benötigen das öffentliche Schlüsseltoken für das nächste Verfahren.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>So fügen Sie einen Verweis auf die Assistenten-Assembly in der VSTEMPLATE-Datei hinzu  
  
1.  In **Projektmappen-Explorer**, erweitern Sie die **ItemTemplate** Projektknoten, und öffnen Sie dann die Datei ItemTemplate.vstemplate.  
  
2.  Fügen Sie das folgende `WizardExtension`-Element zwischen dem `</TemplateContent>`-Tag und dem `</VSTemplate>`-Tag am Ende der Datei hinzu. Ersetzen Sie die *YourToken* Wert, der die `PublicKeyToken` Attribut mit dem Token des öffentlichen Schlüssels, die Sie im vorherigen Verfahren abgerufen haben.  
  
    ```  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Weitere Informationen zu den `WizardExtension` Element finden Sie unter [WizardExtension-Element &#40;Visual Studio-Vorlagen&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Speichern und schließen Sie die Datei.  
  
## <a name="adding-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Hinzufügen von ersetzbaren Parametern zur Datei "Elements.xml" in der Elementvorlage  
 Fügen Sie der Datei "Elements.xml" im Projekt ItemTemplate mehrere ersetzbare Parameter hinzu. Diese Parameter werden in der `PopulateReplacementDictionary`-Methode in der zuvor definierten `CustomActionWizard`-Klasse initialisiert. Wenn ein Benutzer zu einem Projekt ein Projektelement für die benutzerdefinierte Aktion hinzufügt, ersetzt Visual Studio diese Parameter in der Datei Elements.xml im neuen Projektelement automatisch mit den Werten, die sie im Assistenten angegeben.  
  
 Ein ersetzbarer Parameter ist ein Token, das mit einem Dollarzeichen ($) beginnt und endet. Zusätzlich zum Definieren Ihrer eigenen ersetzbare Parameter, können Sie integrierte Parameter verwenden, die SharePoint-Projektsystem definiert und initialisiert. Weitere Informationen finden Sie unter [ersetzbare Parameter](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>So fügen Sie der Datei Elements.xml ersetzbare Parameter hinzu  
  
1.  Ersetzen Sie den Inhalt der Datei "Elements.xml" im Projekt ItemTemplate durch folgendes XML.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Die folgenden XML-Code ändert die Werte der `Id`, `GroupId`, `Location`, `Description`, und `Url` -Attribute verwenden, um ersetzbare Parameter.  
  
2.  Speichern und schließen Sie die Datei.  
  
## <a name="adding-the-wizard-to-the-vsix-package"></a>Hinzufügen des Assistenten zum VSIX-Paket  
 Fügen Sie in der Datei source.extension.vsixmanifest im VSIX-Projekt einen Verweis auf das Assistentenprojekt, sodass er mit dem VSIX-Paket bereitgestellt wird, das das Projektelement enthält.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>So fügen Sie den Assistenten dem VSIX-Paket hinzu  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü von der **"Source.Extension.vsixmanifest"** im CustomActionProjectItem-Projekt, und wählen Sie dann **öffnen** öffnen die Datei im manifest-Editor.  
  
2.  Wählen Sie im manifest-Editor die **Bestand** Registerkarte aus, und wählen Sie dann die **neu** Schaltfläche.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.  
  
3.  In der **Typ** wählen **Microsoft.VisualStudio.Assembly**.  
  
4.  In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.  
  
5.  In der **Projekt** wählen **ItemTemplateWizard**, und wählen Sie dann die **OK** Schaltfläche.  
  
6.  Wählen Sie in der Menüleiste **erstellen**, **Projektmappe**, und stellen Sie sicher, dass die Lösung ohne Fehler kompiliert wird.  
  
## <a name="testing-the-wizard"></a>Testen des Assistenten  
 Sie können den Assistenten jetzt testen. Starten Sie die Projektmappe "CustomActionProjectItem" in der experimentellen Instanz von Visual Studio debuggen. Anschließend testen Sie den Assistenten für die benutzerdefinierte Aktion für das Projektelement in einer SharePoint-Projekt in der experimentellen Instanz von Visual Studio. Erstellen und führen Sie zum Schluss das SharePoint-Projekt aus, um sicherzustellen, dass die benutzerdefinierte Aktion ordnungsgemäß funktioniert.  
  
#### <a name="to-start-to-debug-the-solution"></a>Starten Sie die Lösung zu debuggen  
  
1.  Starten Sie Visual Studio erneut mit Administratoranmeldeinformationen, und öffnen Sie dann die Projektmappe "CustomActionProjectItem".  
  
2.  Klicken Sie im Projekt ItemTemplateWizard CustomActionWizard-Codedatei öffnen, und fügen Sie einen Haltepunkt an der ersten Codezeile in der `RunStarted` Methode.  
  
3.  Wählen Sie in der Menüleiste **Debuggen**, **Ausnahmen**.  
  
4.  In der **Ausnahmen** Dialogfeld Feld, stellen Sie sicher, dass die **ausgelöst** und **vom Benutzercode unbehandelt** Kontrollkästchen für **Common Language Runtime-Ausnahmen**deaktiviert sind, und wählen Sie dann die **OK** Schaltfläche.  
  
5.  Starten Sie durch Auswählen der F5-Taste, oder wählen Sie in der Menüleiste, Auswahl **Debuggen**, **Debuggen**.  
  
     Visual Studio die Erweiterung %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Aktion Projekt Item\1.0 und eine experimentelle Instanz von Visual Studio wird gestartet. Sie testen das Projektelement in dieser Instanz von Visual Studio.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>So testen Sie den Assistenten in Visual Studio  
  
1.  Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **Datei**, **neu**, **Projekt**.  
  
2.  Erweitern Sie die **Visual C#-** oder **Visual Basic** -Knoten (je nach von der die Elementvorlage unterstützten Sprache), erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
3.  Wählen Sie in der Liste der Projektvorlagen **SharePoint 2010-Projekt**, nennen Sie das Projekt **Zeichenfolge CustomActionWizardTest**, und wählen Sie dann die **OK** Schaltfläche.  
  
4.  In der **Assistent zum Anpassen von SharePoint**, geben Sie die URL der Site, die Sie zum Debuggen verwenden möchten, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
5.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektknoten, wählen Sie **hinzufügen**, und wählen Sie dann **neues Element**.  
  
6.  In der **neues Element hinzufügen - CustomItemWizardTest** Dialogfeld erweitern Sie die **SharePoint** Knoten, und erweitern Sie dann die **2010** Knoten.  
  
7.  Wählen Sie in der Liste der Projektelemente, die **benutzerdefinierte Aktion** -Element aus, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
8.  Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `RunStarted`-Methode festgelegt haben.  
  
9. Fahren Sie mit dem Debuggen des Projekts durch Auswählen der F5-Taste, oder wählen Sie in der Menüleiste **Debuggen**, **Fortfahren**.  
  
     Der Assistent zum Anpassen von SharePoint wird angezeigt.  
  
10. Klicken Sie unter **Speicherort**, wählen Sie die **Liste bearbeiten** Optionsfeld.  
  
11. In der **Gruppenbezeichner** wählen **Kommunikation**.  
  
12. In der **Titel** geben **SharePoint Developer Center**.  
  
13. In der **Beschreibung** geben **SharePoint Developer Center-Website geöffnet**.  
  
14. In der **URL** geben **http://msdn.microsoft.com/sharepoint/default.aspx**, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
     Isual Studio fügt ein Element mit dem Namen **CustomAction1** zum Projekt und öffnet die Datei "Elements.xml"-Datei im Editor. Vergewissern Sie sich, dass Elements.xml die Werte enthält, die Sie im Assistenten angegeben haben.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>So testen Sie die benutzerdefinierte Aktion in SharePoint  
  
1.  In der experimentellen Instanz von Visual Studio, wählen Sie die F5-Taste, oder wählen Sie auf der Menüleiste **Debuggen**, **Debuggen**.  
  
     Die benutzerdefinierte Aktion wird verpackt und bereitgestellt werden, auf die SharePoint-Website, die gemäß der **Website-URL** Eigenschaft des Projekts, und der Webbrowser wird die Standardseite dieser Website geöffnet.  
  
    > [!NOTE]  
    >  Wenn die **Skriptdebugging deaktiviert** im Dialogfeld angezeigt wird, wählen Sie die **Ja** Schaltfläche.  
  
2.  Wählen Sie in den Bereich der SharePoint-Website, die **Aufgaben** Link.  
  
     Die **Aufgaben – alle Aufgaben** Seite wird angezeigt.  
  
3.  Auf der **Listentools** Registerkarte des Menübands, wählen Sie die **Liste** Registerkarte, und dann auf die **Einstellungen** Gruppe **Listeneinstellungen**.  
  
     Die **Listeneinstellungen** Seite wird angezeigt.  
  
4.  Unter den **Kommunikation** Überschrift am oberen Rand der Seite ", wählen Sie die **SharePoint Developer Center** verknüpfen möchten, stellen Sie sicher, dass der Browser die Website geöffnet http://msdn.microsoft.com/sharepoint/default.aspx, und schließen Sie den Browser.  
  
## <a name="cleaning-up-the-development-computer"></a>Bereinigen des Entwicklungscomputers  
 Nachdem Sie die Tests des Projektelements abgeschlossen haben, entfernen Sie die Projektelementvorlage aus der experimentellen Instanz von Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>So bereinigen Sie den Entwicklungscomputer  
  
1.  Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **Tools**, **Erweiterungen und Updates**.  
  
     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.  
  
2.  Wählen Sie in der Liste der Erweiterungen, die **Custom Action Project Item** Erweiterung, und wählen Sie dann die **Deinstallieren** Schaltfläche.  
  
3.  Wählen Sie im angezeigten Dialogfeld die **Ja** , um zu bestätigen, dass Sie verwenden möchten, deinstallieren Sie die Erweiterung aus, und wählen Sie dann die **jetzt neu starten** Schaltfläche, um die Deinstallation abzuschließen.  
  
4.  Schließen Sie beide Instanzen von Visual Studio (die experimentelle Instanz und die Instanz von Visual Studio in der Projektmappe CustomActionProjectItem geöffnet ist).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements für die benutzerdefinierte Aktion mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Schemareferenz zu Visual Studio-Vorlagen](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Vorgehensweise: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)   
 [Standardspeicherorte für die benutzerdefinierte Aktion und IDs](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  