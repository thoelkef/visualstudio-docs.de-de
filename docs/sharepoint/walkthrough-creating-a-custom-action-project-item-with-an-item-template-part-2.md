---
title: 'Exemplarische Vorgehensweise: Erstellen eine benutzerdefinierte Aktion das Projektelement, mit einer Elementvorlage, Teil 2 | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a04171e79843de8948818e75279136478f20929c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630885"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Exemplarische Vorgehensweise: Erstellen eines Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 2
  Nachdem Sie einen benutzerdefinierten Typ von SharePoint-Projektelements definiert und sie eine Elementvorlage in Visual Studio ordnen, möchten Sie auch einen Assistenten für die Vorlage bereitzustellen. Sie können den Assistenten verwenden, zum Sammeln von Informationen von Benutzern, wenn sie Ihre Vorlage verwenden, um eine neue Instanz des Projektelements zu einem Projekt hinzuzufügen. Mit den gesammelten Informationen kann das Projektelement initialisiert werden.

 In dieser exemplarischen Vorgehensweise fügen Sie einen Assistenten, die benutzerdefinierte Aktion-Projektelement, das gezeigt wird [Exemplarische Vorgehensweise: Erstellen ein Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Wenn ein Benutzer einem SharePoint-Projekt ein Projektelement für die benutzerdefinierte Aktion hinzufügt, wird der Assistent sammelt Informationen zu der benutzerdefinierten Aktion (z. B. den Speicherort und die URL, zu der navigiert werden soll, wenn ein Endbenutzer wählt) und fügt diese Informationen, um die *"Elements.xml"* -Datei in das neue Projektelement.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

-   Erstellen einen Assistenten für einen benutzerdefinierten SharePoint-Projektelementtyp, dem eine Elementvorlage zugeordnet ist.

-   Definieren ein benutzerdefiniertes Assistenten-Benutzeroberfläche, die von den integrierten Assistenten für SharePoint-Projektelemente in Visual Studio ähnelt.

-   Initialisieren von SharePoint-Projektdateien mit im Assistenten gesammelten Daten mithilfe von ersetzbaren Parametern

-   Debuggen und Testen des Assistenten

> [!NOTE]
>  Sie können ein Beispiel von [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) , die zeigt, wie benutzerdefinierte Aktivitäten für einen Workflow zu erstellen.

## <a name="prerequisites"></a>Vorraussetzungen
 Um diese exemplarische Vorgehensweise durchführen zu können, müssen Sie zunächst die Projektmappe "CustomActionProjectItem" erstellen, gehen Sie [Exemplarische Vorgehensweise: Erstellen ein Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer außerdem die folgenden Komponenten benötigt:

- Unterstützte Editionen von Windows, SharePoint und Visual Studio.

- Das Visual Studio SDK. Diese exemplarische Vorgehensweise verwendet die **VSIX-Projekt** Vorlage in das SDK zum Erstellen eines VSIX-Pakets zum Bereitstellen des Projektelements. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- Assistenten für Projekt- und Elementvorlagen in Visual Studio. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md) und <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstelle.

- Benutzerdefinierte Aktionen in SharePoint. Weitere Informationen finden Sie unter [benutzerdefinierte Aktion](http://go.microsoft.com/fwlink/?LinkId=177800).

## <a name="create-the-wizard-project"></a>Erstellen Sie die Assistenten-Projekt
 Um diese exemplarische Vorgehensweise abzuschließen, müssen Sie die Projektmappe "CustomActionProjectItem", die Sie in erstellt ein Projekt hinzufügen [Exemplarische Vorgehensweise: Erstellen ein Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). In diesem Projekt implementieren Sie die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>-Schnittstelle, und Sie definieren die Assistenten-Benutzeroberfläche.

#### <a name="to-create-the-wizard-project"></a>Die Assistenten-Projekt erstellen

1.  Öffnen Sie in Visual Studio die Projektmappe "CustomActionProjectItem"

2.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen **hinzufügen**, und wählen Sie dann **neues Projekt**.

3.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann die **Windows** Knoten.

4.  Am oberen Rand der **neues Projekt** Dialogfeld Feld, stellen Sie sicher, dass **.NET Framework 4.5** wird in der Liste der Versionen von .NET Framework ausgewählt.

5.  Wählen Sie die **WPF-Benutzersteuerelementbibliothek** -Projektvorlage aus, nennen Sie das Projekt **ItemTemplateWizard**, und wählen Sie dann die **OK** Schaltfläche.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **ItemTemplateWizard** Projekt der Projektmappe.

6.  Löschen Sie das Element "UserControl1" aus dem Projekt ein.

## <a name="configure-the-wizard-project"></a>Konfigurieren Sie die Assistenten-Projekt
 Bevor Sie den Assistenten zum Erstellen, müssen Sie ein Windows Presentation Foundation (WPF)-Fenster, eine Codedatei und das Projekt Assemblyverweise hinzufügen.

#### <a name="to-configure-the-wizard-project"></a>So konfigurieren Sie ein Assistentenprojekt

1.  In **Projektmappen-Explorer**, öffnen Sie im Kontextmenü über die **ItemTemplateWizard** Projektknoten, und wählen Sie dann **Eigenschaften**.

2.  In der **Projekt-Designer**, stellen Sie sicher, dass das Zielframework auf .NET Framework 4.5 festgelegt ist.

     Für Visual c#-Projekten können Sie diesen Wert festlegen, auf die **Anwendung** Registerkarte. Für Visual Basic-Projekten können Sie diesen Wert festlegen, auf die **Kompilieren** Registerkarte. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Projekten für eine bestimmte .NET Framework-Version](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

3.  In der **ItemTemplateWizard** fügen eine **Fenster (WPF)** Element dem Projekt aus, und nennen Sie das Element **WizardWindow**.

4.  Fügen Sie zwei Codedateien mit den Namen CustomActionWizard und Zeichenfolgen hinzu.

5.  Öffnen Sie das Kontextmenü für die **ItemTemplateWizard** Projekt, und wählen Sie dann **Verweis hinzufügen**.

6.  In der **Verweis-Manager - ItemTemplateWizard** Dialogfeld die **Assemblys** Knoten, wählen Sie die **Erweiterungen** Knoten.

7.  Wählen Sie die Kontrollkästchen neben den folgenden Assemblys aus, und wählen Sie dann die **OK** Schaltfläche:

    -   EnvDTE

    -   Microsoft.VisualStudio.Shell.11.0

    -   Microsoft.VisualStudio.TemplateWizardInterface

8.  In **Projektmappen-Explorer**in die **Verweise** ItemTemplateWizard Projektordner, wählen Sie die **EnvDTE** Verweis.

9. In der **Eigenschaften** Fenster ändern Sie den Wert von der **Embed Interop Types** Eigenschaft **"false"**.

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Definieren Sie den Standardspeicherort und ID-Zeichenfolgen für benutzerdefinierte Aktionen
 Jede benutzerdefinierte Aktion hat, einen Speicherort und die ID, die im angegebenen die `GroupID` und `Location` Attribute der `CustomAction` Element in der *"Elements.xml"* Datei. In diesem Schritt definieren Sie einige der für diese Attribute im Projekt ItemTemplateWizard gültigen Zeichenfolgen. Wenn Sie diese exemplarische Vorgehensweise abgeschlossen haben, werden diese Zeichenfolgen in geschrieben der *"Elements.xml"* -Datei in das Projektelement benutzerdefinierte Aktion, wenn Benutzer im Assistenten einen Speicherort und eine ID angeben.

 Der Einfachheit halber unterstützt in diesem Beispiel nur eine Teilmenge der verfügbaren Standardspeicherorte und IDs. Eine vollständige Liste finden Sie unter [Default Custom Action Locations und IDs](http://go.microsoft.com/fwlink/?LinkId=181964).

#### <a name="to-define-the-default-location-and-id-strings"></a>Zum Definieren der Standardspeicherort und ID-Zeichenfolgen

1.  Öffnen Sie.

2.  In der **ItemTemplateWizard** Projekt, ersetzen Sie den Code in der Zeichenfolgen-Codedatei durch folgenden Code.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]

## <a name="create-the-wizard-ui"></a>Erstellen der Benutzeroberfläche des Assistenten
 Hinzufügen von XAML zum Definieren der Benutzeroberflächenautomatisierungs des Assistenten, und fügen Sie Code, um einige der Steuerelemente im Assistenten auf die ID-Zeichenfolgen zu binden. Der erstellte Assistent ähnelt dem integrierten Assistenten für SharePoint-Projekte in Visual Studio.

#### <a name="to-create-the-wizard-ui"></a>Zum Erstellen der Benutzeroberfläche des Assistenten

1.  In der **ItemTemplateWizard** Projekt, öffnen Sie das Kontextmenü für die **WizardWindow.xaml** Datei, und wählen Sie dann **öffnen** um das Fenster im Designer zu öffnen.

2.  Ersetzen Sie in der XAML-Ansicht das aktuelle durch folgendes XAML. Die XAML definiert eine Benutzeroberfläche, die eine Überschrift enthält, die zum Angeben des Verhaltens der benutzerdefinierten Aktion und die Navigationsschaltflächen am unteren Rand des Fensters steuert.

    > [!NOTE]
    >  Nachdem Sie diesen Code hinzufügen, müssen Ihr Projekt einige Kompilierungsfehler. Diese Fehler werden durch Code behoben, den Sie in späteren Schritten hinzufügen.

     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]

    > [!NOTE]
    >  Das Fenster, das in diesem XAML erstellt wird ergibt sich aus der <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> Basisklasse. Wenn Sie ein benutzerdefiniertes WPF-Dialogfeld zu Visual Studio hinzufügen, wird empfohlen, dass Sie Ihrem Dialogfeld ableiten, von dieser Klasse ein einheitliches Aussehen mit anderen Dialogfeldern in Visual Studio und zur Vermeidung von Problemen, die andernfalls mit modalen Dialogfeldern auftreten können. Weitere Informationen finden Sie unter [erstellen und Verwalten von modalen Dialogfeldern](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).

3.  Wenn Sie ein Visual Basic-Projekt entwickeln, entfernen Sie die `ItemTemplateWizard` Namespace aus der `WizardWindow` Class-Name in der `x:Class` Attribut des der `Window` Element. Dieses Element befindet sich in der ersten XAML-Zeile. Wenn Sie fertig sind, sollte die erste Zeile den folgenden Code ähneln:

    ```xml
    <Window x:Class="WizardWindow"
    ```

4.  Ersetzen Sie in der CodeBehind-Datei für die Datei "WizardWindow.xaml" des aktuellen Codes durch den folgenden Code ein.

     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]

