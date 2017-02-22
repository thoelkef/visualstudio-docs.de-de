---
title: "Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bootstrappers zum Anzeigen einer Datenschutzeingabeaufforderung | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce-Bereitstellung, Voraussetzungen"
  - "Abhängigkeiten [.NET Framework], Benutzerdefiniertes Bootstrapperpaket"
  - "Bereitstellen von Anwendungen [Visual Studio], Benutzerdefinierte erforderliche Komponenten"
  - "Voraussetzungen [.NET Framework], Benutzerdefiniertes Bootstrapperpaket"
  - "Windows Installer-Bereitstellung, Voraussetzungen"
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bootstrappers zum Anzeigen einer Datenschutzeingabeaufforderung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können ClickOnce\-Anwendungen so konfigurieren, dass sie automatisch aktualisiert werden, wenn Assemblys mit neueren Dateiversionen und Assemblyversionen verfügbar werden.  Um sicherzustellen, dass die Kunden diesem Verhalten zustimmen, können Sie eine Datenschutzeingabeaufforderung anzeigen.  Dann können die Kunden entscheiden, ob sie die Berechtigung zur automatischen Aktualisierung der Anwendung erteilen möchten.  Wenn die automatische Aktualisierung der Anwendung nicht gestattet wird, findet keine Installation statt.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Visual Studio 2010  
  
## Erstellen eines Dialogfelds zur Updatezustimmung  
 Um eine Datenschutzeingabeaufforderung anzuzeigen, erstellen Sie eine Anwendung, die die Zustimmung des Lesers zur Installation automatischer Updates für die Anwendung einholt.  
  
#### So erstellen Sie ein Zustimmungsdialogfeld  
  
1.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt** auf **Windows**, und klicken Sie dann auf **Windows Forms**\-**Anwendung**.  
  
3.  Geben Sie als **Name** "ConsentDialog" ein, und klicken Sie dann auf **OK**.  
  
4.  Klicken Sie im Designer auf das Formular.  
  
5.  Ändern Sie im Eigenschaftenfenster die Eigenschaft **Text** in Update Consent Dialog.  
  
6.  Erweitern Sie in der **Toolbox** den Eintrag **Alle Windows Forms**, und ziehen Sie ein **Label**\-Steuerelement in das Formular.  
  
7.  Klicken Sie im Designer auf das Label\-Steuerelement.  
  
8.  Ändern Sie im Eigenschaftenfenster  die **Text**\-Eigenschaft unter **Darstellung** in Folgendes:  
  
     The application that you are about to install checks for the latest updates on the Web.  By clicking on "I Agree", you authorize the application to check for and install updates automatically from the Internet.  
  
9. Ziehen Sie in der **Toolbox** ein **Checkbox**\-Steuerelement in die Mitte des Formulars.  
  
10. Ändern Sie im Eigenschaftenfenster die **Text**\-Eigenschaft unter **Layout** in I Agree.  
  
11. Ziehen Sie in der **Toolbox** ein **Button**\-Steuerelement unten links in das Formular.  
  
12. Ändern Sie im Eigenschaftenfenster die **Text**\-Eigenschaft unter **Layout** in Proceed.  
  
13. Ändern Sie im Eigenschaftenfenster die **\(Name\)**\-Eigenschaft unter **Entwurf** in "ProceedButton".  
  
14. Ziehen Sie in der **Toolbox** ein **Button**\-Steuerelement unten rechts in das Formular.  
  
15. Ändern Sie im Eigenschaftenfenster die **Text**\-Eigenschaft unter **Layout** in Cancel.  
  
16. Ändern Sie im Eigenschaftenfenster die **\(Name\)**\-Eigenschaft unter **Entwurf** in "CancelButton".  
  
17. Doppelklicken Sie im Designer auf das Kontrollkästchen **I Agree**, um den CheckedChanged\-Ereignishandler zu generieren.  
  
