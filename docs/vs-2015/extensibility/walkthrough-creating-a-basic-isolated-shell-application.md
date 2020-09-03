---
title: 'Exemplarische Vorgehensweise: Erstellen einer einfachen isolierten Shellanwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6192eb5583e7d0bc37518e995aacccad643cc9ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850348"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Exemplarische Vorgehensweise: Erstellen einer grundlegenden Isolated Shell-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie eine isolierte shelllösung erstellen, die Hilfe zum Tool Fenster anpassen und ein Setup Programm erstellen, mit dem die isolierte Shell installiert wird.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Zum Bereitstellen der isolierten Shell müssen Sie auch das verteilbare Visual Studio Shell-Paket (isoliert) verwenden.  
  
## <a name="creating-an-isolated-shell-solution"></a>Erstellen einer isolierten shelllösung  
 In diesem Abschnitt wird gezeigt, wie Sie die isolierte Visual Studio Shell-Projektvorlage verwenden, um eine isolierte shelllösung zu erstellen. Die Lösung enthält die folgenden Projekte:  
  
- Der *SolutionName*. Aboutboxpackage-Projekt, mit dem Sie die Darstellung des Felds "Hilfe/Info" anpassen können.  
  
- Das shellextensionsvsix-Projekt, das die Datei "Source. Extension. vsixmanifest" enthält, die die verschiedenen Komponenten der isolierten Shellanwendung definiert.  
  
- Das *SolutionName* -Projekt, das die ausführbare Datei erstellt, die die isolierte Shellanwendung aufruft. Dieses Projekt enthält den shellanpassungsordner, mit dem Sie die Darstellung und das Verhalten der isolierten Shellanwendung anpassen können.  
  
- Das *SolutionName* -Benutzeroberflächen Projekt, das eine Satellitenassembly erzeugt, die aktive Menübefehle und lokalisierbare Zeichen folgen definiert.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>So erstellen Sie eine grundlegende Lösung für isolierte Shell  
  
1. Öffnen Sie Visual Studio, und erstellen Sie ein neues Projekt.  
  
2. Erweitern Sie im Fenster **Neues Projekt** den Eintrag **andere Projekttypen** , und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie die Vorlage **Visual Studio Shell isoliertes** Projekt aus.  
  
3. Benennen Sie das Projekt `MyVSShellStub` und geben Sie einen Speicherort an. Stellen Sie sicher, dass Projektmappenverzeichnis **Erstellen** aktiviert ist, und klicken Sie dann auf **OK**.  
  
     Die neue Projekt Mappe wird in **Projektmappen-Explorer**angezeigt.  
  
4. Erstellen Sie die Projekt Mappe, und starten Sie das Debugging der isolierten Shellanwendung.  
  
     Die isolierte Visual Studio-Shell wird angezeigt. Die Titelleiste liest **myvsshellstub**. Das Symbol für die Titelleiste wird aus "\meinvsshellstub\ressourcendateien\applicationicon.ico" generiert.  
  
## <a name="customizing-the-application-name-and-icon"></a>Anpassen des Anwendungs namens und des Symbols  
 Möglicherweise möchten Sie Ihre Anwendung mit dem Namen Ihres Unternehmens und dem Logo in der Titelleiste versehen. Die folgenden Schritte zeigen, wie Sie den Namen und das Symbol ändern können, die in der Titelleiste der benutzerdefinierten Anwendung angezeigt werden, indem Sie die Paket Definitionsdatei myvsshellstub. Application. pkgdef ändern.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>So passen Sie den Anwendungsnamen und das Symbol an  
  
1. Öffnen Sie im Projekt myvsshellstub den Befehl \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2. Ändern `AppName` Sie den Wert des Elements in **"appname" = "Fabrikam Music Editor"** .  
  
3. Zum Ändern des Anwendungs Symbols kopieren Sie ein anderes Symbol in das Verzeichnis "\myvsshellstub\meinvsshellstub\meinvsshellstub\". Benennen Sie die vorhandene Datei "ApplicationIcon. ico" in ApplicationIcon1. ico um. Benennen Sie die neue Datei in "ApplicationIcon. ico" um.  
  
4. Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Die IDE für isolierte Shell wird angezeigt. Die Titelleiste enthält das neue Symbol neben den Wörtern **Fabrikam Music Editor**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Anpassen der Standard Webbrowser-Startseite  
 In diesem Abschnitt wird gezeigt, wie die Standard Startseite des **Webbrowser** Fensters geändert wird, indem die Paket Definitionsdatei geändert wird.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>So passen Sie die Standard Startseite des Webbrowsers an  
  
1. Ändern Sie in der Datei myvsshellstub. Application. pkgdef den `DefaultHomePage` Elementwert in " <https://www.microsoft.com> ".  
  
