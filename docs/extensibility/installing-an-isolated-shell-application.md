---
title: "Installieren einer Anwendung isolierte Shell | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Shell [Visual Studio], Shell-basierte Bereitstellung"
  - "Visual Studio-Shell, Shell-basierte Bereitstellung"
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 40
caps.handback.revision: 40
ms.author: "gregvanl"
manager: "ghogen"
---
# Installieren einer Anwendung isolierte Shell
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um eine Shell\-app zu installieren, müssen Sie die folgenden Schritte ausführen.  
  
-   Vorbereiten der Projektmappe.  
  
-   Erstellen Sie eine Windows Installer \(MSI\)\-Paket für Ihre Anwendung.  
  
-   Erstellen Sie einen Setup\-Bootstrapper.  
  
 Alle von der Beispielcode in diesem Dokument stammt aus der [Shell Bereitstellung Beispiel](http://go.microsoft.com/fwlink/?LinkId=262245), die Sie in der Code Gallery auf der MSDN\-Website herunterladen können. Das Beispiel zeigt die Ergebnisse der einzelnen Schritte.  
  
## Erforderliche Komponenten  
 Zum Ausführen der Prozeduren, die in diesem Thema wird beschrieben, müssen die folgenden Tools auf Ihrem Computer installiert werden.  
  
-   Das Visual Studio SDK  
  
-   Die [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) Version 3.6  
  
 Das Beispiel erfordert auch die Microsoft\-Visualization and Modeling SDK, die nicht alle Shells erfordern.  
  
## Vorbereiten der Projektmappe  
 In der Standardeinstellung Shell Vorlagen zum VSIX\-Pakete erstellen, aber dieses Verhalten ist in erster Linie für Debugzwecke bestimmt. Wenn Sie eine Shell\-Anwendung bereitstellen, müssen Sie MSI\-Paketen verwenden, um für den Zugriff auf die Registrierung und Neustarts während der Installation zu ermöglichen. Um Ihre Anwendung für die MSI\-Bereitstellung vorzubereiten, führen Sie die folgenden Schritte aus.  
  
#### Vorbereiten eine shellanwendung für MSI\-Bereitstellung  
  
1.  Bearbeiten Sie jede vsixmanifest\-Datei in der Projektmappe.  
  
     In der `Identifier` \-Element, Hinzufügen einer `InstalledByMSI` Element und ein `SystemComponent` \-Element, und setzen Sie deren Werte auf `true`.  
  
     Diese Elemente verhindern, dass das VSIX\-Installationsprogramm beim Versuch, Ihre Komponenten und die Benutzer installieren aus deinstallieren sie mithilfe der **Erweiterungen und Updates** \(Dialogfeld\).  
  
2.  Bearbeiten Sie für jedes Projekt, das ein VSIX\-Manifest enthält die Aufgaben des Inhalts an den Speicherort für die Ausgabe von dem MSI installiert. Schließen Sie das VSIX\-Manifest in die Buildausgabe, aber erstellen Sie nicht zu eine VSIX\-Datei.  
  
## Erstellen eine MSI\-Datei für Ihre Shell  
 Um die MSI\-Paket zu erstellen, wird empfohlen, Sie verwenden die [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) da dadurch mehr Flexibilität als ein standard\-Setup\-Projekt.  
  
 Legen Sie in der Datei Product.wxs Erkennung Blöcke und das Layout der Komponenten.  
  
 Erstellen Sie in der Registrierungsdatei für Ihre Projektmappe und in ApplicationRegistry.wxs Registrierungseinträge.  
  
### Erkennung von Blöcken  
 Ein Erkennung Block besteht aus einer `Property` Element, das eine Voraussetzung für die Erkennung angibt und ein `Condition` \-Element, das gibt eine Meldung zurückgegeben, wenn die erforderlichen Komponenten nicht auf dem Computer vorhanden ist. Beispielsweise Ihre Shell\-Anwendung muss der Microsoft Visual Studio\-Shell redistributable, und der Erkennung\-Block wird das folgende Markup entsprechen.  
  
```xml  
<Property Id="ISOSHELLSFX"> <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Property Id="INTSHELLSFX"> <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again."> <![CDATA[Installed OR ISOSHELLSFX]]> </Condition> <Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again."> <![CDATA[Installed OR INTSHELLSFX]]> </Condition>  
  
```  
  
### Layout der Shellkomponenten  
 Sie müssen die Elemente zum Identifizieren der Ziel\-Verzeichnisstruktur und die zu installierenden Komponenten hinzufügen.  
  
##### Das Layout der Komponenten festlegen  
  
1.  Erstellen einer Hierarchie von `Directory` Elemente stehen alle Verzeichnisse im Dateisystem auf dem Zielcomputer erstellen, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir"> <Directory Id="ProgramFilesFolder"> <Directory Id="CompanyDirectory" Name="$(var.CompanyName)"> <Directory Id="INSTALLDIR" Name="$(var.FullProductName)"> <Directory Id="ExtensionsFolder" Name="Extensions" /> <Directory Id="Folder1033" Name="1033" /> </Directory> </Directory> </Directory> <Directory Id="ProgramMenuFolder"> <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/> </Directory> </Directory>  
    ```  
  
     Diese Verzeichnisse zu verdanken `Id` bei Dateien, die installiert werden müssen angegeben werden.  
  
2.  Identifizieren Sie die Komponenten, die die Shell und die Shell\-Anwendung, wie im folgenden Beispiel gezeigt erfordern.  
  
    > [!NOTE]
    >  Einige Elemente möglicherweise auf Definitionen in anderen WXS\-Dateien verweisen.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1"> <ComponentGroupRef Id="ApplicationGroup" /> <ComponentGroupRef Id="HelpAboutPackage" /> <ComponentRef Id="GeneralProfile" /> <ComponentGroupRef Id="EditorAdornment"/> <ComponentGroupRef Id="SlideShowDesignerGroup"/> <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. --> <ComponentGroupRef Id="Product.Generated" /> </Feature>  
    ```  
  
    1.  Die `ComponentRef` Element verweist auf eine andere WXS\-Datei, die Dateien identifiziert, die die aktuelle Komponente erforderlich sind. GeneralProfile enthält z. B. die folgende Definition HelpAbout.wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles"> <DirectoryRef Id="INSTALLDIR"> <Directory Id="ProfilesFolder" Name="Profiles"> <Component Id='GeneralProfile' Guid='*'> <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' /> </Component> </Directory> </DirectoryRef> </Fragment>  
        ```  
  
         Das `DirectoryRef` \-Element gibt an, wo diese Dateien auf dem Computer des Benutzers. Das `Directory` \-Element gibt an, dass es in einem Unterverzeichnis, und jeder installiert wird `File` Element repräsentiert eine Datei, die erstellt wird oder als Teil der Projektmappe vorhanden ist und identifiziert, in dem diese Datei der Erstellung der MSI\-Datei gefunden werden kann.  
  
    2.  Die `ComponentGroupRef` Element verweist auf eine Gruppe anderer Komponenten \(oder Komponenten und Gruppen\). Z. B. `ComponentGroupRef` unter ApplicationGroup ist wie folgt definiert in Application.wxs.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup"> <ComponentGroupRef Id="DebuggerProxy" /> <ComponentRef Id="MasterPkgDef" /> <ComponentRef Id="SplashResource" /> <ComponentRef Id="IconResource" /> <ComponentRef Id="WinPrfResource" /> <ComponentRef Id="AppExe" /> <ComponentRef Id="AppConfig" /> <ComponentRef Id="AppPkgDef" /> <ComponentRef Id="AppPkgDefUndef" /> <ComponentRef Id="$(var.ShortProductName)UI1033" /> <ComponentRef Id="ApplicationShortcut"/> <ComponentRef Id="ApplicationRegistry"/> </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  Abhängigkeiten für Applikationen Shell \(isoliert\) sind erforderlich: DebuggerProxy, MasterPkgDef, Ressourcen \(insbesondere die .winprf\-Datei\), Anwendung und PkgDefs.  
  
### Registrierungseinträge  
 Die Shell \(isoliert\)\-Projektvorlage enthält ein *Projektname*reg\-Datei für die Registrierungsschlüssel auf Installation zusammenführen. Diese Registrierungseinträge müssen Teil der MSI\-Datei für die Installation und Bereinigung zu sein. Sie müssen auch übereinstimmende Registrierung Blöcke in ApplicationRegistry.wxs erstellen.  
  
##### Registrierungseinträge in die MSI\-Datei integrieren.  
  
1.  In der **Shell Anpassung** öffnen Sie im Ordner *Projektname*. reg.  
  
2.  Ersetzen Sie alle Instanzen des Tokens $ $RootFolder durch den Pfad des Ziel\-Installationsverzeichnisses.  
  
3.  Fügen Sie andere Registrierungseinträge, die Ihre Anwendung benötigt.  
  
4.  Öffnen Sie ApplicationRegistry.wxs.  
  
5.  Für jeden Registrierungseintrag in *Projektname*reg, fügen Sie einen entsprechenden Block für die Registrierung, wie im folgenden Beispiel.  
  
    |*Projektname*reg|ApplicationRegisty.wxs|  
    |----------------------|----------------------------|  
    |\[HKEY\_CLASSES\_ROOT\\CLSID\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6}\]<br /><br /> @\= "PhotoStudio DTE Object"|\< RegistryKey\-Id \= 'DteClsidRegKey' Root \= "HKCR" Key \= "$\(var.\) DteClsidRegKey\)' Aktion 'CreateAndRemoveOnUninstall' \= \><br /><br /> \< RegistryValue Type \= 'String' Name \=' @' Wert \= "$\(var ShortProductName\) DTE\-Objekt "\/ \><br /><br /> \< \/ RegistryKey \>|  
    |\[\\LocalServer32 HKEY\_CLASSES\_ROOT\\CLSID\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6}\]<br /><br /> @\= "$RootFolder$\\PhotoStudio.exe"|\< RegistryKey\-Id \= 'DteLocSrv32RegKey' Root \= "HKCR" Key \= "$\(var.\) DteClsidRegKey\) \\LocalServer32' Aktion 'CreateAndRemoveOnUninstall' \= \><br /><br /> \< RegistryValue Type \= 'String' Name \=' @' Wert \='\[INSTALLDIR\] $\(var ShortProductName\) .exe "\/ \><br /><br /> \< \/ RegistryKey \>|  
  
     In diesem Beispiel löst Var.DteClsidRegKey in den Registrierungsschlüssel in der obersten Zeile auf. Var.ShortProductName löst in `PhotoStudio`.  
  
## Erstellen eines Setup\-Bootstrappers  
 Fertigen MSI installiert nur, wenn Sie zuerst alle erforderlichen Komponenten installiert sind. Um des Endbenutzers zu vereinfachen, erstellen Sie ein Setupprogramm, sammelt und alle erforderlichen Komponenten installiert, bevor sie die Anwendung installiert wird. Um eine erfolgreiche Installation sicherzustellen, müssen führen Sie folgende Aktionen aus:  
  
-   Erzwingen Sie die Installation durch den Administrator.  
  
-   Erkennen Sie, ob der Visual Studio\-Shell \(isoliert\) installiert ist.  
  
-   Führen Sie eine oder beide Shell Installationsprogramme in der Reihenfolge.  
  
-   Neustart\-Anfragen behandelt.  
  
-   Führen Sie die MSI\-Datei.  
  
### Erzwingen der Installation durch den Administrator  
 Dieses Verfahren ist erforderlich, um das Setup\-Programm den Zugriff auf erforderliche Verzeichnisse wie z. B. \\programme\\ zu aktivieren.  
  
##### Installation vom Administrator erzwungen werden  
  
1.  Öffnen Sie das Kontextmenü für das Setup\-Projekt, und wählen Sie dann **Eigenschaften**.  
  
2.  Klicken Sie unter **Konfigurationsdatei Linker\/Eigenschaften\/Manifest**, legen **UAC\-Ausführungsebene** auf **RequireAdministrator**.  
  
     Diese Eigenschaft setzt das Attribut, das das Programm als Administrator ausgeführt werden soll, in der eingebetteten manifest\-Datei erforderlich ist.  
  
### Erkennen von Shell\-Installationen  
 Um zu bestimmen, ob der Visual Studio\-Shell \(isoliert\) installiert werden muss, zuerst zu bestimmen, ob es bereits installiert ist, überprüfen Sie den Wert des Registrierungsschlüssels, der HKLM\\Software\\Microsoft\\DevDiv\\vs\\Servicing\\ShellVersion\\isoshell\\LCID\\Install.  
  
> [!NOTE]
>  Diese Werte werden auch vom Shell\-Erkennung in Product.wxs Block gelesen werden.  
  
 HKLM\\Software\\Microsoft\\AppEnv\\14.0\\ShellFolder Gibt den Speicherort der Visual Studio\-Shell installiert wurde, und können nach Dateien suchen.  
  
 Ein Beispiel eine Shellinstallation zu ermitteln, finden Sie unter der `GetProductDirFromReg` Funktion der Utilities.cpp in der Shell\-Bereitstellung\-Beispiel.  
  
 Wenn eine oder beide der Visual Studio\-Shells, die das Paket erfordert, ist nicht auf dem Computer installiert, müssen Sie diese der Liste der zu installierenden Komponenten hinzufügen. Ein Beispiel finden Sie die `ComponentsPage::OnInitDialog` Funktion der ComponentsPage.cpp in der Shell\-Bereitstellung\-Beispiel.  
  
### Die Shell\-Installationsprogramme ausgeführt  
 Führen Sie das Shell\-Installationsprogramme rufen Sie die Visual Studio Shell verteilbaren Komponenten mit den richtigen Befehlszeilenargumenten. Sie müssen mindestens die Befehlszeilenargumente verwenden **\/norestart \/q** und achten Sie auf den Rückgabecode, um zu bestimmen, was als Nächstes ausgeführt werden soll. Im folgende Beispiel wird die Shell \(isoliert\) redistributable ausgeführt.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### Die Shell Language Pack\-Installationsprogramme ausgeführt  
 Wenn Sie stattdessen feststellen, dass die Shell oder Shells installiert wurden und nur ein Language pack benötigen, können Sie wie im folgenden Beispiel gezeigt die Sprachpakete installieren.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### Entschlüsseln von Rückgabewerten  
 Bei einigen Betriebssystemen ist die Installation von Visual Studio\-Shell \(isoliert\) ein Neustart erforderlich. Diese Bedingung kann bestimmt werden, indem Sie die Ergebnisse des Aufrufs von `ExecCmd`.  
  
|Rückgabewert|Beschreibung|  
|------------------|------------------|  
|ERROR\_SUCCESS|Installation wurde abgeschlossen. Sie können die Anwendung jetzt installieren.|  
|ERROR\_SUCCESS\_REBOOT\_REQUIRED|Installation wurde abgeschlossen. Sie können die Anwendung nach dem Neustart des Computers installieren.|  
|3015|Installation wird ausgeführt. Ein Neustart des Computers ist erforderlich, um die Installation fortzusetzen.|  
  
### Behandlung von Neustarts  
 Ausgeführt Shell\-Installationsprogramm mit dem **\/norestart** Argument angegeben, dass sie den Computer neu starten oder bitten Sie für den Computer neu gestartet werden, würde nicht. Jedoch möglicherweise ein Neustart erforderlich, und Sie müssen sicherstellen, dass Ihr Installationsprogramm auch weiterhin nach dem Neustart des Computers.  
  
 Neustarts ordnungsgemäß behandeln werden, vergewissern Sie sich, nur eine Setup\-Programm ist auf fortsetzen und der Vorgang fortsetzen ordnungsgemäß behandelt werden.  
  
 ERROR\_SUCCESS\_REBOOT\_REQUIRED oder 3015 zurückgegeben wird, sollte der Code den Computer neu starten, bevor die Installation fortgesetzt wird.  
  
 Um Neustarts zu behandeln, können führen Sie folgende Aktionen aus:  
  
-   Legen Sie die Registrierung, um die Installation fortsetzen, wenn Windows gestartet wird.  
  
-   Führen Sie einen doppelten Neustart des Bootstrappers.  
  
-   Löschen Sie die Shell Installer ResumeData Schlüssel.  
  
-   Starten Sie Windows neu.  
  
-   Zurücksetzen des Start\-Pfads, der die MSI\-Datei.  
  
### Festlegen der Registrierungs die Installation fort, wenn Windows gestartet wird  
 Die HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\RunOnce\\ Registrierungsschlüssel beim Systemstart mit Administratorrechten ausgeführt wird, und anschließend gelöscht wird.HKEY\_CURRENT\_USER enthält einen Schlüssel, die ähnlich, aber er wird als normaler Benutzer ausgeführt und ist für Installationen. Sie können die Installation fortsetzen, verlegen Sie einen Zeichenfolgenwert in den RunOnce\-Schlüssel, der das Installationsprogramm aufruft. Jedoch wird empfohlen, Sie das Installationsprogramm mithilfe rufen einer **\/restart** oder ähnliche Parameter, um die Anwendung zu benachrichtigen, die es statt fortgesetzt wird. Sie können auch angeben, wo Sie bei der Installation wird insbesondere für Installationen, die mehrere Neustarts erfordern möglicherweise Parameter einschließen.  
  
 Das folgende Beispiel zeigt eine RunOnce\-Registrierungsschlüsselwert zum Fortsetzen der Installation.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### Doppelte Neustart des Bootstrappers installieren  
 Wenn Setup direkt von RunOnce verwendet wird, werden der Desktop kann nicht vollständig geladen. Um die vollständige Benutzeroberfläche verfügbar zu machen, müssen Sie erstellen eine weitere Ausführung des Setups und die RunOnce\-Instanz zu beenden.  
  
 Das Setup\-Programm muss erneut ausgeführt werden, damit er die richtigen Berechtigungen erhält, und müssen Sie ihm genügend Informationen kennen, in denen beendet vor dem Neustart, wie im folgenden Beispiel gezeigt.  
  
```  
if (_cmdLineInfo.IsRestart()) { TCHAR path[MAX_PATH]={0}; GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR)); ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL ); }  
  
