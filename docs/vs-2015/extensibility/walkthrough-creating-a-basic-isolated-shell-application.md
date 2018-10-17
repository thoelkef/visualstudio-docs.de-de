---
title: 'Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7158dcbd55229998e49e2d2891ae46d88c7fbc9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199536"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Exemplarische Vorgehensweise: Erstellen einer grundlegenden Isolated Shell-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise zeigt, wie Sie eine isolierte Shell-Lösung erstellen, das Toolfenster Info anpassen und erstellen ein Setup-Programm, das die isolated Shell installiert.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Um der isolated Shell bereitstellen zu können, müssen Sie auch das Visual Studio Shell (isoliert) Redistributable Package verwenden.  
  
## <a name="creating-an-isolated-shell-solution"></a>Erstellen einer isolierten Shell-Lösung  
 In diesem Abschnitt zeigt, wie die Visual Studio Shell Isolated-Projektvorlage zum Erstellen einer isolierten Shell-Projektmappe verwendet wird. Die Lösung enthält die folgenden Projekten:  
  
-   Die *SolutionName*. AboutBoxPackage-Projekt, dem Sie die Darstellung der Hilfe/Info-Dialogfeld anpassen kann.  
  
-   Das ShellExtensionsVSIX-Projekt, das die Datei "Source.Extension.vsixmanifest" enthält, die die verschiedenen Komponenten der isolated Shell-Anwendung definiert.  
  
-   Die *SolutionName* -Projekt, das die ausführbare Datei erzeugt, die der isolated Shell-Anwendung aufruft. Dieses Projekt enthält den Ordner Shell Anpassung, wodurch Sie anpassn die Darstellung und das Verhalten der isolated Shell-Anwendung.  
  
-   Die *SolutionName* UI-Projekt, die eine Satellitenassembly erzeugt, die aktiven Menübefehle und lokalisierbaren Zeichenfolgen definiert.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Zum Erstellen einer grundlegenden isolated Shell-Lösung  
  
1.  Öffnen Sie Visual Studio, und erstellen Sie ein neues Projekt.  
  
2.  In der **neues Projekt** Fenster erweitern **andere Projekttypen** und dann **Erweiterbarkeit**. Wählen Sie die **Visual Studio Shell Isolated** Projektvorlage.  
  
3.  Nennen Sie das Projekt `MyVSShellStub` und einen Speicherort angeben. Stellen Sie sicher, dass **Projektmappenverzeichnis erstellen** aktiviert ist, und klicken Sie dann auf **OK**.  
  
     Die neue Projektmappe wird in **Projektmappen-Explorer**.  
  
4.  Erstellen Sie die Projektmappe, und starten Sie das Debuggen der isolated Shell-Anwendung.  
  
     Die Visual Studio isolierte Shell wird angezeigt. Liest die Titelleiste **MyVSShellStub**. Das Title-Balken-Symbol wird von \MyVSShellStub\Resource Files\ApplicationIcon.ico generiert.  
  
## <a name="customizing-the-application-name-and-icon"></a>Anpassen der Anwendungsname und Symbol  
 Sie sollten das Branding Ihrer Anwendung mit den Namen Ihres Unternehmens und das Logo in der Titelleiste angezeigt. Die folgenden Schritte zeigen, wie Sie den Namen und Symbol an, die in der Titelleiste der benutzerdefinierten Anwendung angezeigt werden, durch Ändern der Paketdefinitionsdatei MyVSShellStub.Application.pkgdef ändern.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Zum Anpassen der Anwendungsname und Symbol  
  
1.  Öffnen Sie im Projekt MyVSShellStub \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2.  Ändern der `AppName` Elementwert, **"AppName" = "Fabrikam-Musik-Editor"**  
  
3.  Um das Anwendungssymbol zu ändern, kopieren Sie ein anderes Symbol zu dem Verzeichnis \MyVSShellStub\MyVSShellStub\MyVSShellStub\. Benennen Sie die vorhandene ApplicationIcon.ico-Datei in ApplicationIcon1.ico an. Benennen Sie die neue Datei in ApplicationIcon.ico an.  
  
4.  Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Der isolated Shell wird die IDE angezeigt. Die Titelleiste verfügt über das neue Symbol neben den Wörtern **Fabrikam Musik Editor**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Anpassen der standardmäßigen Web-Browser-Startseite  
 In diesem Abschnitt wird gezeigt, wie die Standardstartseite der Ändern der **Webbrowser** Fenster durch Ändern der Paketdefinitionsdatei.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Anpassen des Standard-Webbrowser-Startseite  
  
