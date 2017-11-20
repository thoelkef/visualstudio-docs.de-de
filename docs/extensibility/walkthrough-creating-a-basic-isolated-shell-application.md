---
redirect_url: shell/walkthrough-creating-a-basic-isolated-shell-application
title: 'Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: "54"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4df0d9f772d92ac7f1f106b9befc0a8a2f89a22
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Exemplarische Vorgehensweise: Erstellen einer grundlegenden Isolated Shell-Anwendung
Diese exemplarische Vorgehensweise zeigt, wie eine isolierte Shell-Lösung erstellen, Anpassen des Toolfensters Info und ein Setupprogramm erstellen, die die isolierte Shell installiert.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Um die isolierte Shell bereitstellen zu können, müssen Sie auch das Visual Studio Shell (isoliert) Redistributable Package verwenden.  
  
## <a name="creating-an-isolated-shell-solution"></a>Erstellen einer isolierten Shell-Lösung  
 In diesem Abschnitt wird gezeigt, wie die Visual Studio Shell Isolated Projektvorlage zum Erstellen einer isolierten Shell-Lösung verwenden. Die Lösung enthält die folgenden Projekte:  
  
-   Die *SolutionName*. AboutBoxPackage-Projekt, dem Sie die Darstellung der Hilfe/Informationsfeld anpassen kann.  
  
-   Das ShellExtensionsVSIX-Projekt, das die Datei "Source.Extension.vsixmanifest" enthält, die die verschiedenen Komponenten von isolierten Shell-Anwendung definiert.  
  
-   Die *SolutionName* Projekt, in dem die ausführbare Datei erzeugt, die die isolierte Shell-Anwendung aufruft. Dieses Projekt enthält die Anpassung der Shell-Ordners, der Ihnen anpassn die Darstellung und das Verhalten des isolierten Shell-Anwendung ermöglicht.  
  
-   Die *SolutionName* Benutzeroberflächenprojekts, der eine Satellitenassembly erzeugt, die Befehle im Menü aktiv und lokalisierbaren Zeichenfolgen definiert.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Erstellen eine grundlegenden isolierte Shell-Lösung  
  
1.  Öffnen Sie Visual Studio, und erstellen Sie ein neues Projekt.  
  
2.  In der **neues Projekt** Fenster, erweitern Sie **andere Projekttypen** und dann **Erweiterbarkeit**. Wählen Sie die **Visual Studio Shell Isolated** -Projektvorlage.  
  
3.  Nennen Sie das Projekt `MyVSShellStub` und Speicherort angeben. Stellen Sie sicher, dass **Projektmappenverzeichnis erstellen** aktiviert ist, und klicken Sie dann auf **OK**.  
  
     Die neue Projektmappe wird in **Projektmappen-Explorer**.  
  
4.  Erstellen Sie die Projektmappe, und starten Sie das Debuggen von isolierten Shell-Anwendung.  
  
     Die Visual Studio isolated Shell wird angezeigt. Liest die Titelleiste **MyVSShellStub**. Das Symbol "Leiste Titel" wird aus \MyVSShellStub\Resource Files\ApplicationIcon.ico generiert.  
  
## <a name="customizing-the-application-name-and-icon"></a>Anpassen der Anwendungsname und das Symbol "  
 Möglicherweise möchten Ihre Anwendung mit den Namen Ihres Unternehmens und das Logo in der Titelleiste Branding versehen. Die folgenden Schritte zeigen, wie so ändern Sie den Namen und das Symbol ", die in der Titelleiste der benutzerdefinierten Anwendung angezeigt werden, indem Sie die Paketdefinitionsdatei MyVSShellStub.Application.pkgdef ändern.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Zum Anpassen der Anwendungsname und das Symbol "  
  
1.  Öffnen Sie im Projekt MyVSShellStub \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2.  Ändern der `AppName` Elementwert, **"AppName" = "Fabrikam Musik-Editor"**  
  
3.  Um das Symbol "Anwendung" zu ändern, kopieren Sie ein anderes Symbol in das Verzeichnis \MyVSShellStub\MyVSShellStub\MyVSShellStub\. Benennen Sie die vorhandene ApplicationIcon.ico-Datei in ApplicationIcon1.ico. Benennen Sie die neue Datei in ApplicationIcon.ico.  
  
