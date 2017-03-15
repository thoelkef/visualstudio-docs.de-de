---
title: "Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierte Shell | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio-Shell, exemplarische Vorgehensweisen"
  - "Exemplarische Vorgehensweisen-Shell [Visual Studio]"
  - "Exemplarische Vorgehensweisen [Visual Studio], isolierte Shell-basierten Anwendung"
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 54
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 54
---
# Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierte Shell
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieser exemplarischen Vorgehensweise erstellen eine isolierte Shell\-Lösung, das Toolfenster Info anpassen und erstellen ein Setupprogramm, die isolierte Shell installiert.  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise ausführen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Um die isolierte Shell bereitzustellen, müssen Sie auch das Visual Studio\-Shell \(isoliert\) Redistributable Package verwenden.  
  
## Erstellen eine isolierte Shell\-Lösung  
 Dieser Abschnitt zeigt, wie die Visual Studio Shell Isolated Projektvorlage zum Erstellen einer Projektmappe isolierte Shell verwenden. Die Lösung enthält die folgenden Projekte:  
  
-   Die *SolutionName*. AboutBoxPackage\-Projekt, können Sie zum Anpassen der Darstellung der Hilfe\/Info\-Dialogfeld.  
  
-   Das ShellExtensionsVSIX\-Projekt, das die Datei "Source.Extension.vsixmanifest" enthält, die die verschiedenen Komponenten der Anwendung für isolierte Shells definiert.  
  
-   Die *SolutionName* \-Projekt, das die ausführbare Datei erzeugt, die die isolierte Shell\-Anwendung aufruft. Dieses Projekt enthält den Ordner Shell Anpassung Sie anpassn das Aussehen und Verhalten der Anwendung für isolierte Shells kann.  
  
-   Die *SolutionName* UI\-Projekt, der eine Satellitenassembly erstellt, die Befehle im Menü aktiv und lokalisierbare Zeichenfolgen definiert.  
  
#### Zum Erstellen einer grundlegenden isolierte Shell\-Lösung  
  
1.  Öffnen Sie Visual Studio, und erstellen Sie ein neues Projekt.  
  
2.  In der **Neues Projekt** Fenster, erweitern Sie **Andere Projekttypen** und **Erweiterbarkeit**. Wählen Sie die **Visual Studio Shell Isolated** \-Projektvorlage.  
  
3.  Nennen Sie das Projekt `MyVSShellStub` und einen Speicherort angeben. Stellen Sie sicher, dass **Projektmappenverzeichnis erstellen** aktiviert ist, und klicken Sie dann auf **OK**.  
  
     Die neue Projektmappe wird in **Projektmappen\-Explorer**.  
  
4.  Erstellen Sie die Projektmappe, und starten Sie das Debuggen der Anwendung für isolierte Shells.  
  
     Visual Studio isolated Shell wird angezeigt. Die Titelleiste lautet **MyVSShellStub**. Das Titelleistensymbol \\MyVSShellStub\\Resource Files\\ApplicationIcon.ico erzeugt.  
  
## Anpassen der Anwendungsname und Symbol  
 Möglicherweise möchten Ihre Anwendung mit den Namen Ihres Unternehmens und das Logo in der Titelleiste der Marke. Die folgenden Schritte zeigen, wie so ändern Sie den Namen und das Symbol, die in der Titelleiste der benutzerdefinierten Anwendung angezeigt werden, indem Sie die Paketdefinitionsdatei MyVSShellStub.Application.pkgdef ändern.  
  
#### Zum Anpassen der Anwendungsname und Symbol  
  
1.  Öffnen Sie im Projekt MyVSShellStub \\Shell Customization\\MyVSShellStub.Application.pkgdef.  
  
2.  Ändern der `AppName` Elementwert zu **"AppName" \= "Fabrikam\-Musik\-Editor"**  
  
3.  Um das Anwendungssymbol zu ändern, kopieren Sie ein anderes Symbol in das Verzeichnis \\MyVSShellStub\\MyVSShellStub\\MyVSShellStub\\. Benennen Sie die vorhandene ApplicationIcon.ico\-Datei in ApplicationIcon1.ico. Benennen Sie die neue Datei in ApplicationIcon.ico.  
  
4.  Erstellen Sie die Projektmappe, und starten Sie das Debuggen. Isolierte Shell wird die IDE angezeigt. Die Titelleiste verfügt das neue Symbol neben den Wörtern **Fabrikam Musik Editor**.  
  
## Anpassen der standardmäßige Web\-Browser\-Homepage  
 In diesem Abschnitt wird gezeigt, wie die Standardhomepage der Ändern der **Webbrowser** Fenster durch Ändern der Paketdefinitionsdatei.  
  