## <a name="implement-the-wizard"></a>Der Assistent zum Implementieren von
 Definieren Sie die Funktionen des Assistenten durch das Implementieren der <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstelle.

#### <a name="to-implement-the-wizard"></a>So implementieren Sie den Assistenten

1.  In der **ItemTemplateWizard** -Projekt, öffnen die **CustomActionWizard** Codedatei, und klicken Sie dann den aktuellen Code in dieser Datei durch den folgenden Code ersetzen:

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]

## <a name="checkpoint"></a>Checkpoint
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte für den Assistenten benötigte Code in das Projekt eingefügt. Erstellen Sie das Projekt, um sicherzustellen, dass es ohne Fehler kompiliert wird.

#### <a name="to-build-your-project"></a>So erstellen Sie das Projekt

1.  Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

## <a name="associate-the-wizard-with-the-item-template"></a>Ordnen Sie den Assistenten mit der Elementvorlage
 Nun, da Sie den Assistenten implementiert haben, müssen Sie ordnen sie die **benutzerdefinierte Aktion** Elementvorlage dazu drei Hauptschritte:

1.  Signieren der Assistenten-Assembly mit einem starkem Namen

2.  Abrufen des öffentlichen Schlüsseltokens der Assistenten-Assembly

3.  Fügen Sie einen Verweis auf die Assistenten-Assembly in der VSTEMPLATE-Datei für die **benutzerdefinierte Aktion** Elementvorlage.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>So signieren Sie die Assistenten-Assembly mit einem starkem Namen

