---
title: 'Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bootstrappers zum Datenschutzbestimmungen Prompt anzeigen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 6f20389e0487fd548ac239503faae01adb7dbdf1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bootstrappers zum Anzeigen einer Datenschutzeingabeaufforderung
Sie können konfigurieren, dass ClickOnce-Anwendungen automatisch aktualisiert, wenn Assemblys mit neueren Versionen und der Assemblyversionen verfügbar sind. Um sicherzustellen, dass Ihre Kunden dieses Verhalten zustimmen, können Sie eine datenschutzeingabeaufforderung anzuzeigen. Sie können dann auswählen, ob die Berechtigung für die Anwendung für die automatische Aktualisierung verwendet wird. Wenn die Anwendung für die automatische Aktualisierung nicht zulässig ist, wird nicht installiert.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Visual Studio 2010.  
  
## <a name="creating-an-update-consent-dialog-box"></a>Erstellen ein Update Zustimmung (Dialogfeld)  
 Zum Anzeigen einer datenschutzeingabeaufforderung erstellen Sie eine Anwendung mit der Frage den Reader an die automatischen Updates für die Anwendung zustimmen.  
  
#### <a name="to-create-a-consent-dialog-box"></a>So erstellen einen Zustimmung (Dialogfeld)  
  
1.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
2.  In der **neues Projekt** (Dialogfeld), klicken Sie auf **Windows**, und klicken Sie dann auf **WindowsFormsApplication**.  
  
3.  Für die **Namen**, Typ **ConsentDialog**, und klicken Sie dann auf **OK**.  
  
4.  Klicken Sie im Designer auf das Formular.  
  
5.  In der **Eigenschaften** Ändern der **Text** Eigenschaft **Update Zustimmungsdialogfeld**.  
  
6.  In der **Toolbox**, erweitern Sie **alle Windows Forms**, und ziehen Sie eine **Bezeichnung** Steuerelement dem Formular.  
  
7.  Klicken Sie im Designer auf das Label-Steuerelement.  
  
8.  In der **Eigenschaften** Ändern der **Text** Eigenschaft mit dem **Darstellung** , der dem folgenden:  
  
     Die Anwendung, die Sie installieren überprüft die neuesten Updates im Web. Indem Sie auf "Ich stimme zu" klicken, autorisieren Sie die Anwendung zu suchen und diese Updates automatisch aus dem Internet zu installieren.  
  
9. In der **Toolbox**, ziehen Sie eine **Kontrollkästchen** Steuerelement in die Mitte des Formulars.  
  
10. In der **Eigenschaften** Ändern der **Text** Eigenschaft mit dem **Layout** auf **ich stimme zu**.  
  
11. In der **Toolbox**, ziehen Sie eine **Schaltfläche** Steuerelement unten links in der Form.  
  
12. In der **Eigenschaften** Ändern der **Text** Eigenschaft mit dem **Layout** auf **Fortfahren**.  
  
13. In der **Eigenschaften** Ändern der **(Name)** Eigenschaft mit dem **Entwurf** auf **"ProceedButton"**.  
  
14. In der **Toolbox**, ziehen Sie eine **Schaltfläche** Steuerelement unten rechts auf der das Formular.  
  
15. In der **Eigenschaften** Ändern der **Text** Eigenschaft mit dem **Layout** auf **"Abbrechen"**.  
  
16. In der **Eigenschaften** Ändern der **(Name)** Eigenschaft mit dem **Entwurf** auf **CancelButton**.  
  
17. Doppelklicken Sie im Designer auf die **ich stimme zu** Kontrollkästchen, um das CheckedChanged-Ereignishandler zu generieren.  
  