```  
  
### Löschen die Shell Installer ResumeData Schlüssel  
 Die Shell Installer legt die HKLM\\Software\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData Registrierungsschlüssel mit Daten, um die Installation nach dem Neustart fortgesetzt. Da die Anwendung, die Shell\-Installationsprogramm, fortgesetzt wird, löschen Sie diesen Registrierungsschlüssel, wie im folgenden Beispiel gezeigt.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData")); RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### Windows\-Neustart  
 Nachdem Sie die erforderlichen Registrierungsschlüssel festgelegt haben, können Sie Windows neu starten. Das folgende Beispiel ruft die Neustart\-Befehle für verschiedene Windows\-Betriebssysteme.  
  
```  
OSVERSIONINFO ov; HANDLE htoken ; //Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown. if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken)) { LUID luid ; LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ; TOKEN_PRIVILEGES    privs ; privs.Privileges[0].Luid = luid ; privs.PrivilegeCount = 1 ; privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ; AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ; } //Use InitiateSystemShutdownEx to avoid unexpected restart message box try { if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) )) { bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG); } else { #pragma prefast(suppress:380,"ignore warning about legacy api") bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE); } } catch(...) { //advapi32.dll call not available! Will not restart! }  
  
```  
  
### Zurücksetzen des Start\-Pfads der MSI\-Datei  
 Das aktuelle Verzeichnis ist der Speicherort der Setup\-Programm vor dem Neustart jedoch nach dem Neustart wird des Speicherorts system32\-Verzeichnis. Das Setup\-Programm sollte wie im folgenden Beispiel gezeigt vor jedem Aufruf MSI\-Datei im aktuelle Verzeichnis zurückgesetzt.  
  
```  
CString GetSetupPath() { TCHAR file[MAX_PATH]; GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR)); CString path(file); int fpos = path.ReverseFind('\\'); if (fpos != -1) { path = path.Left(fpos + 1); } return path; }  
  
```  
  
### Ausführen der MSI\-Anwendung  
 Nachdem der Installer für Visual Studio\-Shell ERROR\_SUCCESS zurückgegeben wurde, können Sie die MSI\-Datei für Ihre Anwendung ausführen. Da das Setupprogramm die Benutzeroberfläche bereitstellt, starten Sie die MSI\-Datei im stillen Modus \(**\/q**\) und mit Protokollierung \(**\/L**\), wie im folgende Beispiel gezeigt.  
  
```cpp#  
TCHAR temp[MAX_PATH]; GetTempPath(MAX_PATH, temp); CString boutiqueInstallCmd, msi, log; CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress")); CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi")); log.Format(_T("\"%s%s.log\""), temp, name); msi.Format(_T("\"%s%s\""), GetSetupPath(), name); boutiqueInstallCmd.Format(cmdLine, msi, log); //TODO: You can use MSI API to gather and present install progress feedback from your MSI. dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)