1.  In **Projektmappen-Explorer**, öffnen Sie im Kontextmenü über die **ItemTemplateWizard** Projektknoten, und wählen Sie dann **Eigenschaften**.

2.  Auf der **Signierung** Registerkarte die **Assembly signieren** Kontrollkästchen.

3.  In der **Schlüsseldatei mit starkem Namen auswählen** wählen  **\<neu... >**.

4.  In der **Schlüssel für einen starken Namen erstellen** Dialogfeld Geben Sie einen Namen ein, deaktivieren die **Schlüsseldatei mit Kennwort schützen** aus, und wählen Sie dann die **OK** Schaltfläche.

5.  Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>So rufen Sie das öffentliche Schlüsseltoken der Assistenten-Assembly ab

1.  Führen Sie in einem Fenster Visual Studio-Eingabeaufforderung den folgenden Befehl, und Ersetzen Sie dabei *PathToWizardAssembly* durch den vollständigen Pfad zur erstellten Assembly ItemTemplateWizard.dll für das Projekt ItemTemplateWizard auf Ihrem Entwicklungs- Computer, auf.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     Das Token des öffentlichen Schlüssels für die *ItemTemplateWizard.dll* Assembly wird in der Visual Studio-Eingabeaufforderungsfenster geschrieben.

2.  Lassen Sie das Fenster der Visual Studio-Eingabeaufforderung geöffnet. Sie benötigen das öffentliche Schlüsseltoken, das nächste Verfahren abgeschlossen.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>So fügen Sie einen Verweis auf die Assistenten-Assembly in der VSTEMPLATE-Datei hinzu

