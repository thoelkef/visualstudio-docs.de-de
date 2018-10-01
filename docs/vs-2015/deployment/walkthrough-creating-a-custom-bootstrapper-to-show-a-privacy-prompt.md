---
title: 'Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bootstrappers zum Datenschutzbestimmungen Eingabeaufforderung anzeigen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 790aa1c67ef8c76e404876bd61a42d4b286892da
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509628"
---
# <a name="walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bootstrappers zum Anzeigen einer Datenschutzeingabeaufforderung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bootstrappers zum Anzeigen einer Datenschutzeingabeaufforderung](https://docs.microsoft.com/visualstudio/deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt).  
  
Sie können konfigurieren, dass ClickOnce-Anwendungen automatisch aktualisiert, wenn Assemblys mit neueren Versionen und die Assemblyversionen verfügbar sind. Um sicherzustellen, dass Ihre Kunden, die dieses Verhalten zu gestatten, können Sie eine datenschutzeingabeaufforderung anzuzeigen. Sie können dann auswählen, ob gewähren der Berechtigung für die Anwendung zum automatischen Aktualisieren verwendet wird. Wenn die Anwendung nicht zulässig ist, automatisch zu aktualisieren, wird es nicht installiert.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Visual Studio 2010.  
  
## <a name="creating-an-update-consent-dialog-box"></a>Erstellen ein Update Zustimmung (Dialogfeld)  
 Erstellen Sie eine Anwendung, die den Reader, der für die Zustimmung zu automatischen Updates für die Anwendung fragt, zum Anzeigen einer datenschutzeingabeaufforderung.  
  
#### <a name="to-create-a-consent-dialog-box"></a>Um ein Dialogfeld "Zustimmung" zu erstellen.  
  
1.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld klicken Sie auf **Windows**, und klicken Sie dann auf **WindowsFormsApplication**.  
  
3.  Für die **Namen**, Typ **ConsentDialog**, und klicken Sie dann auf **OK**.  
  
4.  Klicken Sie im Designer auf das Formular.  
  
5.  In der **Eigenschaften** Ändern der **Text** Eigenschaft **Update-Zustimmungsdialogfeld**.  
  
6.  In der **Toolbox**, erweitern Sie **alle Windows Forms**, und ziehen Sie eine **Bezeichnung** -Steuerelement auf das Formular.  
  
7.  Klicken Sie im Designer auf das Label-Steuerelement.  
  
8.  In der **Eigenschaften** Ändern der **Text** Eigenschaft **Darstellung** folgt:  
  
     Die Anwendung, die Sie installieren, überprüft die neuesten Updates im Web. Indem Sie auf "Ich stimme zu" klicken, autorisieren Sie die Anwendung zu suchen und installieren Sie Updates automatisch über das Internet.  
  
9. In der **Toolbox**, ziehen Sie eine **Kontrollkästchen** Steuerelement in die Mitte des Formulars.  
  
10. In der **Eigenschaften** Ändern der **Text** Eigenschaft **Layout** zu **ich stimme zu**.  
  
11. In der **Toolbox**, ziehen Sie eine **Schaltfläche** Steuerelement unten links in der Form.  
  
12. In der **Eigenschaften** Ändern der **Text** Eigenschaft **Layout** zu **fortsetzen**.  
  
13. In der **Eigenschaften** Ändern der **(Name)** Eigenschaft **Entwurf** zu **"ProceedButton"**.  
  
14. In der **Toolbox**, ziehen Sie eine **Schaltfläche** Steuerelement auf der unteren rechten Ecke des Formulars.  
  
15. In der **Eigenschaften** Ändern der **Text** Eigenschaft **Layout** zu **Abbrechen**.  
  
16. In der **Eigenschaften** Ändern der **(Name)** Eigenschaft **Entwurf** zu **CancelButton**.  
  
17. Doppelklicken Sie im Designer auf die **ich stimme zu** Kontrollkästchen, um das CheckedChanged-Ereignishandler zu generieren.  
  