1.  Ändern Sie in der Datei MyVSShellStub.Application.pkgdef der `DefaultHomePage` Wert der Elements auf "http://www.microsoft.com".  
  
2.  Erstellen Sie das MyVSShellStub-Projekt neu.  
  
3.  Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen.  
  
4.  In **anzeigen / Other Windows**, klicken Sie auf **Webbrowser**. Die **Webbrowser** Fenster zeigt die Homepage der Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Entfernen den Druckbefehl  
 Die VSCT-Datei in einem isolierten Shell-UI-Projekt besteht aus einem Satz von Deklarationen des Formulars `<Define name=No_` *Element*`>`, wobei *Element* ist einer der von Visual Studio-Standardmenüs und die Befehle.  
  
 Wenn eine Deklaration aufweist, wird dieses Menü oder den Befehl aus der isolated Shell ausgeschlossen. Im Gegensatz dazu, wenn eine Deklaration kommentiert wird, ist das Menü oder den Befehl in der isolated Shell enthalten.  
  
 In den folgenden Schritten heben Sie die auskommentierung Sie Druckbefehl in der VSCT-Datei.  
  
#### <a name="to-remove-the-print-command"></a>So entfernen Sie den Druckbefehl  
  
1.  Überprüfen Sie, ob die **Drucken** -Befehl angezeigt wird, auf die **Datei** im Menü der isolated Shell-Anwendung.  
  
2.  Öffnen Sie im Projekt MyVSShellStubUI \Resource Files\MyVSShellStubUI.vsct für die Bearbeitung aus.  
  
3.  Die kommentarmarkierung dieser Zeile aufheben:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Dadurch wird den Druckbefehl entfernt.  
  
5.  Debuggen der isolated Shell-Anwendung gestartet werden. Überprüfen Sie, ob die **Datei / drucken** Befehl ist nicht mehr vorhanden.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Entfernen von Funktionen aus der Isolated Shell  
 Sie können einige Pakete entfernen, die mit Visual Studio geladen werden, durch Bearbeiten der pkgundef-Datei, wenn Sie nicht über diese Features in Ihrer benutzerdefinierten isolierten Shell-Anwendung wünschen. Sie geben Sie das Paket in einer der Unterschlüssel des Registrierungsschlüssels $RootKey$ \Packages.  
  
> [!NOTE]
>  Die GUIDs von Visual Studio-Funktionen finden Sie unter [-Paket-GUIDs von Visual Studio-Features](../extensibility/package-guids-of-visual-studio-features.md).  
  
 Das folgende Verfahren zeigt, wie So entfernen Sie den XML-Code-Editor aus der isolated Shell.  
  
#### <a name="to-remove-the-xml-editor"></a>So entfernen Sie den XML-editor  
  
1.  Öffnen Sie die MyVSShellStub.pkgundef-Datei im Ordner des Projekts MyVSShellStub Shell-Anpassung aus.  
  
2.  Heben Sie die auskommentierung der folgenden Zeile:  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  Erstellen Sie die Projektmappe neu, und starten Sie das Debuggen der isolated Shells. Öffnen Sie eine XML-Datei, z. B. \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Stellen Sie sicher, dass die XML-Schlüsselwörter in der Datei nicht farbig markiert werden und geben Sie diese "<" in einer Zeile bringt nicht um XML-QuickInfos.  
  
## <a name="customizing-the-helpabout-box"></a>Anpassen der Hilfe/Info-Dialogfeld  
 Sie können anpassen, die Hilfe/Info-Dialogfeld, das als Teil der isolated Shell-Projektvorlage erstellt wird.  
  
#### <a name="to-customize-the-company-name"></a>Name des Unternehmens anpassen.  
  
1.  Der Firmenname, Copyrightinformationen, Produktversion und produktbeschreibung sind in der Datei \Properties\AssemblyInfo.cs MyVSShellStub.AboutBoxPackage im Projekt gefunden. Öffnen Sie diese Datei.  
  