#### Anpassen des Standard\-Webbrowser\-Startseite  
  
1.  Ändern Sie in der Datei MyVSShellStub.Application.pkgdef die `DefaultHomePage` Wert des Elements auf "http:\/\/www.microsoft.com".  
  
2.  Das MyVSShellStub\-Projekt neu.  
  
3.  Erstellen Sie die Projektmappe, und starten Sie das Debuggen.  
  
4.  In **Anzeigen \/ andere Fenster**, klicken Sie auf **Webbrowser**. Die **Webbrowser** Fenster zeigt die Startseite der Microsoft Corporation.  
  
## Entfernen den Druckbefehl  
 Die VSCT\-Datei in eine isolierte Shell UI\-Projekt besteht aus einem Satz von Deklarationen der Form `<Define name=No_`*Element*`>`, wobei *Element* ist der standardmäßige Visual Studio\-Menüs und Befehle.  
  
 Wenn eine Deklaration unkommentierten ist, wird das Menü oder den Befehl über die isolierte Shell ausgeschlossen. Umgekehrt, wenn eine Deklaration kommentiert wird, ist das Menü oder den Befehl in der isolierte Shell enthalten.  
  
 In den folgenden Schritten kommentieren Sie Druckbefehl in der VSCT\-Datei.  
  
#### So entfernen Sie den Druckbefehl  
  
1.  Überprüfen Sie, ob die **Drucken** Befehl angezeigt wird, auf die **Datei** Menü in der isolierte Shell\-Anwendung.  
  
2.  Öffnen Sie im Projekt MyVSShellStubUI \\Resource Files\\MyVSShellStubUI.vsct zur Bearbeitung aus.  
  
3.  Kommentieren Sie diese Zeile:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Dadurch wird den Druckbefehl entfernt.  
  
5.  Debuggen Sie die Anwendung für isolierte Shells. Überprüfen Sie, ob die **Datei \/ Druck** Befehl ist nicht mehr vorhanden.  
  
## Entfernen von Funktionen aus der isolierte Shell  
 Sie können einige der Pakete entfernen, die mit Visual Studio geladen werden, die .pkgundef\-Datei bearbeiten, wenn Sie nicht über diese Funktionen in Ihrer Anwendung benutzerdefinierte isolierte Shell möchten. Das Paket angeben in einem der Unterschlüssel des Registrierungsschlüssels für $RootKey$ \\Packages.  
  
> [!NOTE]
>  Die GUIDs von Visual Studio\-Features finden Sie unter [Paket\-GUIDs der Visual Studio\-Funktionen](../extensibility/package-guids-of-visual-studio-features.md).  
  
 Das folgende Verfahren zeigt, wie So entfernen Sie den XML\-Code\-Editor über die isolierte Shell.  
  
#### So entfernen Sie den XML\-editor  
  
1.  Öffnen Sie die MyVSShellStub.pkgundef\-Datei im Ordner Shell Anpassung des Projekts MyVSShellStub.  
  
2.  Kommentieren Sie die folgende Zeile:  
  
     \[$RootKey$ \\Packages\\ {87569308\-4813\-40a0\-9cd0\-d7a30838ca3f}\]  
  
3.  Erstellen Sie die Lösung Debuggen und die isolierte Shell. Öffnen Sie eine XML\-Datei, z. B. \\MyVSShellStub\\MyVSShellStub\\MyVSShellStubUI\\MyVSShellStubUI.vsct. Stellen Sie sicher, dass die XML\-Schlüsselwörter in der Datei nicht farbig hervorgehoben werden und, geben Sie "\<" in einer Zeile bringt nicht XML\-QuickInfos.  
  
## Anpassen der Hilfe\/Info\-Dialogfeld  
 Sie können anpassen, die Hilfe\/Info\-Feld, das als Teil der isolierte Shell\-Projektvorlage erstellt wird.  
  
#### Der Firmenname anpassen  
  
1.  Der Firmenname, copyright\-Informationen, Produktversion und Produkt sind in der Datei \\Properties\\AssemblyInfo.cs MyVSShellStub.AboutBoxPackage im Projekt gefunden. Öffnen Sie diese Datei.  
  