2. Erstellen Sie das Projekt myvsshellstub neu.  
  
3. Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen.  
  
4. Klicken Sie in der **Ansicht bzw. in anderen Fenstern**auf **Webbrowser**. Im **Webbrowser** Fenster wird die Microsoft Corporation-Startseite angezeigt.  
  
## <a name="removing-the-print-command"></a>Entfernen des Print-Befehls  
 Die vsct-Datei in einem Projekt für eine isolierte Shell-Benutzeroberfläche besteht aus einem Satz von Deklarationen des Formular `<Define name=No_` *Elements* `>` , wobei *Element* eines der Standardmenüs und-Befehle von Visual Studio ist.  
  
 Wenn eine Deklaration nicht kommentiert ist, wird das Menü oder der Befehl von der isolierten Shell ausgeschlossen. Wenn eine Deklaration hingegen kommentiert wird, ist das Menü oder der Befehl in der isolierten Shell enthalten.  
  
 In den folgenden Schritten heben Sie die Auskommentierung des Befehls Drucken in der vsct-Datei auf.  
  
#### <a name="to-remove-the-print-command"></a>So entfernen Sie den Befehl "Drucken"  
  
1. Überprüfen Sie, ob der Befehl **Drucken** im Menü **Datei** in der isolierten Shellanwendung angezeigt wird.  
  
2. Öffnen Sie im Projekt myvsshellstubui \ressourcendateien\myvsshellstubui.vsct zur Bearbeitung.  
  
3. Kommentieren Sie diese Zeile aus:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4. Dadurch wird der Befehl "Drucken" entfernt.  
  
5. Starten Sie das Debuggen der isolierten Shellanwendung. Vergewissern Sie sich, dass der Befehl **File/Print** nicht mehr vorhanden ist.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Entfernen von Features aus der isolierten Shell  
 Sie können einige der Pakete entfernen, die mit Visual Studio geladen werden, indem Sie die pkgundef-Datei bearbeiten, wenn Sie diese Funktionen nicht in der benutzerdefinierten Anwendung für isolierte Shell verwenden möchten. Sie geben das Paket in einem der Unterschlüssel des Registrierungsschlüssels "$RootKey $ \packages" an.  
  
> [!NOTE]
> Die GUIDs von Visual Studio-Funktionen finden Sie unter [Paket-GUIDs von Visual Studio-Funktionen](../extensibility/package-guids-of-visual-studio-features.md).  
  
 Im folgenden Verfahren wird gezeigt, wie der XML-Editor aus der isolierten Shell entfernt wird.  
  
#### <a name="to-remove-the-xml-editor"></a>So entfernen Sie den XML-Editor  
  
1. Öffnen Sie die Datei myvsshellstub. pkgundef im Ordner shellanpassung des Projekts myvsshellstub.  
  
2. Entfernen Sie die Auskommentierung der folgenden Zeile:  
  
     [$RootKey $ \packages \\ {87569308-4813-40A0-9cd0-d7a30838ca3f}]  
  
3. Erstellen Sie die Projekt Mappe neu, und starten Sie das Debugging der isolierten Shell Öffnen Sie eine XML-Datei, z. b. \meinvsshellstub\meinvsshellstub\meinvsshellstus\meinvsshellstubui.vsct. Vergewissern Sie sich, dass die XML-Schlüsselwörter in der Datei nicht farbig sind und dass bei der Eingabe von "<" in einer Zeile keine XML-Quick Infos angezeigt werden.  
  
## <a name="customizing-the-helpabout-box"></a>Anpassen des Felds "Hilfe/Info"  
 Sie können das Feld "Hilfe/Info" anpassen, das als Teil der Projektvorlage für isolierte Shell erstellt wird.  
  
#### <a name="to-customize-the-company-name"></a>So passen Sie den Firmennamen an  
  
1. Der Name des Unternehmens, die Copyright Informationen, die Produktversion und die Produktbeschreibung finden Sie im Projekt "myvsshellstub. aboutboxpackage" in der Datei "\Properties\AssemblyInfo.cs". Öffnen Sie diese Datei.  
  
2. Ändern Sie den `AssemblyCompany` Wert in **Fabrikam**, `AssemblyProduct` die `AssemblyTitle` Werte und in **Fabrikam Music Editor**, und `AssemblyCopyright` legen Sie den Wert **Copyright © Fabrikam 2015**:  
  
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
  