4.  Erstellen Sie die Lösung und beginnen Sie mit dem Debuggen. Isolierte Shell wird die IDE angezeigt. Die Titelleiste wurde das neue Symbol neben den Wörtern **Fabrikam Musik Editor**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Anpassen der standardmäßig Web-Browser-Startseite  
 In diesem Abschnitt wird gezeigt, wie die Standardstartseite der Ändern der **Webbrowser** Fenster durch Ändern der Paketdefinitionsdatei.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Die Standardstartseite im Webbrowser anpassen  
  
1.  Ändern Sie in der Datei MyVSShellStub.Application.pkgdef die `DefaultHomePage` Elementwert, der "http://www.microsoft.com".  
  
2.  Das MyVSShellStub-Projekt neu.  
  
3.  Erstellen Sie die Lösung und beginnen Sie mit dem Debuggen.  
  
4.  In **Ansicht / Weitere Fenster**, klicken Sie auf **Webbrowser**. Die **Webbrowser** Fenster zeigt die Startseite "Microsoft Corporation".  
  
## <a name="removing-the-print-command"></a>Entfernen den Befehl Print  
 Die VSCT-Datei in einem isolierten Shell-UI-Projekt besteht aus einem Satz von Deklarationen des Formulars `<Define name=No_` *Element*`>`, wobei *Element* ist der standardmäßige Visual Studio-Menüs und Befehle.  
  
 Wenn eine Deklaration keine Kommentierung aufweist, ist das Menü oder einen Befehl vom isolierte Shell ausgeschlossen. Umgekehrt, wenn eine Deklaration Kommentarzeichen deaktiviert ist, ist das Menü oder den Befehl in der isolierten Shell enthalten.  
  
 Kommentieren Sie in den folgenden Schritten Druckbefehl in der VSCT-Datei aus.  
  
#### <a name="to-remove-the-print-command"></a>So entfernen Sie den Befehl print  
  
1.  Überprüfen Sie, ob die **Drucken** -Befehl angezeigt wird, auf die **Datei** Menü in der isolierten shellanwendung.  
  
2.  Öffnen Sie im Projekt MyVSShellStubUI \Resource Files\MyVSShellStubUI.vsct für die Bearbeitung aus.  
  
3.  Die kommentarmarkierung dieser Zeile aufheben:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Dadurch wird der Druckbefehl entfernt.  
  
5.  Starten Sie das Debuggen von isolierten Shell-Anwendung. Überprüfen Sie, ob die **Datei / drucken** Befehl ist nicht mehr vorhanden.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Entfernen von Funktionen aus der isolierte Shell  
 Sie können einige der Pakete entfernen, die mit Visual Studio geladen werden, durch Bearbeiten der .pkgundef-Datei aus, wenn Sie nicht über diese Funktionen in der benutzerdefinierten isolierten shellanwendung möchten. Sie können das Paket in einem der Unterschlüssel des Registrierungsschlüssels für $RootKey$ \Packages angeben.  
  
> [!NOTE]
>  Die GUIDs von Visual Studio-Funktionen finden Sie unter [Paket-GUIDs von Visual Studio-Funktionen](../extensibility/package-guids-of-visual-studio-features.md).  
  
 Das folgende Verfahren zeigt, wie So entfernen Sie den XML-Code-Editor über isolierte Shell.  
  
#### <a name="to-remove-the-xml-editor"></a>So entfernen Sie die XML-editor  
  
1.  Öffnen Sie die MyVSShellStub.pkgundef-Datei im Ordner "Shell-Anpassung" des Projekts MyVSShellStub.  
  
2.  Kommentieren Sie die folgende Zeile:  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  Erstellen Sie die Projektmappe neu und Debuggen Sie isolierte Shell. Öffnen Sie eine XML-Datei, z. B. \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Stellen Sie sicher, dass die XML-Schlüsselwörter in der Datei nicht farbig hervorgehoben sind und diese Folgendes eingeben: "<" in einer Zeile bringt nicht XML-QuickInfos.  
  
## <a name="customizing-the-helpabout-box"></a>Anpassen der Hilfe/Informationsfeld  
 Sie können anpassen, die Hilfe/Informationsfeld, die als Teil der isolierte Shell-Projektvorlage erstellt wird.  
  
#### <a name="to-customize-the-company-name"></a>Zum Anpassen des Namens des Unternehmens  
  
1.  Den Firmennamen, die copyright-Informationen, die Produktversion und die produktbeschreibung sind in der Datei \Properties\AssemblyInfo.cs MyVSShellStub.AboutBoxPackage im Projekt gefunden. Öffnen Sie diese Datei.  
  