2.  Ändern der `AssemblyCompany` \-Wert **Fabrikam**, die `AssemblyProduct` und `AssemblyTitle` Werte **Fabrikam Musik Editor**, und die `AssemblyCopyright` Wert **Copyright © Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")] [assembly: AssemblyDescription("")] [assembly: AssemblyConfiguration("")] [assembly: AssemblyCompany("Fabrikam")] [assembly: AssemblyProduct("Fabrikam Music Editor")] [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")] [assembly: AssemblyProduct("Fabrikam Music Editor ")] [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  Um eine Beschreibung des Produkts hinzuzufügen, ändern Sie die `AssemblyDescription` Wert **die Beschreibung der Fabrikam\-Musik\-Editor.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  Starten Sie das Debuggen, und öffnen Sie in der Anwendung isolierte Shell der **Hilfe \/ zu** Feld. Die geänderten Zeichenfolgen sollte angezeigt werden. Der Titel der Hilfe\/Info\-Dialogfeld ist identisch mit der `AssemblyTitle` Wert in der Datei "AssemblyInfo.cs".  
  
5.  Die Eigenschaften der **Hilfe\/Info** kann in der Datei MyVSShellStub.AboutBoxPackage\\AboutBox.xaml gefunden werden. Um die Breite der Hilfe\/Info\-Feld zu ändern, rufen Sie die `AboutDialogStyle` blockieren, und legen Sie die `Width` Eigenschaft auf 200:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window"> <Setter Property="Height" Value="Auto" /> <Setter Property="Width" Value="200" /> <Setter Property="ShowInTaskbar" Value="False" /> <Setter Property="ResizeMode" Value="NoResize" /> <Setter Property="WindowStyle" Value="SingleBorderWindow" /> <Setter Property="SizeToContent" Value="Height" /> </Style>  
    ```  
  
6.  Erstellen Sie die Lösung Debuggen und die isolierte Shell. Die Hilfe\/Info\-Dialogfeld sollte etwa Quadrat.  
  
## Bevor Sie die isolierte Shell\-Anwendung bereitstellen  
 Die isolierte Shell\-Anwendung kann auf jedem Computer installiert werden, die das Visual Studio\-Shell \(isoliert\) Redistributable Package aufweist. Weitere Informationen über das verteilbare Paket finden Sie unter der [Downloads zu Visual Studio\-Erweiterbarkeit](http://go.microsoft.com/fwlink/?LinkID=119298) Website.  
  
## Bereitstellen der Anwendung isolierte Shell  
 Sie haben die isolierte Shell\-Anwendung auf einem Zielcomputer durch das Erstellen eines Setup\-Projekts bereitstellen. Sie müssen Folgendes angeben:  
  
-   Das Layout der Ordner und Dateien auf dem Zielcomputer.  
  
-   Die Startbedingungen, die sicherstellen, dass .NET Framework und Visual Studio\-Laufzeit Shell, die auf dem Zielcomputer installiert sind.  
  
 Im folgenden Verfahren müssen Sie InstallShield Limited Edition auf Ihrem Computer zu installieren.  
  
#### Das Setup\-Projekt erstellen  
  
1.  In **Projektmappen\-Explorer**, mit der rechten Maustaste auf den Projektmappenknoten, und klicken Sie dann auf **Neues Projekt hinzufügen**.  
  
2.  In der **Neues Projekt** Dialogfeld erweitern Sie **Andere Projekttypen** und wählen Sie dann **Setup und Bereitstellung**. Wählen Sie die InstallShield\-Vorlage. Nennen Sie das neue Projekt `MySetup` und klicken Sie dann auf **OK**.  
  
3.  Wenn InstallShield Limited Edition bereits installiert ist, fahren Sie mit dem nächsten Schritt fort.  
  
     Wenn der InstallShield Limited Edition nicht bereits installiert ist, wird die InstallShield\-Download\-Seite angezeigt. Befolgen Sie die Anweisungen zum Herunterladen und installieren Sie das Produkt, und wählen Sie die Version der InstallShield, die mit Ihrer Version von Visual Studio kompatibel ist. Sie müssen entscheiden, ob Ihre Installation von InstallShield registrieren oder als Evaluierungsversion verwenden. Sie müssen Visual Studio nach Abschluss der Installation neu starten.  
  
    > [!IMPORTANT]
    >  Sie müssen Visual Studio als Administrator starten, bevor Sie ein InstallShield\-Projekt erstellen. Wenn Sie dies tun, erhalten Sie Fehler, wenn Sie das Projekt erstellen.  
  
 Die nächsten Schritte zeigen, wie das Setup\-Projekt zu konfigurieren.  
  
> [!IMPORTANT]
>  Stellen Sie sicher, dass Sie mindestens einmal die Releasekonfiguration des Projekts isolierte Shell erstellt haben, bevor Sie das Setup\-Projekt konfigurieren.  
  
#### So konfigurieren Sie das Setup\-Projekt  
  
1.  In der **Projektmappen\-Explorer**, unter der **MySetup** Projekt, wählen Sie **Projekt\-Assistent**. Auf der untersten Zeile der **Projekt\-Assistent** Fenster Wählen Sie **Anwendungsinformationen**. Geben Sie **Fabrikam** als den Namen Ihres Unternehmens und **Fabrikam Musik Editor** als Name Ihrer Anwendung. Wählen Sie den weiter\-Pfeil unten rechts in der **Projekt\-Assistent**.  
  
2.  Wählen Sie **Ja** unter **benötigt Ihre Anwendung Software auf dem Computer installiert werden?** und wählen Sie dann **vollständige Microsoft .NET Framework 4.5\-Paket**.  
  
3.  Wählen Sie die **Anwendungsdateien** Schaltfläche am unteren Rand des Fensters, und stellen Sie sicher, dass die **Fabrikam Musik Editor** Ordner ausgewählt ist.  
  
4.  Wählen Sie die **Dateien hinzufügen** Schaltfläche. In der **Dateien hinzufügen** Dialogfeld fügen die folgenden Dateien aus dem **MyVSShellStub\\Release** Ordner:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Klicken Sie auf die **Projektausgaben hinzufügen** Schaltfläche, und fügen **MyVSShellStub oder primäre Ausgabe**. Klicken Sie auf **OK**.  
  
6.  Im linken Bereich unter **Zielcomputer**, mit der rechten Maustaste die **Fabrikam\-Musik\-Editor \[INSTALLDIR\]** Knoten und Hinzufügen einer **neuen Ordner** mit dem Namen **Extensions**.  
  
7.  Mit der rechten Maustaste die **Extensions** im linken Bereich den Knoten, und fügen Sie einen neuen Ordner namens **Anwendung**.  
  
8.  Wählen Sie die **Anwendung** Ordner und klicken Sie auf die **Projektausgaben hinzufügen** Schaltfläche, und wählen Sie die primäre Ausgabe aus dem MyVSShellStub.AboutBoxPackage\-Projekt.  
  
9. Klicken Sie auf die **Dateien hinzufügen** Schaltfläche, und fügen Sie die folgenden Dateien aus dem Ordner \\MyVSShellStub\\Release\\Extensions\\Application\\ hinzu:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Mit der rechten Maustaste die **Fabrikam\-Musik\-Editor \[INSTALLDIR\]** im linken Bereich den Knoten, und fügen Sie einen neuen Ordner namens **1033**.  
  
11. Wählen Sie den Ordner 1033, und klicken Sie dann auf die **Projektausgaben hinzufügen** und wählen Sie die primäre Ausgabe aus dem MyVSShellStubUI\-Projekt.  
  
12. Verschieben Sie in der **Anwendungsverknüpfungen** Fenster.  
  
13. Klicken Sie auf **Neu** eine Verknüpfung erstellen, und wählen Sie **\[ProgramFilesFolder\] \\Fabrikam\\Fabrikam Music Editor\\MyVSShellStub.Primary Output**.  
  
14. Verschieben Sie in der **Installationsinterview** Bereich.  
  
15. Legen Sie alle Elemente auf **Nr.**.  
  
16. In **Projektmappen\-Explorer**, öffnen Sie das Projekt MySetup **Installationsanforderungen definieren und Aktionen \\ Anforderungen**. Die **Anforderungen** wird geöffnet.  
  
17. Klicken Sie mit der rechten Maustaste auf **System Software Requirements** und wählen Sie **erstellen neue Startbedingung**. Die **System Suche Assistenten** angezeigt wird.  
  
18. In der **Was möchten Sie suchen?** Bereich wählen **Registrierungseintrag** in der Dropdown\-Liste und klicken Sie auf **Weiter**.  
  
19. In der **Wie möchten Sie danach suchen?** aus **HKEY\_LOCAL\_MACHINE** als der Registrierungsstamm. Geben Sie **SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell** für 64\-Bit\-Systemen oder **SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell** für 32\-Bit\-Systeme, und geben Sie **Installieren** als Wert des Registrierungsschlüssels. Klicken Sie auf **Weiter**.  
  
20. In der **Was möchten Sie mit dem Wert tun?** Bereich geben Sie **dieses Produkt erfordert Visual Studio 2015 isolierte Shell Redistributable installiert werden.** als Anzeigetext und auf **Fertig stellen**.  
  
21. Erstellen Sie die isolierte Shell\-Lösung, um das Setup\-Projekt zu erstellen.  
  
     Sie finden die Datei setup.exe im folgenden Ordner:  
  
     \\MyVSShellStub\\MySetup\\MySetup\\Express\\SingleImage\\DiskImages\\DISK1  
  
## Testen das Installationsprogramm  
 Um die Installation zu testen, kopieren Sie die Datei setup.exe auf einen anderen Computer, und führen Sie die Setup\-Datei. Sie sollten die isolierte Shell\-Anwendung ausgeführt werden können.