3. Um eine Beschreibung des Produkts hinzuzufügen, ändern Sie den `AssemblyDescription` Wert in **die Beschreibung von Fabrikam Music Editor.**  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4. Starten Sie das Debugging, und öffnen Sie in der Anwendung für isolierte Shell das Feld **Hilfe/** Info. Die geänderten Zeichen folgen sollten angezeigt werden. Der Titel des Felds Hilfe/Info ist mit dem `AssemblyTitle` Wert in AssemblyInfo.cs identisch.  
  
5. Die Eigenschaften des Felds " **Hilfe/** Info" selbst finden Sie in der Datei "myvsshellstub. aboutboxpackage\aboutbox.XAML". Wenn Sie die Breite des Felds "Hilfe/Info" ändern möchten, wechseln Sie zum- `AboutDialogStyle` Block, und legen Sie die- `Width` Eigenschaft auf 200 fest:  
  
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
  
6. Erstellen Sie die Projekt Mappe neu, und starten Sie das Debugging der isolierten Shell Das Feld "Hilfe/Info" sollte ungefähr quadratisch sein.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Vor dem Bereitstellen der isolierten Shellanwendung  
 Ihre isolierte Shell-Anwendung kann auf jedem Computer installiert werden, auf dem das verteilbare Paket von Visual Studio Shell (isoliert) installiert ist. Weitere Informationen zum verteilbaren Paket finden Sie auf der Website [Visual Studio-Erweiterbarkeits Downloads](https://msdn.microsoft.com/vstudio/bb984878.aspx) .  
  
## <a name="deploying-the-isolated-shell-application"></a>Bereitstellen der isolierten Shellanwendung  
 Sie stellen die isolierte Shellanwendung auf einem Bereitstellungs Zielcomputer bereit, indem Sie ein Setup-Projekt erstellen. Sie müssen Folgendes angeben:  
  
- Das Layout der Ordner und Dateien auf dem Zielcomputer.  
  
- Die Startbedingungen, die sicherstellen, dass die .NET Framework und die Visual Studio Shell-Laufzeit auf dem Bereitstellungs Zielcomputer installiert sind.  
  
  Im folgenden Verfahren müssen Sie InstallShield Limited Edition auf Ihrem Computer installieren.  
  
#### <a name="to-create-the-setup-project"></a>So erstellen Sie das Setup-Projekt  
  
1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Lösungs Knoten, und klicken Sie dann auf **Neues Projekt hinzufügen**.  
  
2. Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **andere Projekttypen** , und wählen Sie dann **Setup und Bereitstellung**aus. Wählen Sie die Vorlage InstallShield aus. Benennen Sie das neue Projekt, `MySetup` und klicken Sie dann auf **OK**.  
  
3. Wenn InstallShield Limited Edition bereits installiert ist, fahren Sie mit dem nächsten Schritt fort.  
  
    Wenn InstallShield Limited Edition noch nicht installiert ist, wird die InstallShield-Downloadseite angezeigt. Befolgen Sie die Anweisungen zum herunterladen und Installieren des Produkts, und wählen Sie die Version von InstallShield aus, die mit Ihrer Version von Visual Studio kompatibel ist. Sie müssen entscheiden, ob Sie die Installation von InstallShield registrieren oder als Evaluierungsversion verwenden möchten. Sie müssen Visual Studio nach Abschluss der Installation neu starten.  
  
   > [!IMPORTANT]
   > Vor dem Erstellen eines InstallShield-Projekts müssen Sie Visual Studio als Administrator starten. Wenn Sie dies nicht tun, erhalten Sie eine Fehlermeldung, wenn Sie das Projekt erstellen.  
  
   In den nächsten Schritten wird gezeigt, wie Sie das Setup-Projekt konfigurieren.  
  
> [!IMPORTANT]
> Stellen Sie sicher, dass Sie die Releasekonfiguration des isolierten shellprojekts mindestens einmal erstellt haben, bevor Sie das Setup-Projekt konfigurieren.  
  
#### <a name="to-configure-the-setup-project"></a>So konfigurieren Sie das Setup-Projekt  
  
1. Wählen Sie im **Projektmappen-Explorer**unter dem Projekt **mySetup** die Option **Projekt-Assistent**aus. Wählen Sie in der unteren Zeile des Fensters **Projekt-Assistent** die Option **Anwendungsinformationen**aus. Geben Sie unter Unternehmens Name den Namen **Fabrikam** **und den Anwendungsnamen als Anwendungs** Namen ein. Wählen Sie den vorwärts Pfeil unten rechts im Projekt- **Assistent**aus.  
  
2. Wählen Sie unter **ist Ihre Anwendung muss Software auf dem Computer installiert sein? die** Option **Ja** aus, und wählen Sie dann **Microsoft .net vollständigen Paket für Framework 4,5**aus.  
  
3. Wählen Sie unten im Fenster die Schaltfläche **Anwendungs Dateien** aus, und vergewissern Sie sich, dass der Ordner **Fabrikam Music Editor** ausgewählt ist.  
  
4. Wählen Sie die Schaltfläche **Dateien hinzufügen** aus. Fügen Sie im Dialogfeld " **Dateien hinzufügen** " die folgenden Dateien aus dem Ordner " **myvsshellstub\release** " hinzu:  
  
    1. MyVSShellStub.exe.config  
  
    2. DebuggerProxy.dll  
  
    3. DebuggerProxy.dll. Manifest  
  
    4. Myvsshellstub. pkgdef  
  
    5. Myvsshellstub. pkgundef  
  
    6. Myvsshellstub. winprf  
  
    7. Splash.bmp  
  
5. Klicken Sie auf die Schaltfläche **Projekt Ausgaben hinzufügen** , und fügen Sie **myvsshellstub/Primary Output**hinzu. Klicken Sie auf **OK**.  
  
6. Klicken Sie im linken Bereich unter **Ziel Computer**mit der rechten Maustaste auf den Knoten **Fabrikam Music Editor [INSTALLDIR]** , und fügen Sie einen **neuen Ordner** mit dem Namen **Extensions**hinzu.  
  
7. Klicken Sie mit der rechten Maustaste auf den Knoten **Erweiterungen** im linken Bereich, und fügen Sie einen neuen Ordner mit dem Namen **Application**  
  
8. Wählen Sie den **Anwendungs** Ordner aus, und klicken Sie auf die Schaltfläche **Projekt Ausgaben hinzufügen** . Wählen Sie dann die primäre Ausgabe aus dem Projekt myvsshellstub. aboutboxpackage aus.  
  
9. Klicken Sie auf die Schaltfläche **Dateien hinzufügen** , und fügen Sie im Ordner \myvsshellstub\release\extensions\application\ die folgenden Dateien hinzu:  
  
    - Myvsshellstub. aboutboxpackage. pkgdef  
  
    - Myvsshellstub. Application. pkgdef  
  
10. Klicken Sie im linken Bereich mit der rechten Maustaste auf den Knoten **Fabrikam Music Editor [INSTALLDIR]** , und fügen Sie einen neuen Ordner mit dem Namen **1033**hinzu.  
  
11. Wählen Sie den Ordner 1033 aus, und klicken Sie dann auf die Schaltfläche **Projekt Ausgaben hinzufügen** . Wählen Sie dann die primäre Ausgabe aus dem Projekt myvsshellstubui aus.  
  
12. Wechseln Sie zum Fenster **Anwendungs** Verknüpfungen.  
  
13. Klicken Sie auf " **neu** ", um eine Verknüpfung zu erstellen, und wählen Sie " **[ProgramFilesFolder] \fabrikam\fabrikam Music editor\myvsshellstub.Primary Output**" aus.  
  
14. Wechseln Sie zum Bereich **Installations Interview** .  
  
15. Legen Sie alle Elemente auf **Nein**fest.  
  
16. Öffnen Sie in **Projektmappen-Explorer**im Projekt mySetup die **Einstellung Setup Anforderungen und Aktionen \ Anforderungen definieren**. Das Fenster **Anforderungen** wird geöffnet.  
  
17. Klicken Sie mit der rechten Maustaste auf **System Software Anforderungen** und dann auf **neue Startbedingung erstellen**. Der **Assistent für die System Suche** wird angezeigt.  
  
18. Wählen Sie im Bereich **Was möchten Sie suchen?** die Option **Registrierungs Eintrag** in der Dropdown Liste aus, und klicken Sie auf **weiter**.  
  
19. Wählen Sie im Bereich **wie möchten Sie suchen?** den **HKEY_LOCAL_MACHINE** als Registrierungs Stamm aus. Geben Sie **software\wow6432node\microsoft\devdiv\vs\servicing\14.0\isoshell** für 64-Bit-Systeme oder **software\microsoft\devdiv\vs\servicing\14.0\isoshell** für 32-Bit-Systeme ein, und geben Sie **install** als Registrierungs Wert ein. Klicken Sie auf **Weiter**.  
  
20. Geben Sie im Bereich **Was möchten Sie mit dem Wert machen?** ein, dass **für dieses Produkt die Installation von Visual Studio 2015 isolierte Shell Redistributable erforderlich ist.** als Anzeige Text, und klicken Sie auf **Fertig**stellen.  
  
21. Erstellen Sie die Lösung für isolierte Shell neu, um das Setup Projekt zu erstellen.  
  
     Sie finden die setup.exe Datei im folgenden Ordner:  
  
     \Meinvsshellstub\mysetup\mysetup\express \singleimage\diskimages\disk1  
  
## <a name="testing-the-installation-program"></a>Testen des Installationsprogramms  
 Um das Setup zu testen, kopieren Sie die setup.exe Datei auf einen anderen Computer, und führen Sie die ausführbare Setup Datei aus. Sie sollten in der Lage sein, die isolierte Shellanwendung auszuführen.