18. Fügen Sie in der Form1\-Codedatei den folgenden Code für den CheckedChanged\-Ereignishandler hinzu.  
  
     [!code-cs[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. Aktualisieren Sie den Klassenkonstruktor, um die Schaltfläche **Proceed** standardmäßig zu deaktivieren.  
  
     [!code-cs[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. Fügen Sie in der Form1\-Codedatei den folgenden Code für eine zu verfolgende boolesche Variable hinzu, wenn der Endbenutzer der Installation von Onlineupdates zugestimmt hat.  
  
     [!code-cs[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. Doppelklicken Sie im Designer auf die Schaltfläche **Proceed**, um einen Click\-Ereignishandler zu generieren.  
  
22. Fügen Sie in der Form1\-Codedatei dem Click\-Ereignishandler den folgenden Code für die Schaltfläche **Proceed** hinzu.  
  
     [!code-cs[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. Doppelklicken Sie im Designer auf die Schaltfläche **Cancel**, um einen Click\-Ereignishandler zu generieren.  
  
24. Fügen Sie in der Form1\-Codedatei dem Click\-Ereignishandler den folgenden Code für die Schaltfläche **Cancel** hinzu.  
  
     [!code-cs[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. Aktualisieren Sie die Anwendung so, dass ein Fehler zurückgegeben wird, wenn der Endbenutzer den Onlineupdates nicht zustimmt.  
  
     Nur für Visual Basic\-Entwickler:  
  
    1.  Klicken Sie im **Projektmappen\-Explorer** auf **ConsentDialog**.  
  
    2.  Klicken Sie im Menü **Projekt** auf **Modul hinzufügen**, und klicken Sie dann auf **Hinzufügen**.  
  
    3.  Fügen Sie in der Module1.vb\-Codedatei den folgenden Code hinzu.  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  Klicken Sie im Menü **Projekt** auf **ConsentDialog\-Eigenschaften**, und klicken Sie dann auf die Registerkarte **Anwendung**.  
  
    5.  Deaktivieren Sie **Anwendungsframework aktivieren**.  
  
    6.  Wählen Sie im Dropdownmenü **Startobjekt** den Eintrag **Module1** aus.  
  
        > [!NOTE]
        >  Durch Deaktivieren des Anwendungsframeworks werden Funktionen wie z. B. visuelle Windows XP\-Stile, Anwendungsereignisse, Begrüßungsbildschirm, einzelne Instanzanwendung und mehr deaktiviert.  Weitere Informationen finden Sie unter [Seite "Anwendung", Projekt\-Designer \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
     Nur für Visual C\#\-Entwickler:  
  
     Öffnen Sie die Program.cs\-Codedatei, und fügen Sie den folgenden Code hinzu.  
  
     [!code-cs[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
## Erstellen des benutzerdefinierten Bootstrapperpakets  
 Um für Endbenutzer die Datenschutzeingabeaufforderung anzuzeigen, können Sie ein benutzerdefiniertes Bootstrapperpaket für die Anwendung "Dialogfeld zur Updatezustimmung" erstellen und es als erforderliche Komponente in alle ClickOnce\-Anwendungen einschließen.  
  
 Diese Prozedur veranschaulicht, wie ein benutzerdefiniertes Bootstrapperpaket erstellt wird, indem folgende Dokumente erstellt werden:  
  
-   Eine product.xml\-Manifestdatei, um den Inhalt des Bootstrappers zu beschreiben.  
  
-   Eine package.xml\-Manifestdatei, um die lokalisierungsspezifischen Aspekte des Pakets aufzulisten, z. B. Zeichenfolgen und die Softwarelizenzbedingungen.  
  
-   Ein Dokument für die Softwarelizenzbedingungen.  
  
#### Schritt 1: So erstellen Sie das Bootstrapperverzeichnis  
  
1.  Erstellen Sie ein Verzeichnis namens "UpdateConsentDialog" unter %PROGRAMME%\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages".  
  
    > [!NOTE]
    >  Sie benötigen möglicherweise Administratorrechte, um diesen Ordner zu erstellen.  
  
2.  Erstellen Sie im UpdateConsentDialog\-Verzeichnis ein Unterverzeichnis namens "en".  
  
    > [!NOTE]
    >  Erstellen Sie ein neues Verzeichnis für jedes Gebietsschema.  Sie können z. B. Unterverzeichnisse für die Gebietsschemas "fr" und "de" hinzufügen.  Diese Verzeichnisse würden die französischen und deutschen Zeichenfolgen und ggf. Language Packs enthalten.  
  
#### Schritt 2: So erstellen Sie die product.xml\-Manifestdatei  
  
1.  Erstellen Sie eine Textdatei mit dem Namen `product.xml`.  
  
2.  Fügen Sie der Datei "product.xml" den folgenden XML\-Code hinzu.  Stellen Sie sicher, dass Sie den vorhandenen XML\-Code nicht überschreiben.  
  
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
  
3.  Speichern Sie die Datei im UpdateConsentDialog\-Bootstrapperverzeichnis.  
  
#### Schritt 3: So erstellen Sie die package.xml\-Manifestdatei und die Softwarelizenzbedingungen  
  
1.  Erstellen Sie eine Textdatei mit dem Namen `package.xml`.  
  
2.  Fügen Sie der Datei "package.xml" den folgenden XML\-Code hinzu, um das Gebietsschema zu definieren und die Softwarelizenzbedingungen einzuschließen.  Stellen Sie sicher, dass Sie den vorhandenen XML\-Code nicht überschreiben.  
  
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
  
3.  Speichern Sie die Datei im Unterverzeichnis "en" im UpdateConsentDialog\-Bootstrapperverzeichnis.  
  
4.  Erstellen Sie ein Dokument mit dem Namen "eula.rtf" für die Softwarelizenzbedingungen.  
  
    > [!NOTE]
    >  Die Softwarelizenzbedingungen sollten Informationen zu Lizenzierung, Gewährleistungen, Haftungen und lokalen Gesetzen einschließen.  Diese Dateien sollten gebietsschemaspezifisch sein. Stellen Sie daher sicher, dass die Datei in einem Format gespeichert wird, das MBCS\- oder UNICODE\-Zeichen unterstützt.  Wenden Sie sich bezüglich des Inhalts der Softwarelizenzbedingungen an die Rechtsabteilung.  
  
5.  Speichern Sie das Dokument im Unterverzeichnis "en" im UpdateConsentDialog\-Bootstrapperverzeichnis.  
  
6.  Erstellen Sie bei Bedarf für jedes Gebietsschema eine neue package.xml\-Manifestdatei und ein neues eula.rtf\-Dokument für die Softwarelizenzbedingungen.  Wenn Sie z. B. Unterverzeichnisse für die Gebietsschemas "fr" und "de" erstellt haben, erstellen Sie separate package.xml\-Manifestdateien und Softwarelizenzbedingungen, und speichern Sie diese in den Unterverzeichnissen "fr" und "de".  
  
## Festlegen der Anwendung zur Updatezustimmung als erforderliche Komponente  
 In Visual Studio können Sie die Anwendung zur Updatezustimmung als erforderliche Komponente festlegen.  
  
#### So legen Sie die Anwendung zur Updatezustimmung als erforderliche Komponente fest  
  
1.  Klicken Sie im **Projektmappen\-Explorer** auf den Namen der Anwendung, die Sie bereitstellen möchten.  
  
2.  Klicken Sie im Menü **Projekt** auf *Projektname*\-**Eigenschaften**.  
  
3.  Klicken Sie auf die Seite **Veröffentlichen** und dann auf **Erforderliche Komponenten**.  
  
4.  Wählen Sie **Dialogfeld zur Updatezustimmung** aus.  
  
    > [!NOTE]
    >  Sie müssen möglicherweise Visual Studio schließen und erneut öffnen, um das Dialogfeld zur Updatezustimmung im Dialogfeld "Erforderliche Komponenten" zu sehen.  
  
5.  Klicken Sie auf **OK**.  
  
## Erstellen und Testen des Setupprogramms  
 Nachdem Sie die Anwendung zur Updatezustimmung als erforderliche Komponente festgelegt haben, können Sie das Installationsprogramm und den Bootstrapper für die Anwendung generieren.  
  
#### So erstellen und testen Sie das Setupprogramm, indem Sie nicht auf "Ich stimme zu" klicken  
  
1.  Klicken Sie im **Projektmappen\-Explorer** auf den Namen der Anwendung, die Sie bereitstellen möchten.  
  
2.  Klicken Sie im Menü **Projekt** auf *Projektname*\-**Eigenschaften**.  
  
3.  Klicken Sie auf die Seite **Veröffentlichen**, und klicken Sie dann auf **Jetzt veröffentlichen**.  
  
4.  Wenn die Veröffentlichungsausgabe nicht automatisch geöffnet wird, navigieren Sie zur Veröffentlichungsausgabe.  
  
5.  Führen Sie das Programm "Setup.exe" aus.  
  
     Das Setupprogramm zeigt den Softwarelizenzvertrag für das Dialogfeld zur Updatezustimmung an.  
  
6.  Lesen Sie den Softwarelizenzvertrag, und klicken Sie dann auf **Zustimmen**.  
  
     Das Dialogfeld zur Updatezustimmung wird mit dem folgenden Text angezeigt: Von der Anwendung, die Sie installieren möchten, wird geprüft, ob im Internet aktuelle Updates zur Verfügung stehen.  Sie autorisieren die Anwendung, im Internet automatisch nach Updates zu suchen und diese zu installieren, indem Sie auf "Ich stimme zu" klicken.  
  
7.  Schließen Sie die Anwendung, oder klicken Sie auf Abbrechen.  
  
     Die Anwendung zeigt einen Fehler an: Fehler beim Installieren der Systemkomponenten für *ApplicationName*.  Setup kann erst fortgesetzt werden, wenn alle Systemkomponenten erfolgreich installiert wurden.  
  
8.  Klicken Sie auf Details, um die folgende Fehlermeldung anzuzeigen: Fehler bei der Installation der Komponente "Dialogfeld zur Updatezustimmung" hat nicht mit der folgenden Fehlermeldung installiert: "Die Vereinbarung für automatische Updates wird nicht akzeptiert. Fehler bei der Installation der folgenden Komponenten: \- Dialogfeld zur Updatezustimmung  
  
9. Klicken Sie auf **Schließen**.  
  
#### So erstellen und testen Sie das Setupprogramm, indem Sie auf "Ich stimme zu" klicken  
  
1.  Klicken Sie im **Projektmappen\-Explorer** auf den Namen der Anwendung, die Sie bereitstellen möchten.  
  
2.  Klicken Sie im Menü **Projekt** auf *Projektname*\-**Eigenschaften**.  
  
3.  Klicken Sie auf die Seite **Veröffentlichen**, und klicken Sie dann auf **Jetzt veröffentlichen**.  
  
4.  Wenn die Veröffentlichungsausgabe nicht automatisch geöffnet wird, navigieren Sie zur Veröffentlichungsausgabe.  
  
5.  Führen Sie das Programm "Setup.exe" aus.  
  
     Das Setupprogramm zeigt den Softwarelizenzvertrag für das Dialogfeld zur Updatezustimmung an.  
  
6.  Lesen Sie den Softwarelizenzvertrag, und klicken Sie dann auf **Zustimmen**.  
  
     Das Dialogfeld zur Updatezustimmung wird mit dem folgenden Text angezeigt: Von der Anwendung, die Sie installieren möchten, wird geprüft, ob im Internet aktuelle Updates zur Verfügung stehen.  Sie autorisieren die Anwendung, im Internet automatisch nach Updates zu suchen und diese zu installieren, indem Sie auf "Ich stimme zu" klicken.  
  
7.  Klicken Sie auf **Ich stimme zu** und dann auf **Fortsetzen**.  
  
     Die Anwendungsinstallation beginnt.  
  
8.  Wenn das Dialogfeld "Anwendungsinstallation" angezeigt wird, klicken Sie auf **Installieren**.  
  
## Siehe auch  
 [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md)   
 [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md)   
 [Gewusst wie: Erstellen eines Produktmanifests](../deployment/how-to-create-a-product-manifest.md)   
 [Gewusst wie: Erstellen eines Paketmanifests](../deployment/how-to-create-a-package-manifest.md)   
 [Referenz zum Produkt\- und Paketschema](../deployment/product-and-package-schema-reference.md)