2.  Ändern der `AssemblyCompany` Wert **Fabrikam**, `AssemblyProduct` und `AssemblyTitle` Werte **Fabrikam-Musik-Editor**, und die `AssemblyCopyright` Wert **Copyright © Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  Ändern Sie zum Hinzufügen einer Beschreibung des Produkts der `AssemblyDescription` Wert **die Beschreibung des Fabrikam-Musik-Editor.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  Mit dem Debuggen beginnen, und öffnen Sie in der isolated Shell-Anwendung, die **Hilfe / Info** Feld. Daraufhin sollte die geänderten Zeichenfolgen. Der Titel, der die Hilfe/Info-Dialogfeld ist identisch mit der `AssemblyTitle` Wert in der Datei "AssemblyInfo.cs".  
  
5.  Die Eigenschaften der **Hilfe bzw. Info** Felds selbst in der Datei MyVSShellStub.AboutBoxPackage\AboutBox.xaml gefunden werden. Um die Breite der Hilfe/Info-Dialogfeld zu ändern, rufen Sie die `AboutDialogStyle` blockieren, und legen Sie die `Width` Eigenschaft auf 200:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6.  Erstellen Sie die Projektmappe neu, und starten Sie das Debuggen der isolated Shells. Die Hilfe/Info-Dialogfeld sollte ungefähr Quadrat.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Vor der Bereitstellung der Isolated Shell-Anwendung  
 Die isolated Shell-Anwendung kann auf jedem Computer installiert werden, die über das Visual Studio Shell (isoliert) Redistributable Package verfügt. Weitere Informationen über das redistributable Package finden Sie unter den [Downloads zu Visual Studio-Erweiterbarkeit](http://go.microsoft.com/fwlink/?LinkID=119298) Website.  
  
## <a name="deploying-the-isolated-shell-application"></a>Bereitstellen der Isolated Shell-Anwendung  
 Sie stellen Ihre isolated Shell-Anwendung auf einem Zielcomputer durch das Erstellen eines Setup-Projekts bereit. Sie müssen Folgendes angeben:  
  
-   Das Layout der Ordner und Dateien auf dem Zielcomputer.  
  
-   Die Starten von Bedingungen, die garantieren, dass .NET Framework und Visual Studio-Runtime Shell, die auf dem Zielcomputer installiert sind.  
  
 Im folgenden Verfahren müssen Sie InstallShield Limited Edition auf Ihrem Computer zu installieren.  
  
#### <a name="to-create-the-setup-project"></a>Um das Setup-Projekt zu erstellen.  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektmappenknoten, und klicken Sie dann auf **neues Projekt hinzufügen**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie **andere Projekttypen** und wählen Sie dann **Setup und Bereitstellung**. Wählen Sie die InstallShield-Vorlage. Nennen Sie das neue Projekt `MySetup` , und klicken Sie dann auf **OK**.  
  
3.  Wenn der InstallShield Limited Edition bereits installiert ist, weiterhin mit dem nächsten Schritt.  
  
     Wenn der InstallShield Limited-Edition nicht bereits installiert ist, wird die InstallShield-Download-Seite angezeigt. Führen Sie die Anweisungen zum Herunterladen und installieren Sie das Produkt, das Auswählen der Version von InstallShield, die mit Ihrer Version von Visual Studio kompatibel ist. Sie müssen entscheiden, ob die Installation von InstallShield nicht registriert oder verwenden sie eine Evaluierungsversion. Sie müssen Visual Studio nach Abschluss der Installation neu starten.  
  
    > [!IMPORTANT]
    >  Sie müssen Visual Studio als Administrator starten, bevor Sie ein InstallShield-Projekt erstellen. Wenn Sie dies nicht tun, erhalten Sie Fehler, wenn Sie das Projekt erstellen.  
  
 Die nächsten Schritte zeigen, wie das Setup-Projekt zu konfigurieren.  
  
> [!IMPORTANT]
>  Stellen Sie sicher, dass Sie mindestens einmal die Releasekonfiguration des Ihrer isolierten Shell-Projekt erstellt haben, bevor Sie das Setup-Projekt konfigurieren.  
  
#### <a name="to-configure-the-setup-project"></a>So konfigurieren Sie das Setup-Projekt  
  
1.  In der **Projektmappen-Explorer**unter der **MySetup** Projekts **Projekt-Assistent**. In der unteren Zeile mit der **Projekt-Assistent** Fenster wählen **Anwendungsinformationen**. Geben Sie **Fabrikam** als den Namen Ihres Unternehmens und **Fabrikam Musik Editor** als den Namen Ihrer Anwendung. Wählen Sie den Vorwärtspfeil unten rechts auf der die **Projekt-Assistent**.  
  
2.  Wählen Sie **Ja** unter **benötigt Ihre Anwendung keine Software auf dem Computer installiert werden?** und wählen Sie dann **vollständige Microsoft .NET Framework 4.5-Paket**.  
  
3.  Wählen Sie die **Anwendungsdateien** Schaltfläche am unteren Rand des Fensters, und stellen Sie sicher, dass die **Fabrikam Musik Editor** Ordner ausgewählt ist.  
  
4.  Wählen Sie die **Hinzufügen von Dateien** Schaltfläche. In der **Hinzufügen von Dateien** Dialogfeld hinzu, und die folgenden Dateien aus dem **MyVSShellStub\Release** Ordner:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  "Debuggerproxy.dll"  
  
    3.  "Debuggerproxy.dll.manifest" wurden  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Klicken Sie auf die **Projektausgaben hinzufügen** Schaltfläche, und fügen **MyVSShellStub oder primäre Ausgabe**. Klicken Sie auf **OK**.  
  
6.  Im linken Bereich unter **Zielcomputer**, mit der rechten Maustaste die **Fabrikam-Musik-Editor [INSTALLDIR]** Knoten und Hinzufügen einer **neuer Ordner** mit dem Namen **Erweiterungen** .  
  
7.  Mit der rechten Maustaste die **Erweiterungen** im linken Bereich den Knoten, und fügen Sie einen neuen Ordner namens **Anwendung**.  
  
8.  Wählen Sie die **Anwendung** Ordner, und klicken Sie auf die **Projektausgaben hinzufügen** und dann auf die primäre Ausgabe aus dem MyVSShellStub.AboutBoxPackage-Projekt.  
  
9. Klicken Sie auf die **Hinzufügen von Dateien** Schaltfläche, und fügen Sie die folgenden Dateien aus dem Ordner \MyVSShellStub\Release\Extensions\Application\ hinzu:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Mit der rechten Maustaste die **Fabrikam-Musik-Editor [INSTALLDIR]** im linken Bereich den Knoten, und fügen Sie einen neuen Ordner namens **1033**.  
  
11. Wählen Sie den Ordner "1033" aus, und klicken Sie dann auf die **Projektausgaben hinzufügen** Schaltfläche, und wählen Sie die primäre Ausgabe aus dem MyVSShellStubUI-Projekt.  
  
12. Verschieben Sie in der **Anwendungsverknüpfungen** Fenster.  
  
13. Klicken Sie auf **neu** erstellen Sie eine Verknüpfung, und wählen Sie **[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**.  
  
14. Verschieben Sie in der **Installationsinterview** Bereich.  
  
15. Legen Sie alle Elemente auf **keine**.  
  
16. In **Projektmappen-Explorer**, öffnen Sie im Projekt MySetup **definieren Installationsanforderungen und Aktionen \ Anforderungen**. Die **Anforderungen** Fenster wird geöffnet.  
  
17. Klicken Sie mit der rechten Maustaste auf **Software Systemanforderungen** , und wählen Sie **erstellen neue Startbedingung**. Die **Assistenten von System Search** angezeigt wird.  
  
18. In der **Was möchten Sie suchen?** Bereich wählen **Registrierungseintrag** in der Dropdown-Liste und klicken Sie auf **Weiter**.  
  
19. In der **wie möchten Sie danach suchen?** wählen Sie im Bereich **HKEY_LOCAL_MACHINE** als den Registrierungsstamm. Geben Sie **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** für 64-Bit-Systeme oder **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** für 32-Bit-Systeme, und geben Sie  **Installieren Sie** als Wert des Registrierungsschlüssels. Klicken Sie auf **Weiter**.  
  
20. In der **Was möchten Sie Sie mit dem Wert?** Bereich eingeben **dieses Produkt muss Visual Studio 2015 Isolated Shell Redistributable installiert werden.** als Anzeigetext und auf **Fertig stellen**.  
  
21. Neu erstellen Sie, die isolierte Shell-Lösung, um das Setupprojekt zu erstellen.  
  
     Sie finden die setup.exe-Datei im folgenden Ordner:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Testen das Installationsprogramm  
 Um das Setup zu testen, kopieren Sie die setup.exe-Datei auf einen anderen Computer aus, und führen Sie die Setup-Datei. Sie sollten die isolated Shell-Anwendung ausführen können.