1.  In **Projektmappen-Explorer**, erweitern Sie die **ItemTemplate** Projektknoten, und öffnen Sie dann die *ItemTemplate.vstemplate* Datei.

2.  Fügen Sie das folgende `WizardExtension`-Element zwischen dem `</TemplateContent>`-Tag und dem `</VSTemplate>`-Tag am Ende der Datei hinzu. Ersetzen Sie die *YourToken* Wert der `PublicKeyToken` Attribut mit dem Token des öffentlichen Schlüssels, den Sie in der vorherigen Prozedur abgerufen haben.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     Weitere Informationen zu den `WizardExtension` Element finden Sie unter [WizardExtension-Element &#40;Visual Studio-Vorlagen&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).

3.  Speichern und schließen Sie die Datei.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Hinzufügen von ersetzbaren Parametern, die *"Elements.xml"* Datei in der Elementvorlage
 Fügen Sie mehrere ersetzbare Parameter, die *"Elements.xml"* Datei im Projekt ItemTemplate-Element. Diese Parameter werden in der `PopulateReplacementDictionary`-Methode in der zuvor definierten `CustomActionWizard`-Klasse initialisiert. Wenn ein Benutzer ein Projektelement für die benutzerdefinierte Aktion zu einem Projekt hinzufügt, ersetzt Visual Studio automatisch diese Parameter werden in der *"Elements.xml"* -Datei in das neue Projektelement mit den Werten, die sie im Assistenten angegeben.

 Ein ersetzbarer Parameter ist ein Token, das mit einem Dollarzeichen ($) beginnt und endet. Zusätzlich zum Definieren Ihrer eigenen ersetzbare Parameter, können Sie integrierte Parameter, die SharePoint-Projektsystem definiert und initialisiert. Weitere Informationen finden Sie unter [ersetzbare Parameter](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Ersetzbare Parameter zum Hinzufügen der *"Elements.xml"* Datei

1.  Ersetzen Sie den Inhalt der im Projekt ItemTemplate die *"Elements.xml"* -Datei mit den folgenden XML-Code.

    ```xml
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

     Das neue XML-ändert die Werte der `Id`, `GroupId`, `Location`, `Description`, und `Url` Attribute ersetzbare Parameter.

2.  Speichern und schließen Sie die Datei.

## <a name="add-the-wizard-to-the-vsix-package"></a>Fügen Sie den Assistenten zum VSIX-Paket
 Fügen Sie in der Datei source.extension.vsixmanifest im VSIX-Projekt einen Verweis auf das Assistentenprojekt, sodass er mit dem VSIX-Paket bereitgestellt wird, die das Projektelement enthält.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>So fügen Sie den Assistenten dem VSIX-Paket hinzu

1.  In **Projektmappen-Explorer**, öffnen Sie im Kontextmenü aus der **"Source.Extension.vsixmanifest"** -Datei im Projekt "CustomActionProjectItem", und wählen Sie dann **öffnen** öffnen die Datei im manifest-Editor.

2.  Wählen Sie im manifest-Editor die **Assets** Registerkarte aus, und wählen Sie dann die **neu** Schaltfläche.

     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.

3.  In der **Typ** wählen **Microsoft.VisualStudio.Assembly**.

4.  In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.

5.  In der **Projekt** wählen **ItemTemplateWizard**, und wählen Sie dann die **OK** Schaltfläche.

6.  Wählen Sie auf der Menüleiste **erstellen** > **Projektmappe**, und klicken Sie dann stellen Sie sicher, dass die Projektmappe ohne Fehler kompiliert wird.

## <a name="test-the-wizard"></a>Testen Sie den Assistenten
 Sie können den Assistenten jetzt testen. Starten Sie zunächst die Projektmappe "CustomActionProjectItem" in der experimentellen Instanz von Visual Studio zu debuggen. Anschließend testen Sie den Assistenten für das Projektelement für die benutzerdefinierte Aktion in einer SharePoint-Projekt in der experimentellen Instanz von Visual Studio. Erstellen und führen Sie zum Schluss das SharePoint-Projekt aus, um sicherzustellen, dass die benutzerdefinierte Aktion ordnungsgemäß funktioniert.

#### <a name="to-start-to-debug-the-solution"></a>Starten Sie zum Debuggen der Projektmappe

1.  Starten Sie Visual Studio erneut mit Administratoranmeldeinformationen, und öffnen Sie dann die Projektmappe "CustomActionProjectItem".

2.  Öffnen Sie die Codedatei CustomActionWizard ItemTemplateWizard im Projekt und dann fügen Sie einen Haltepunkt auf der ersten Zeile des Codes in der `RunStarted` Methode.

3.  Wählen Sie auf der Menüleiste **Debuggen** > **Ausnahmen**.

4.  In der **Ausnahmen** Dialogfeld Feld, stellen Sie sicher, dass die **ausgelöst** und **vom Benutzercode unbehandelt** Kontrollkästchen für **Common Language Runtime-Ausnahmen**werden gelöscht, und wählen Sie dann die **OK** Schaltfläche.

5.  Starten Sie das Debuggen durch Auswählen der **F5** drücken, oder wählen Sie in der Menüleiste die Optionen **Debuggen** > **Debuggen starten**.

     Visual Studio installiert die Erweiterung in %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Aktion Projekt Item\1.0 und eine experimentelle Instanz von Visual Studio. Sie testen das Projektelement in dieser Instanz von Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>So testen Sie den Assistenten in Visual Studio

1.  Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste **Datei** > **neu** > **Projekt**.

2.  Erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten (je nach der die Elementvorlage unterstützten Sprache), erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.

3.  Wählen Sie in der Liste der Projektvorlagen das Projekt **SharePoint 2010-Projekt**, nennen Sie das Projekt **Zeichenfolge CustomActionWizardTest**, und wählen Sie dann die **OK** Schaltfläche.

4.  In der **SharePoint Customization Wizard**, geben Sie die URL der Website, die Sie für das Debuggen verwenden möchten, und wählen Sie dann die **Fertig stellen** Schaltfläche.

5.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektknoten, wählen **hinzufügen**, und wählen Sie dann **neues Element**.

6.  In der **neues Element hinzufügen - CustomItemWizardTest** Dialogfeld erweitern Sie die **SharePoint** Knoten, und erweitern Sie dann die **2010** Knoten.

7.  Wählen Sie in der Liste der Projektelemente, die **benutzerdefinierte Aktion** Element aus, und wählen Sie dann die **hinzufügen** Schaltfläche.

8.  Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `RunStarted`-Methode festgelegt haben.

9. Fahren Sie mit dem Debuggen des Projekts durch Auswahl der **F5** -Taste oder wählen Sie auf der Menüleiste die Optionen **Debuggen** > **Weiter**.

     SharePoint Customization Wizard angezeigt wird.

10. Klicken Sie unter **Speicherort**, wählen Sie die **Liste bearbeiten** Optionsfeld aus.

11. In der **Gruppen-ID** wählen **Kommunikation**.

12. In der **Titel** geben **SharePoint Developer Center**.

13. In der **Beschreibung** geben **die Entwicklercenter für SharePoint-Website geöffnet**.

14. In der **URL** geben **https://docs.microsoft.com/sharepoint/dev/**, und wählen Sie dann die **Fertig stellen** Schaltfläche.

     Visual Studio fügt ein Element mit dem Namen **CustomAction1** auf Ihr Projekt und öffnet die *"Elements.xml"* Datei im Editor. Überprüfen Sie, ob *"Elements.xml"* enthält die Werte, die Sie im Assistenten angegeben.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>So testen Sie die benutzerdefinierte Aktion in SharePoint

1.  Wählen Sie in der experimentellen Instanz von Visual Studio die **F5** Taste, oder wählen Sie auf der Menüleiste **Debuggen** > **Debuggen starten**.

     Die benutzerdefinierte Aktion wird verpackt und bereitgestellt werden, auf die SharePoint-Website, die gemäß der **Website-URL** Eigenschaft des Projekts, und der Webbrowser öffnet die Standardseite der Website.

    > [!NOTE]
    >  Wenn die **Skriptdebugging deaktiviert** wählen Sie im angezeigten Dialogfeld die **Ja** Schaltfläche.

2.  Wählen Sie im Bereich Listen der SharePoint-Website die **Aufgaben** Link.

     Die **Aufgaben – alle Vorgänge** Seite wird angezeigt.

3.  Auf der **Listentools** Registerkarte des Menübands, wählen Sie die **Liste** Registerkarte und dann auf die **Einstellungen** Gruppe **Listeneinstellungen**.

     Die **Listeneinstellungen** Seite wird angezeigt.

4.  Unter den **Kommunikation** Überschrift in der Nähe der oberen Rand der Seite Wählen Sie die **SharePoint Developer Center** verknüpfen, stellen Sie sicher, dass der Browser die Website geöffnet wird https://docs.microsoft.com/sharepoint/dev/, und klicken Sie dann den Browser schließen.

## <a name="cleaning-up-the-development-computer"></a>Bereinigung auf dem Entwicklungscomputer
 Nachdem Sie die Tests des Projektelements abgeschlossen haben, entfernen Sie die Projektelementvorlage aus der experimentellen Instanz von Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>So bereinigen Sie den Entwicklungscomputer

1.  Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste **Tools** > **Erweiterungen und Updates**.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2.  Wählen Sie in der Liste der Erweiterungen, die **Custom Action Project Item** -Erweiterung, und wählen Sie dann die **Deinstallieren** Schaltfläche.

3.  Wählen Sie in das Dialogfeld, das angezeigt wird, die **Ja** , um zu bestätigen, dass Sie verwenden möchten, deinstallieren Sie die Erweiterung aus, und wählen Sie dann die **jetzt neu starten** Schaltfläche, um die Deinstallation abzuschließen.

4.  Schließen Sie beide Instanzen von Visual Studio (die experimentelle Instanz und die Instanz von Visual Studio, in dem die Projektmappe "CustomActionProjectItem" geöffnet ist).

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Erstellen eines Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Schemareferenz zu Visual Studio-Vorlagen](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Vorgehensweise: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)
- [Standardspeicherorte für die benutzerdefinierte Aktion und IDs](http://go.microsoft.com/fwlink/?LinkId=181964)