18. Fügen Sie in der Codedatei Form1 den folgenden Code für das CheckedChanged-Ereignishandler hinzu.  
  
     [!code-csharp[ConsentDialog#1](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#1)]
     [!code-vb[ConsentDialog#1](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#1)]  
  
19. Aktualisieren Sie den Konstruktor der Klasse zum Deaktivieren der **fortsetzen** Schaltfläche in der Standardeinstellung.  
  
     [!code-csharp[ConsentDialog#6](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#6)]
     [!code-vb[ConsentDialog#6](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#6)]  
  
20. Fügen Sie den folgenden Code für eine boolesche Variable, um nachzuverfolgen, wenn der Endbenutzer Onlineupdates zugestimmt hat, in der Codedatei Form1.  
  
     [!code-csharp[ConsentDialog#3](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#3)]
     [!code-vb[ConsentDialog#3](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#3)]  
  
21. Doppelklicken Sie im Designer auf die **fortsetzen** Schaltfläche, um dem Click-Ereignishandler zu generieren.  
  
22. Fügen Sie in der Codedatei Form1 den folgenden Code zum Click-Ereignishandler für die **fortsetzen** Schaltfläche.  
  
     [!code-csharp[ConsentDialog#2](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#2)]
     [!code-vb[ConsentDialog#2](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#2)]  
  
23. Doppelklicken Sie im Designer auf die **Abbrechen** Schaltfläche, um dem Click-Ereignishandler zu generieren.  
  
24. Fügen Sie in der Codedatei Form1 den folgenden Code für das Click-Ereignishandler für die **Abbrechen** Schaltfläche.  
  
     [!code-csharp[ConsentDialog#4](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#4)]
     [!code-vb[ConsentDialog#4](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#4)]  
  
25. Aktualisieren Sie die Anwendung auf einen Fehler zurück, wenn der Endbenutzer zu online-Updates nicht einverstanden ist.  
  
     Visual Basic nur für Entwickler:  
  
    1.  In **Projektmappen-Explorer**, klicken Sie auf **ConsentDialog**.  
  
    2.  Auf der **Projekt** Menü klicken Sie auf **Modul hinzufügen**, und klicken Sie dann auf **hinzufügen**.  
  
    3.  Fügen Sie in der Datei "Module1.vb" Code den folgenden Code ein.  
  
         [!code-vb[ConsentDialog#7](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/module1.vb#7)]  
  
    4.  Auf der **Projekt** Menü klicken Sie auf **ConsentDialog Eigenschaften**, und klicken Sie dann auf die **Anwendung** Registerkarte.  
  
    5.  Deaktivieren Sie **Anwendungsframework aktivieren**.  
  
    6.  In der **Startobjekt** wählen Sie im Dropdownmenü **Module1**.  
  
        > [!NOTE]
        >  Deaktivieren das Anwendungsframework deaktiviert Features wie z. B. die visuellen Windows XP-Stile, Anwendungsereignisse, Splash-Bildschirm, einzelinstanzanwendung und vieles mehr. Weitere Informationen finden Sie unter [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
     Visual C# -Code nur für Entwickler:  
  
     Öffnen Sie die Codedatei "Program.cs", und fügen Sie den folgenden Code hinzu.  
  
     [!code-csharp[ConsentDialog#5](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/program.cs#5)]  
  
26. Auf der **erstellen** Menü klicken Sie auf **BuildSolution**.  
  
## <a name="creating-the-custom-bootstrapper-package"></a>Erstellen das benutzerdefinierte Bootstrapperpaket  
 Sie können zum Anzeigen der datenschutzeingabeaufforderung für Endbenutzer, Erstellen eines benutzerdefinierten Bootstrapperpakets für die Update-Zustimmungsdialogfeld-Anwendung und fügen Sie es als erforderliche Komponente in allen von ClickOnce-Anwendungen.  
  
 Dieses Verfahren veranschaulicht, wie ein benutzerdefinierte Bootstrapperpaket zu erstellen, indem Sie die folgenden Dokumente zu erstellen:  
  
-   Eine product.xml Manifestdatei, um den Inhalt des Bootstrappers zu beschreiben.  
  
-   Eine Manifestdatei "Package.xml", um die Lokalisierung-spezifische Aspekte des Pakets, z. B. Zeichenfolgen und die Software-Lizenzbedingungen aufzulisten.  
  
-   Ein Dokument für die Software-Lizenzbedingungen.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Schritt 1: Erstellen Sie das Bootstrapperverzeichnis  
  
1.  Erstellen Sie ein Verzeichnis mit dem Namen **UpdateConsentDialog** im %PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
    > [!NOTE]
    >  Möglicherweise Administratorrechte verfügen, um diesen Ordner zu erstellen.  
  
2.  Erstellen Sie im Verzeichnis UpdateConsentDialog ein Unterverzeichnis namens En.  
  
    > [!NOTE]
    >  Erstellen Sie ein neues Verzeichnis für jedes Gebietsschema. Beispielsweise können Sie die Unterverzeichnisse für den fr und de Gebietsschemas hinzufügen. Diese Verzeichnisse würde die Zeichenfolgen für Französisch und Deutsch und Language Packs bei Bedarf enthalten.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Schritt 2: Erstellen Sie die product.xml-Manifestdatei  
  
1.  Erstellen Sie eine Textdatei namens `product.xml`.  
  
2.  Fügen Sie den folgenden XML-Code in die product.xml-Datei hinzu. Stellen Sie sicher, dass Sie nicht den vorhandenen XML-Code überschreiben.  
  
    ```  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3.  Speichern Sie die Datei in das Bootstrapperverzeichnis UpdateConsentDialog.  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Schritt 3: Erstellen Sie das Manifest "Package.xml" Lizenzbedingungen-Datei und der software  
  
1.  Erstellen Sie eine Textdatei namens `package.xml`.  
  
2.  Fügen Sie den folgenden XML-Code definiert das Gebietsschema und die Software-Lizenzbedingungen einschließen möchten, in der Datei "Package.xml". Stellen Sie sicher, dass Sie nicht den vorhandenen XML-Code überschreiben.  
  
    ```  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3.  Speichern Sie die Datei in das Unterverzeichnis "En" in das Bootstrapperverzeichnis UpdateConsentDialog.  
  
4.  Erstellen Sie ein Dokument namens eula.rtf für die Software-Lizenzbedingungen.  
  
    > [!NOTE]
    >  Die Software-Lizenzbedingungen sollte Informationen zu Lizenzierung, zu GEWÄHRLEISTUNGEN, Schulden und vor Ort geltenden Gesetze enthalten. Diese Dateien sollten gebietsschemaspezifische, also stellen Sie sicher, dass die Datei in einem Format gespeichert wird, die MBCS oder UNICODE-Zeichen unterstützt. Wenden Sie sich an Ihre rechtsabteilung über den Inhalt der Software-Lizenzbedingungen.  
  
5.  Speichern Sie das Dokument, das Unterverzeichnis "En" in das Bootstrapperverzeichnis UpdateConsentDialog.  
  
6.  Erstellen Sie bei Bedarf eine neue "Package.xml" Manifestdatei und ein neues eula.rtf-Dokument für den Software-Lizenzbedingungen für jedes Gebietsschema. Sie Unterverzeichnisse für das fr und de Systemgebietsschema erstellt haben, z. B. erstellen Sie separate "Package.xml" manifest-Dateien und Software-Lizenzbedingungen zu und speichern Sie sie in den Unterverzeichnissen fr und de.  
  
## <a name="setting-the-update-consent-application-as-a-prerequisite"></a>Festlegen der Zustimmung Aktualisieren einer Anwendung als erforderliche Komponente  
 In Visual Studio können Sie die Zustimmung der Update-Anwendung als erforderliche Komponente festlegen.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Um die Anwendung für die Update-Zustimmung als erforderliche Komponente festzulegen.  
  
1.  In **Projektmappen-Explorer**, klicken Sie auf den Namen der Anwendung, die Sie bereitstellen möchten.  
  
2.  Auf der **Projekt** Menü klicken Sie auf *ProjectName* **Eigenschaften**.  
  
3.  Klicken Sie auf die **veröffentlichen** Seite, und klicken Sie dann auf **Voraussetzungen**.  
  
4.  Wählen Sie **aktualisieren Zustimmungsdialogfeld**.  
  
    > [!NOTE]
    >  Sie müssen möglicherweise schließen und öffnen Visual Studio, um die Update-Zustimmungsdialogfeld im Dialogfeld "erforderliche Komponenten" finden Sie unter.  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="creating-and-testing-the-setup-program"></a>Erstellen und testen das Setup-Programm  
 Nachdem Sie die Zustimmung der Update-Anwendung als erforderliche Komponente festgelegt haben, können Sie das Installationsprogramm und die Bootstrapper für Ihre Anwendung generieren.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Zum Erstellen und testen das Setup-Programm, indem Sie nicht auf ich stimme zu  
  
1.  In **Projektmappen-Explorer**, klicken Sie auf den Namen der Anwendung, die Sie bereitstellen möchten.  
  
2.  Auf der **Projekt** Menü klicken Sie auf *ProjectName* **Eigenschaften**.  
  
3.  Klicken Sie auf die **veröffentlichen** Seite, und klicken Sie dann auf **jetzt veröffentlichen**.  
  
4.  Wenn die Ausgabe der Veröffentlichung nicht automatisch geöffnet wird, navigieren Sie auf die Ausgabe der Veröffentlichung.  
  
5.  Führen Sie das Programm Setup.exe.  
  
     Das Setup-Programm zeigt die Update-Zustimmungsdialogfeld Software-Lizenzbedingungen.  
  
6.  Lesen Sie die Software-Lizenzbedingungen, und klicken Sie dann auf **Accept**.  
  
     Die Anwendung für die Update-Zustimmungsdialogfeld angezeigt wird, und zeigt den folgenden Text: überprüft die Anwendung, die Sie installieren die neuesten Updates im Web. Wenn Sie auf ich stimme zu, autorisieren Sie die Anwendung nach Updates automatisch auf das Internet zu überprüfen.  
  
7.  Schließen Sie die Anwendung aus, oder klicken Sie auf "Abbrechen".  
  
     Die Anwendung wird ein Fehler angezeigt: Fehler beim Installieren der Systemkomponenten für *ApplicationName*. Setup kann nicht fortgesetzt, bis alle Systemkomponenten erfolgreich installiert wurden.  
  
8.  Klicken Sie auf Details, um die folgende Fehlermeldung angezeigt: Komponente aktualisieren-Zustimmungsdialogfeld Fehler bei der Installation die folgende Fehlermeldung angezeigt: "die Vereinbarung für die automatische Aktualisierung wird nicht akzeptiert." Die folgenden Komponenten konnten nicht installiert:-Update-Zustimmungsdialogfeld  
  
9. Klicken Sie auf **Schließen**.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Zum Erstellen und testen das Setup-Programm, indem Sie auf ich stimme zu  
  
1.  In **Projektmappen-Explorer**, klicken Sie auf den Namen der Anwendung, die Sie bereitstellen möchten.  
  
2.  Auf der **Projekt** Menü klicken Sie auf *ProjectName* **Eigenschaften**.  
  
3.  Klicken Sie auf die **veröffentlichen** Seite, und klicken Sie dann auf **jetzt veröffentlichen**.  
  
4.  Wenn die Ausgabe der Veröffentlichung nicht automatisch geöffnet wird, navigieren Sie auf die Ausgabe der Veröffentlichung.  
  
5.  Führen Sie das Programm Setup.exe.  
  
     Das Setup-Programm zeigt die Update-Zustimmungsdialogfeld Software-Lizenzbedingungen.  
  
6.  Lesen Sie die Software-Lizenzbedingungen, und klicken Sie dann auf **Accept**.  
  
     Die Anwendung für die Update-Zustimmungsdialogfeld angezeigt wird, und zeigt den folgenden Text: überprüft die Anwendung, die Sie installieren die neuesten Updates im Web. Wenn Sie auf ich stimme zu, autorisieren Sie die Anwendung nach Updates automatisch auf das Internet zu überprüfen.  
  
7.  Klicken Sie auf **ich stimme zu**, und klicken Sie dann auf **fortsetzen**.  
  
     Die Anwendung gestartet wird, installieren.  
  
8.  Wenn das Dialogfeld "Anwendung installieren" angezeigt wird, klicken Sie auf **installieren**.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md)   
 [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md)   
 [Vorgehensweise: Erstellen eines Produktmanifests](../deployment/how-to-create-a-product-manifest.md)   
 [Vorgehensweise: Erstellen eines Paketmanifests](../deployment/how-to-create-a-package-manifest.md)   
 [Referenz zum Produkt- und Paketschema](../deployment/product-and-package-schema-reference.md)