18. Fügen Sie in der Codedatei Form1 den folgenden Code für das CheckedChanged-Ereignishandler ein.  
  
     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. Aktualisieren Sie den Klassenkonstruktor Deaktivieren der **Fortfahren** Schaltfläche standardmäßig.  
  
     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. Fügen Sie in der Codedatei Form1 den folgenden Code für eine boolesche Variable überwachen, wenn der Endbenutzer, Onlineupdates zugestimmt hat.  
  
     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. Doppelklicken Sie im Designer auf die **Fortfahren** Schaltfläche, um dem Click-Ereignishandler zu generieren.  
  
22. Fügen Sie in der Codedatei Form1 den folgenden Code, um dem Click-Ereignishandler für das **Fortfahren** Schaltfläche.  
  
     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. Doppelklicken Sie im Designer auf die **"Abbrechen"** Schaltfläche, um dem Click-Ereignishandler zu generieren.  
  
24. Fügen Sie in der Codedatei Form1 den folgenden Code für das Click-Ereignishandler für das **"Abbrechen"** Schaltfläche.  
  
     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. Aktualisieren Sie die Anwendung auf einen Fehler zurück, wenn der Endbenutzer auf Onlineupdates nicht einverstanden ist.  
  
     Visual Basic nur für Entwickler:  
  
    1.  In **Projektmappen-Explorer**, klicken Sie auf **ConsentDialog**.  
  
    2.  Auf der **Projekt** Menü klicken Sie auf **Modul hinzufügen**, und klicken Sie dann auf **hinzufügen**.  
  
    3.  Fügen Sie in der Codedatei "Module1.vb" den folgenden Code ein.  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  Auf der **Projekt** Menü klicken Sie auf **ConsentDialog Eigenschaften**, und klicken Sie dann auf die **Anwendung** Registerkarte.  
  
    5.  Deaktivieren Sie **Anwendungsframework aktivieren**.  
  
    6.  In der **Startobjekt** wählen Sie im Dropdownmenü **Module1**.  
  
        > [!NOTE]
        >  Deaktivieren das Anwendungsframework deaktiviert Funktionen, z. B. visuellen Windows XP-Stilen, Anwendungsereignisse Begrüßungsbildschirm, Einzelinstanz-Anwendung und mehr. Weitere Informationen finden Sie unter [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
     Visual C#-nur für Entwickler:  
  
     Öffnen Sie die Codedatei "Program.cs", und fügen Sie den folgenden Code hinzu.  
  
     [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. Auf der **erstellen** Menü klicken Sie auf **Projektmappe erstellen**.  
  
## <a name="creating-the-custom-bootstrapper-package"></a>Erstellen das benutzerdefinierte Bootstrapperpaket  
 Sie können zum Anzeigen der datenschutzeingabeaufforderung für Endbenutzer Erstellen eines benutzerdefinierten Bootstrapperpakets für die Update-Zustimmungsdialogfeld-Anwendung und fügen Sie ihn als erforderliche Komponente in allen von ClickOnce-Anwendungen.  
  
 Dieses Verfahren veranschaulicht, wie ein benutzerdefiniertes Bootstrapperpaket erstellen, indem Sie die folgenden Dokumente zu erstellen:  
  
-   Eine product.xml Manifestdatei, um den Inhalt des Bootstrappers zu beschreiben.  
  
-   Eine Manifestdatei "Package.xml", um die Lokalisierung-spezifische Aspekte des Pakets, z. B. Zeichenfolgen und die Software-Lizenzbedingungen aufzulisten.  
  
-   Ein Dokument für die Software-Lizenzbedingungen.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Schritt 1: Erstellen des Verzeichnisses Bootstrapper  
  
1.  Erstellen Sie ein Verzeichnis mit dem Namen **UpdateConsentDialog** in %PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
    > [!NOTE]
    >  Möglicherweise Administratorrechte für diesen Ordner zu erstellen.  
  
2.  Erstellen Sie in das Verzeichnis UpdateConsentDialog ein Unterverzeichnis mit dem Namen En.  
  
    > [!NOTE]
    >  Erstellen Sie ein neues Verzeichnis für jedes Gebietsschema. Sie können z. B. Unterverzeichnisse für die Gebietsschemas fr "und" de "hinzufügen. Diese Verzeichnisse würde die Zeichenfolgen für Französisch und Deutsch und die Sprachpakete, bei Bedarf enthalten.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Schritt 2: Erstellen die Manifestdatei product.xml  
  
1.  Erstellen Sie eine Textdatei namens `product.xml`.  
  
2.  Fügen Sie den folgenden XML-Code in der Datei product.xml hinzu. Stellen Sie sicher, dass Sie nicht den vorhandenen XML-Code überschreiben.  
  
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
  
3.  Speichern Sie die Datei in das UpdateConsentDialog Bootstrapper-Verzeichnis ein.  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Schritt 3: Erstellen Sie das Manifest "Package.xml" Lizenzbedingungen Datei- und die software  
  
1.  Erstellen Sie eine Textdatei namens `package.xml`.  
  
2.  Fügen Sie den folgenden XML-Code zum Definieren des Gebietsschemas und die Software-Lizenzbedingungen enthalten, in der Datei "Package.xml". Stellen Sie sicher, dass Sie nicht den vorhandenen XML-Code überschreiben.  
  
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
  
3.  Speichern Sie die Datei, auf das Unterverzeichnis "En" im UpdateConsentDialog Bootstrapper-Verzeichnis.  
  
4.  Erstellen Sie ein Dokument namens eula.rtf für die Software-Lizenzbedingungen.  
  
    > [!NOTE]
    >  Die Software-Lizenzbedingungen sind zu Lizenzierung, GEWÄHRLEISTUNGEN Schulden und örtlich anwendbaren Gesetzen. Diese Dateien sollten gebietsschemaspezifisch sein, achten Sie darauf, dass die Datei in einem Format gespeichert wird, die MBCS und Unicode-Zeichen unterstützt. Wenden Sie sich an Ihre rechtsabteilung über den Inhalt der Software-Lizenzbedingungen.  
  
5.  Speichern Sie das Dokument, das Unterverzeichnis "En" im UpdateConsentDialog Bootstrapper-Verzeichnis.  
  
6.  Erstellen Sie erforderlichenfalls eine neue Datei "package.xml" manifest und ein neues eula.rtf Dokument für die Software-Lizenzbedingungen für jedes Gebietsschema. Beispielsweise wenn Sie die Unterverzeichnisse für die Gebietsschemas fr "und" de "erstellt haben, erstellen Sie separate" Package.xml "Manifestdateien und Software-Lizenzbedingungen, und speichern Sie sie in den Unterverzeichnissen fr" und "de".  
  
## <a name="setting-the-update-consent-application-as-a-prerequisite"></a>Festlegen der Zustimmung Updateanwendung als erforderliche Komponente  
 In Visual Studio können Sie die Anwendung zustimmen, Update als erforderliche Komponente festlegen.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Die Zustimmung Updateanwendung als erforderliche Komponente festlegen  
  
1.  In **Projektmappen-Explorer**, klicken Sie auf den Namen der Anwendung, die Sie bereitstellen möchten.  
  
2.  Auf der **Projekt** Menü klicken Sie auf *Projektname* **Eigenschaften**.  
  
3.  Klicken Sie auf die **veröffentlichen** Seite, und klicken Sie dann auf **Voraussetzungen**.  
  
4.  Wählen Sie **aktualisieren Zustimmungsdialogfeld**.  
  
    > [!NOTE]
    >  Sie müssen möglicherweise schließen und öffnen Visual Studio für die Verwendung der Update-Zustimmungsdialogfeld in das Dialogfeld erforderlichen Komponenten finden Sie unter.  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="creating-and-testing-the-setup-program"></a>Erstellen und testen das Setup-Programm  
 Nachdem Sie die Anwendung zustimmen, Update als erforderliche Komponente festgelegt, können Sie den Installer und den Bootstrapper für Ihre Anwendung generieren.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Zum Erstellen und testen das Setup-Programm, indem Sie nicht auf ich stimme zu  
  
1.  In **Projektmappen-Explorer**, klicken Sie auf den Namen der Anwendung, die Sie bereitstellen möchten.  
  
2.  Auf der **Projekt** Menü klicken Sie auf *Projektname* **Eigenschaften**.  
  
3.  Klicken Sie auf die **veröffentlichen** Seite, und klicken Sie dann auf **jetzt veröffentlichen**.  
  
4.  Wenn die Ausgabe der Veröffentlichung nicht automatisch geöffnet wird, navigieren Sie zu die Ausgabe der Veröffentlichung.  
  
5.  Führen Sie das Programm Setup.exe.  
  
     Das Setup-Programm zeigt den Update-Zustimmungsdialogfeld Softwarelizenzvertrag.  
  
6.  Lesen Sie den Softwarelizenzvertrag, und klicken Sie dann auf **Accept**.  
  
     Die Update-Zustimmungsdialogfeld-Anwendung angezeigt wird, und zeigt den folgenden Text: überprüft die Anwendung, die Sie installieren die neuesten Updates im Web. Durch Klicken auf ich stimme zu, autorisieren Sie die Anwendung zur Überprüfung auf Updates automatisch auf das Internet.  
  
7.  Schließen Sie die Anwendung, oder klicken Sie auf "Abbrechen".  
  
     Die Anwendung zeigt einen Fehler: Fehler beim Installieren von Systemkomponenten für *Parameter "ApplicationName"*. Setup kann nicht fortgesetzt, bis alle Komponenten erfolgreich installiert wurden.  
  
8.  Klicken Sie auf Details, um die folgende Fehlermeldung angezeigt: Komponente aktualisieren Zustimmungsdialogfeld Fehler bei der Installation mit der folgenden Fehlermeldung: "die automatische Aktualisierung Vereinbarung wird nicht akzeptiert." Die folgenden Komponenten bei der Installation:-Update-Zustimmungsdialogfeld  
  
9. Klicken Sie auf **Schließen**.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Zum Erstellen und testen das Setup-Programm, indem Sie auf ich stimme zu  
  
1.  In **Projektmappen-Explorer**, klicken Sie auf den Namen der Anwendung, die Sie bereitstellen möchten.  
  
2.  Auf der **Projekt** Menü klicken Sie auf *Projektname* **Eigenschaften**.  
  
3.  Klicken Sie auf die **veröffentlichen** Seite, und klicken Sie dann auf **jetzt veröffentlichen**.  
  
4.  Wenn die Ausgabe der Veröffentlichung nicht automatisch geöffnet wird, navigieren Sie zu die Ausgabe der Veröffentlichung.  
  
5.  Führen Sie das Programm Setup.exe.  
  
     Das Setup-Programm zeigt den Update-Zustimmungsdialogfeld Softwarelizenzvertrag.  
  
6.  Lesen Sie den Softwarelizenzvertrag, und klicken Sie dann auf **Accept**.  
  
     Die Update-Zustimmungsdialogfeld-Anwendung angezeigt wird, und zeigt den folgenden Text: überprüft die Anwendung, die Sie installieren die neuesten Updates im Web. Durch Klicken auf ich stimme zu, autorisieren Sie die Anwendung zur Überprüfung auf Updates automatisch auf das Internet.  
  
7.  Klicken Sie auf **ich stimme zu**, und klicken Sie dann auf **Fortfahren**.  
  
     So installieren Sie Start der Anwendung.  
  
8.  Wenn das Dialogfeld "Anwendung installieren" angezeigt wird, klicken Sie auf **installieren**.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md)   
 [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md)   
 [Vorgehensweise: Erstellen eines Produktmanifests](../deployment/how-to-create-a-product-manifest.md)   
 [Vorgehensweise: Erstellen eines Paketmanifests](../deployment/how-to-create-a-package-manifest.md)   
 [Referenz zum Produkt- und Paketschema](../deployment/product-and-package-schema-reference.md)