2.  Ändern der `AssemblyCompany` Wert **Fabrikam**, die `AssemblyProduct` und `AssemblyTitle` Werte **Fabrikam Musik Editor**, und die `AssemblyCopyright` Wert **Copyright © Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")]  
    ```  
  
3.  Ändern Sie zum Hinzufügen einer Beschreibung des Produkts der `AssemblyDescription` Wert **die Beschreibung des Editors für Fabrikam Musik.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.")]  
    ```  
  
4.  Mit dem Debuggen beginnen, und öffnen Sie in der isolierten Shell-Anwendung, die **Hilfe / ca.** Feld. Die geänderten Zeichenfolgen sollte angezeigt werden. Der Titel, der die Hilfe/Informationsfeld ist identisch mit der `AssemblyTitle` Wert in der Datei "AssemblyInfo.cs".  
  
5.  Die Eigenschaften der **Hilfe/zu** Box selbst sind in der Datei MyVSShellStub.AboutBoxPackage\AboutBox.xaml gefunden. Um die Breite der Hilfe/Informationsfeld zu ändern, wechseln Sie zu der `AboutDialogStyle` blockieren, und legen Sie die `Width` Eigenschaft auf 200:  
  
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
  
6.  Erstellen Sie die Projektmappe neu und Debuggen Sie isolierte Shell. Die Hilfe/Informationsfeld sollte ungefähr Quadrat.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Bevor Sie die isolierten Shell-Anwendung bereitstellen  
 Die isolierte Shell-Anwendung kann auf jedem Computer installiert werden, die das Visual Studio Shell (isoliert) Redistributable Package wurde. Weitere Informationen über das redistributable Package finden Sie unter der [Visual Studio-Erweiterbarkeit Downloads](http://go.microsoft.com/fwlink/?LinkID=119298) Website.  
  
## <a name="deploying-the-isolated-shell-application"></a>Bereitstellen der Anwendung isolierte Shell  
 Sie bereitstellen Ihre isolierten Shell-Anwendung auf einem Zielcomputer durch das Erstellen eines Setup-Projekts. Sie müssen Folgendes angeben:  
  
-   Das Layout der Ordner und Dateien auf dem Zielcomputer installiert.  
  
-   Die Startbedingungen, die garantieren, dass .NET Framework und Visual Studio-Laufzeit Shell werden auf dem Zielcomputer installiert.  
  
 Im folgenden Verfahren müssen Sie die InstallShield Limited Edition auf Ihrem Computer zu installieren.  
  
#### <a name="to-create-the-setup-project"></a>Zum Erstellen des Setupprojekts  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektmappenknoten, und klicken Sie dann auf **neues Projekt hinzufügen**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie **andere Projekttypen** und wählen Sie dann **Setup und Bereitstellung**. Wählen Sie die InstallShield-Vorlage. Nennen Sie das neue Projekt `MySetup` , und klicken Sie dann auf **OK**.  
  
3.  Wenn InstallShield Limited Edition bereits installiert ist, fahren Sie mit dem nächsten Schritt fort.  
  
     Wenn InstallShield Limited Edition nicht bereits installiert ist, wird Sie die InstallShield-Downloadseite angezeigt. Führen Sie die Anweisungen zum Herunterladen und installieren Sie das Produkt, die Version des InstallShield, die kompatibel mit Ihrer Version von Visual Studio auswählen. Sie müssen entscheiden, ob Sie registrieren Ihre Installation von InstallShield oder verwenden sie eine Evaluierungsversion. Sie müssen Visual Studio neu starten, nachdem Sie die Installation abzuschließen.  
  
    > [!IMPORTANT]
    >  Sie müssen Visual Studio als Administrator starten, bevor Sie die InstallShield-Projekts erstellen. Wenn Sie dies tun, erhalten Sie einen Fehler, wenn Sie das Projekt erstellen.  
  
 Die nächsten Schritte zeigen, wie das Setupprojekt konfigurieren.  
  
> [!IMPORTANT]
>  Stellen Sie sicher, dass Sie mindestens einmal die Releasekonfiguration des Projekts isolierte Shell erstellt haben, bevor Sie das Setup-Projekt konfigurieren.  
  
#### <a name="to-configure-the-setup-project"></a>So konfigurieren Sie das Setup-Projekt  
  
1.  In der **Projektmappen-Explorer**unter der **MySetup** Projekts **Projekt-Assistent**. Auf der untersten Zeile der **Projekt-Assistent** Fenster, wählen Sie **Anwendungsinformationen**. Geben Sie **Fabrikam** als den Namen Ihres Unternehmens und **Fabrikam Musik Editor** als Name Ihrer Anwendung. Wählen Sie den Vorwärtspfeil am unten rechts auf der die **Projekt-Assistent**.  
  
2.  Wählen Sie **Ja** unter **erfordert die Anwendung keine Software auf dem Computer installiert werden?** und wählen Sie dann **vollständige Microsoft .NET Framework 4.5-Paket**.  
  
3.  Wählen Sie die **Anwendungsdateien** Schaltfläche am unteren Rand des Fensters, und stellen Sie sicher, dass die **Fabrikam Musik Editor** Ordner ausgewählt ist.  
  
4.  Wählen Sie die **Hinzufügen von Dateien** Schaltfläche. In der **Hinzufügen von Dateien** Dialogfeld hinzu, und die folgenden Dateien aus dem **MyVSShellStub\Release** Ordner:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Klicken Sie auf die **Projektausgaben hinzufügen** Schaltfläche, und fügen **MyVSShellStub/primäre Ausgabe**. Klicken Sie auf **OK**.  
  
6.  Im linken Bereich unter **Zielcomputer**, mit der rechten Maustaste die **Fabrikam Musik-Editor [INSTALLDIR]** Knoten und Hinzufügen einer **neuer Ordner** mit dem Namen **Erweiterungen**.  
  
7.  Mit der rechten Maustaste die **Erweiterungen** im linken Bereich den Knoten, und fügen Sie einen neuen Ordner namens **Anwendung**.  
  
8.  Wählen Sie die **Anwendung** Ordner, und klicken Sie auf die **Projektausgaben hinzufügen** Schaltfläche, und wählen Sie die primäre Ausgabe aus dem MyVSShellStub.AboutBoxPackage-Projekt.  
  
9. Klicken Sie auf die **Hinzufügen von Dateien** Schaltfläche, und fügen Sie die folgenden Dateien aus dem Ordner \MyVSShellStub\Release\Extensions\Application\ hinzu:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Mit der rechten Maustaste die **Fabrikam Musik-Editor [INSTALLDIR]** im linken Bereich den Knoten, und fügen Sie einen neuen Ordner namens **1033**.  
  
11. Wählen Sie den Ordner 1033, und klicken Sie dann auf die **Projektausgaben hinzufügen** Schaltfläche, und wählen Sie die primäre Ausgabe aus dem MyVSShellStubUI-Projekt.  
  
12. Zum Verschieben der **Anwendungsverknüpfungen** Fenster.  
  
13. Klicken Sie auf **neu** erstellen Sie eine Verknüpfung, und wählen Sie **[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**.  
  
14. Zum Verschieben der **Installationsinterview** Bereich.  
  
15. Legen Sie alle Elemente auf **keine**.  
  
16. In **Projektmappen-Explorer**, öffnen Sie im Projekt MySetup **definieren Installationsanforderungen und Aktionen \ Anforderungen**. Die **Anforderungen** Fenster wird geöffnet.  
  
17. Klicken Sie mit der rechten Maustaste auf **System Softwareanforderungen** , und wählen Sie **erstellen neue Startbedingung**. Die **-Assistent für System Suche** angezeigt wird.  
  
18. In der **Was möchten Sie suchen?** Bereich auswählen **Registrierungseintrag** in der Dropdown-Liste und klicken Sie auf **Weiter**.  
  
19. In der **wie möchten Sie danach suchen?** klicken Sie im Bereich **HKEY_LOCAL_MACHINE** als den Registrierungsstamm. Geben Sie **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** für 64-Bit-Systemen oder **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** für 32-Bit-Systeme, und geben Sie **installieren** als der Registrierungswert "". Klicken Sie auf **Weiter**.  
  
20. In der **Was möchten Sie mit dem Wert tun?** Bereich, geben Sie **dieses Produkts erfordert Visual Studio 2015 Isolated Shell Redistributable installiert werden.** als Anzeigetext und auf **Fertig stellen**.  
  
21. Neu erstellen Sie, die isolierte Shell-Lösung, um das Setupprojekt zu erstellen.  
  
     Sie finden die Datei setup.exe im folgenden Ordner:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Testen das Installationsprogramm  
 Um das Setup zu testen, kopieren Sie die Datei setup.exe auf einen anderen Computer, und führen Sie das Setup ausführbare Datei. Sie sollten die isolierte Shell-Anwendung ausgeführt werden können.