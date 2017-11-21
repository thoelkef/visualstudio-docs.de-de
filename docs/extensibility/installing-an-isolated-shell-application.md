---
redirect_url: shell/installing-an-isolated-shell-application
title: Installieren einer isolierten Shellanwendung | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: "40"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e3c6d5d88563d97c18081cbf44b67e247d98a468
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="installing-an-isolated-shell-application"></a>Installieren einer isolierten Shellanwendung
Um eine Shell-app zu installieren, müssen Sie die folgenden Schritte ausführen.  
  
-   Vorbereiten der Projektmappe.  
  
-   Erstellen Sie eine Windows Installer (MSI)-Paket für Ihre Anwendung.  
  
-   Erstellen Sie einen Setup-Bootstrapper.  
  
 Alle von der Beispielcode in diesem Dokument stammen aus den [Shell Bereitstellung Beispiel](http://go.microsoft.com/fwlink/?LinkId=262245), das Sie in der Code Gallery auf der MSDN-Website herunterladen können. Das Beispiel zeigt die Ergebnisse der einzelnen Schritte ausführen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen der Schritte, die in diesem Thema wird beschrieben, müssen die folgenden Tools auf dem Computer installiert werden.  
  
-   Das Visual Studio SDK  
  
-   Die [Windows Installer XML-Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) Version 3.6  
  
 Das Beispiel erfordert auch die Microsoft-Visualization and Modeling-SDK, die nicht alle Shells erfordern.  
  
## <a name="preparing-your-solution"></a>Vorbereiten der Projektmappe  
 Standardmäßig Shell-Vorlagen für VSIX-Pakete erstellen, aber dieses Verhalten ist in erster Linie für Debugzwecke bestimmt. Wenn Sie eine Shell-Anwendung bereitstellen, müssen Sie die MSI-Paketen verwenden, für den Zugriff auf die Registrierung und Neustart während der Installation zugelassen. Führen Sie die folgenden Schritte aus, um Ihre Anwendung für die MSI-Bereitstellung vorzubereiten.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>So bereiten Sie eine shellanwendung für die MSI-Bereitstellung vor  
  
1.  Bearbeiten Sie jede vsixmanifest-Datei in der Projektmappe.  
  
     In der `Identifier` Element, Hinzufügen einer `InstalledByMSI` Element und ein `SystemComponent` Element, und legen Sie deren Werte auf `true`.  
  
     Diese Elemente verhindern, dass das VSIX-Installationsprogramm versuchen, Ihre Komponenten und die Benutzer installieren aus deinstallieren sie mithilfe der **Erweiterungen und Updates** (Dialogfeld).  
  
2.  Bearbeiten Sie für jedes Projekt, das eine VSIX-Manifest enthält die Buildaufgaben, um den Inhalt an den Speicherort auszugeben, über das die MSI-Datei installiert. Das VSIX-Manifest in der Buildausgabe enthalten jedoch eine VSIX-Datei nicht erstellen.  
  
## <a name="creating-an-msi-for-your-shell"></a>Erstellen eine MSI-Datei für Ihre Shell  
 Um die MSI-Paket zu erstellen, wir empfehlen die Verwendung der [Windows Installer XML-Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) , da sie mehr Flexibilität als ein standard Setupprojekt erhalten.  
  
 Legen Sie in der Datei Product.wxs Erkennung Blöcke und das Layout der Komponenten der Shell aus.  
  
 Erstellen Sie Registrierungseinträge, in die REG-Datei für die Projektmappe und im ApplicationRegistry.wxs.  
  
### <a name="detection-blocks"></a>Erkennung von Blöcken  
 Besteht aus ein Block Erkennung einer `Property` Element, das eine Voraussetzung für die Erkennung angibt und ein `Condition` Element, der angibt, eine Nachricht zurückgeben, wenn die erforderlichen Komponenten nicht auf dem Computer vorhanden sind. Beispielsweise Ihre Shell-Anwendung müssen Microsoft Visual Studio Shell redistributable, und der Erkennung-Block wird das folgende Markup entsprechen.  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>Layout der Shellkomponenten  
 Sie müssen die Elemente zum Identifizieren der Ziel-Verzeichnisstruktur und die zu installierenden Komponenten hinzufügen.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Das Layout der Shell-Komponenten festgelegt.  
  
1.  Erstellen Sie eine Hierarchie von `Directory` Elemente, die alle Verzeichnisse im Dateisystem auf dem Zielcomputer erstellen, wie im folgenden Beispiel gezeigt darstellen.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     Diese Verzeichnisse werden durch bezeichnet `Id` bei Dateien, die installiert werden müssen angegeben werden.  
  
2.  Identifizieren Sie die Komponenten, die die Verwaltungsshell, und Shell-Anwendung, wie im folgenden Beispiel gezeigt erfordern.  
  
    > [!NOTE]
    >  Einige Elemente dürfen sich auf Definitionen in anderen WXS-Dateien verweisen.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1.  Die `ComponentRef` Element bezieht sich auf eine andere WXS-Datei, die Dateien identifiziert, die die aktuelle Komponente erforderlich sind. GeneralProfile weist z. B. folgende Definition in HelpAbout.wxs an.  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         Die `DirectoryRef` Element gibt an, wo diese Dateien auf dem Computer des Benutzers. Die `Directory` Element gibt an, dass es in ein Unterverzeichnis, und jeder installiert werden `File` Element stellt eine Datei, die erstellt wird, oder, die als Teil der Lösung vorhanden ist, und identifiziert, in dem diese Datei wird von der Erstellung der MSI-Datei gefunden werden kann.  
  
    2.  Die `ComponentGroupRef` Element bezieht sich auf eine Gruppe von anderen Komponenten (oder -Komponenten und Komponentengruppen). Z. B. `ComponentGroupRef` unter ApplicationGroup ist wie folgt definiert in Application.wxs.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  Abhängigkeiten für Anwendungen Shell (isoliert) sind erforderlich: DebuggerProxy, MasterPkgDef, Ressourcen (insbesondere die .winprf-Datei), Anwendung und PkgDefs.  
  
### <a name="registry-entries"></a>Registrierungseinträge  
 Die Projektvorlage Shell (isoliert) umfasst eine *Projektname*reg-Datei für den Registrierungsschlüssel, für die Installation zusammenzuführen. Diese Registrierungseinträge muss Teil der MSI-Datei für die Installation und Bereinigung Zwecke. Außerdem müssen Sie übereinstimmende Registrierung Blöcke in ApplicationRegistry.wxs erstellen.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Zum Integrieren der Registrierungseinträge in die MSI-Datei  
  
1.  In der **Shell Anpassung** Ordner *Projektname*. reg.  
  
2.  Ersetzen Sie alle Instanzen des Tokens $ $RootFolder durch den Pfad des Ziel-Installationsverzeichnisses.  
  
3.  Fügen Sie keine andere Registrierungseinträge, die die Anwendung erfordert.  
  
4.  Öffnen Sie ApplicationRegistry.wxs.  
  
5.  Für die einzelnen Registrierungseinträge im *Projektname*reg, fügen Sie einen entsprechenden Block für die Registrierung wie in den folgenden Beispielen veranschaulicht.  
  
    |*Projektname*reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "PhotoStudio DTE-Object"|\<RegistryKey-Id = "DteClsidRegKey" Root "HKCR" Schlüssel = = "$(" var ". DteClsidRegKey) "Aktion"CreateAndRemoveOnUninstall"= ><br /><br /> \<RegistryValue Type = 'String' Name = "@" Wert = "$(" var ". ShortProductName) DTE-Objekt "/ ><br /><br /> \</ RegistryKey >|  
    |[HKEY_CLASSES_ROOT\CLSID\\\LocalServer32 {bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "$RootFolder$\PhotoStudio.exe"|\<RegistryKey-Id = "DteLocSrv32RegKey" Root "HKCR" Schlüssel = = "$(" var ". DteClsidRegKey) \LocalServer32 "Aktion"CreateAndRemoveOnUninstall"= ><br /><br /> \<RegistryValue Type = 'String' Name = "@" Wert = "[INSTALLDIR] $(" var ". ShortProductName) .exe "/ ><br /><br /> \</ RegistryKey >|  
  
     In diesem Beispiel löst Var.DteClsidRegKey in den Registrierungsschlüssel in der obersten Zeile auf. Var.ShortProductName löst in `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Erstellen einen Setup-Bootstrapper  
 Abgeschlossene MSI installiert nur, wenn zunächst die erforderlichen Komponenten installiert werden. Um die benutzerfreundlichkeit zu vereinfachen, erstellen Sie ein Setupprogramm, das erfasst und alle erforderlichen Komponenten installiert, bevor sie die Anwendung installiert. Um eine erfolgreiche Installation zu gewährleisten, können führen Sie folgende Aktionen aus:  
  
-   Erzwingen Sie die Installation vom Administrator.  
  
-   Erkennen Sie, ob die Visual Studio-Shell (isoliert) installiert ist.  
  
-   Führen Sie eine oder beide Shell Installationsprogramme in der Reihenfolge.  
  
-   Neustart-Anforderungen verarbeitet werden.  
  
-   Führen Sie die MSI-Datei.  
  
### <a name="enforcing-installation-by-administrator"></a>Erzwingen der Installation vom Administrator  
 Dieses Verfahren ist erforderlich, um das Setup-Programm den Zugriff auf erforderliche Verzeichnisse z. B. \Program Files aktivieren\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Installation vom Administrator erzwungen werden  
  
1.  Öffnen Sie das Kontextmenü für das Setup-Projekt, und wählen Sie dann **Eigenschaften**.  
  
2.  Klicken Sie unter **Linker/Eigenschaften/Manifest Konfigurationsdatei**legen **UAC-Ausführungsebene** auf **RequireAdministrator**.  
  
     Diese Eigenschaft setzt das Attribut, das das Programm als Administrator ausgeführt werden soll, in der eingebetteten manifest-Datei erfordert.  
  
### <a name="detecting-shell-installations"></a>Erkennen von Shell-Installationen  
 Um zu bestimmen, ob die Visual Studio-Shell (isoliert) installiert werden muss, Sie zuerst ermitteln Sie, ob es bereits installiert ist, überprüfen Sie den Registrierungswert von HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
>  Diese Werte werden auch von der Shell-Erkennung-Block in Product.wxs gelesen.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder gibt den Speicherort, in dem die Visual Studio-Shell installiert wurde, und Sie können nach Dateien suchen.  
  
 Ein Beispiel dafür, wie eine Shell-Installation erkennen, finden Sie die `GetProductDirFromReg` Funktion der Utilities.cpp im Beispiel für den Shell-Bereitstellung.  
  
 Wenn eine oder beide der Visual Studio-Shells, die das Paket benötigte ist nicht auf dem Computer installiert, müssen Sie diese der Liste der zu installierenden Komponenten hinzufügen. Ein Beispiel finden Sie die `ComponentsPage::OnInitDialog` Funktion der ComponentsPage.cpp im Beispiel für den Shell-Bereitstellung.  
  
### <a name="running-the-shell-installers"></a>Die Shell Installationsprogramme ausgeführt  
 Führen Sie die Shell Installationsprogramme rufen Sie die Visual Studio-Shell verteilbare Komponenten mit den richtigen Befehlszeilenargumenten. Sie müssen mindestens die Befehlszeilenargumente verwenden **/q/norestart /** und sehen Sie sich für den Rückgabecode, um zu bestimmen, was als Nächstes ausgeführt werden soll. Im folgende Beispiel wird die Shell (isoliert) redistributable ausgeführt.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Die Shell Language Pack-Installer ausgeführt  
 Wenn Sie stattdessen feststellen, dass der-Shell oder Shells installiert wurde und nur ein Language pack muss, können Sie wie im folgenden Beispiel gezeigt die Sprachpakete installieren.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Rückgabewerte entschlüsseln  
 Bei einigen Betriebssystemen wird die Installation von Visual Studio Shell (isoliert) ein Neustart erforderlich. Diese Bedingung kann bestimmt werden, indem Sie den Rückgabecode des Aufrufs von `ExecCmd`.  
  
|Rückgabewert|Beschreibung|  
|------------------|-----------------|  
|ERROR_SUCCESS|Installation wurde abgeschlossen. Sie können nun Ihre Anwendung installieren.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Installation wurde abgeschlossen. Sie können Ihre Anwendung installieren, nach dem Neustart des Computers.|  
|3015|Installation läuft. Ein Neustart des Computers ist erforderlich, um die Installation fortzusetzen.|  
  
### <a name="handling-restarts"></a>Behandlung von Neustarts  
 Zeitpunkt der Ausführung der Shell-Installer mithilfe der **/norestart /** Argument angegeben, dass sie den Computer neu starten, oder bitten Sie für den Computer neu gestartet werden, wäre nicht. Jedoch möglicherweise ein Neustart erforderlich, und Sie müssen sicherstellen, dass das Installationsprogramm weiterhin nach dem Neustart des Computers.  
  
 Ordnungsgemäß behandeln kann neu gestartet wird, vergewissern Sie sich, nur ein Setupprogramm ist Set fortsetzen und der Prozess fortsetzen ordnungsgemäß behandelt werden.  
  
 Wenn ERROR_SUCCESS_REBOOT_REQUIRED oder 3015 zurückgegeben wird, sollte Code, den Computer neu, bevor die Installation fortgesetzt wird.  
  
 Um Neustarts zu behandeln, können führen Sie folgende Aktionen aus:  
  
-   Legen Sie die Registrierung, um die Installation fortsetzen, wenn Windows gestartet wird.  
  
-   Einen doppelten Neustart des Bootstrappers ausführen.  
  
-   Löschen Sie die Shell Installer ResumeData Schlüssel.  
  
-   Neustart von Windows.  
  
-   Setzen Sie den Startpfad, der die MSI-Datei zurück.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Festlegen der Registrierungs, um das Setup fortgesetzt wird, beim Starten von Windows  
 Der Registrierungsschlüssel HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ beim Systemstart mit Administratorberechtigungen ausgeführt wird und anschließend gelöscht wird. HKEY_CURRENT_USER einen ähnlichen Schlüssel enthält, aber er wird als normaler Benutzer ausgeführt und ist nicht für Installationen geeignet. Sie können die Installation fortsetzen, verlegen Sie einen Zeichenfolgenwert in den RunOnce-Schlüssel, der das Installationsprogramm aufruft. Allerdings wird empfohlen, dass Sie den Installer mit Aufrufen einer **/neu starten** oder ähnliche angeben, um die Anwendung zu benachrichtigen, die er statt fortgesetzt wird. Sie können auch Parameter enthalten, um anzugeben, in denen Sie während des Installationsvorgangs sind, vor allem hilfreich bei Installationen, die mehrere Neustarts erfordern kann.  
  
 Das folgende Beispiel zeigt eine RunOnce Werteintrag des Registrierungsschlüssels für die Installation fortsetzen.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Doppelte Neustart der Bootstrapper installieren  
 Wenn Setup direkt aus RunOnce verwendet wird, werden der Desktop kann nicht vollständig geladen. Um die vollständige Benutzeroberfläche verfügbar zu machen, müssen Sie erstellen eine weitere Ausführung des Setups und die RunOnce-Instanz zu beenden.  
  
 Sie müssen das Setup-Programm erneut ausführen, so, dass er die richtigen Berechtigungen erhält, und Sie sie genügend Informationen weisen müssen zu wissen, wo Sie vor dem Neustart, wie im folgenden Beispiel gezeigt wurde.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Beim Löschen des Shell-Installationsprogramm ResumeData-Schlüssels  
 Shell-Installationsprogramm legt den HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData-Registrierungsschlüssel mit Daten, um die Installation nach dem Neustart fortgesetzt. Da die Anwendung, die Shell-Installationsprogramm, fortgesetzt wird, löschen Sie diesen Registrierungsschlüssel, wie im folgenden Beispiel gezeigt.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Windows-Neustart  
 Nachdem Sie die erforderlichen Registrierungsschlüssel festgelegt haben, können Sie Windows neu starten. Im folgenden Beispiel wird die Neustart-Befehle für verschiedene Windows-Betriebssysteme.  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>Zurücksetzen des Start-Pfads der MSI-Datei  
 Das aktuelle Verzeichnis ist der Speicherort der Setup-Programm vor dem Neustart aber nach dem Neustart wird des Speicherorts dem Verzeichnis "System32". Das Setupprogramm muss das aktuelle Verzeichnis vor jedem Aufruf MSI-Datei wie im folgenden Beispiel gezeigt zurückgesetzt.  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>Ausführen der Anwendung MSI-Datei  
 Nachdem das Installationsprogramm von Visual Studio-Shell ERROR_SUCCESS zurückgegeben hat, können Sie die MSI-Datei für Ihre Anwendung ausführen. Da das Setupprogramm die Benutzeroberfläche bereitstellt, starten Sie die MSI-Datei im stillen Modus (**/q /**) und mit Protokollierung (**/l**), wie im folgende Beispiel gezeigt.  
  
```cpp  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer grundlegenden Isolated Shell-Anwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)