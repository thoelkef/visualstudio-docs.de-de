---
title: Installieren einer Isolated Shell-Anwendung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c288da9345435969f7843f753625ce5471bb1878
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958342"
---
# <a name="installing-an-isolated-shell-application"></a>Installieren einer Isolated Shell-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um eine Shell-app installieren müssen Sie die folgenden Schritte ausführen.  
  
- Bereiten Sie Ihre Lösung vor.  
  
- Erstellen Sie eine Windows Installer (MSI)-Paket für Ihre Anwendung.  
  
- Erstellen Sie einen Setup-Bootstrapper.  
  
  Alle dem Beispielcode in diesem Dokument stammen aus der [Beispiel für die Anwendungsbereitstellung Shell](http://go.microsoft.com/fwlink/?LinkId=262245), die Sie in der Code Gallery auf der MSDN-Website herunterladen können. Das Beispiel zeigt die Ergebnisse der einzelnen Schritte durchführen.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen der Schritte, die in diesem Thema wird beschrieben, müssen die folgenden Tools auf Ihrem Computer installiert werden.  
  
- Visual Studio SDK  
  
- Die [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) Version 3.6  
  
  Das Beispiel erfordert auch die Microsoft Visualization und Modellierungs-SDK, die nicht alle Shells erforderlich ist.  
  
## <a name="preparing-your-solution"></a>Ihre Projektmappe wird vorbereitet  
 In der Standardeinstellung Shell-Vorlagen zum VSIX-Pakete erstellen, aber dieses Verhalten ist in erster Linie für Debugzwecke vorgesehen. Wenn Sie eine Shell-Anwendung bereitstellen, müssen Sie die MSI-Pakete verwenden, um für den Zugriff auf die Registrierung und Neustart während der Installation zu ermöglichen. Um Ihre Anwendung für die MSI-Bereitstellung vorzubereiten, führen Sie die folgenden Schritte aus.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>So bereiten Sie eine Shell-Anwendung für die MSI-Bereitstellung vor  
  
1.  Bearbeiten Sie jede vsixmanifest-Datei in der Projektmappe.  
  
     In der `Identifier` -Element, Hinzufügen einer `InstalledByMSI` Element und ein `SystemComponent` -Element, und legen Sie deren Werte auf `true`.  
  
     Diese Elemente verhindern, dass das VSIX-Installationsprogramm versuchen, die Ihre Komponenten und der Benutzer zu installieren, nicht deinstalliert werden, mithilfe der **Erweiterungen und Updates** Dialogfeld.  
  
2.  Bearbeiten Sie für jedes Projekt, das eine VSIX-Manifest enthält die Buildaufgaben, um den Inhalt, der den Speicherort auszugeben, von dem Ihre MSI installiert wird. Schließen Sie das VSIX-Manifest in die Buildausgabe, aber erstellen Sie eine VSIX-Datei nicht.  
  
## <a name="creating-an-msi-for-your-shell"></a>Erstellen eine MSI-Datei für die Shell  
 Um Ihr MSI-Paket zu erstellen, wird empfohlen, Sie verwenden die [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=82720) , da dadurch mehr Flexibilität als eine standard-Setup-Projekt.  
  
 Legen Sie in der Datei Product.wxs Erkennung Blöcke und das Layout der Komponenten aus.  
  
 Erstellen Sie Registrierungseinträge, klicken Sie dann sowohl in die REG-Datei für Ihre Lösung auch in ApplicationRegistry.wxs.  
  
### <a name="detection-blocks"></a>Erkennung von Blöcken  
 Ein Block Erkennung besteht aus einem `Property` Element, das eine Voraussetzung für die Erkennung angibt und ein `Condition` -Element, das gibt eine Meldung zurückgegeben, wenn die erforderliche Komponente nicht auf dem Computer vorhanden ist. Z. B. Ihre Shell-Anwendung muss Microsoft Visual Studio Shell redistributable und der Block für die Erkennung wird das folgende Markup ähneln.  
  
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
 Sie müssen die Elemente, die zum Identifizieren der Ziel-Verzeichnisstruktur und die zu installierenden Komponenten hinzufügen.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Das Layout der Komponenten festlegen.  
  
1.  Erstellen Sie eine Hierarchie von `Directory` Elemente alle Verzeichnisse im Dateisystem auf dem Zielcomputer erstellen, wie im folgenden Beispiel gezeigt dargestellt.  
  
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
  
     Diese Verzeichnisse zu verdanken `Id` bei Dateien, die installiert werden müssen angegeben werden.  
  
2.  Identifizieren Sie die Komponenten, die die Shell und Ihre Shell-Anwendung, wie im folgenden Beispiel gezeigt erfordern.  
  
    > [!NOTE]
    >  Einige Elemente können sich auf Definitionen in anderen Dateien WXS beziehen.  
  
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
  
    1.  Die `ComponentRef` Element verweist auf eine andere WXS-Datei, die Dateien identifiziert, die die aktuelle Komponente erforderlich sind. GeneralProfile weist z. B. folgende Definition in HelpAbout.wxs an.  
  
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
  
         Die `DirectoryRef` Element gibt an, wo diese Dateien auf dem Computer des Benutzers. Die `Directory` Element gibt an, dass es in ein Unterverzeichnis, und jeder installiert wird `File` -Element stellt dar, eine Datei, der erstellt wurde, oder, die als Teil der Lösung vorhanden ist, und identifiziert, in dem diese Datei die Erstellung der MSI-Datei gefunden werden kann.  
  
    2.  Die `ComponentGroupRef` Element verweist auf eine Gruppe von anderen Komponenten (oder -Komponenten und Komponentengruppen). Z. B. `ComponentGroupRef` unter ApplicationGroup ist wie folgt definiert in Application.wxs.  
  
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
    >  Erforderliche Abhängigkeiten für die Shell (isoliert)-Anwendungen sind: DebuggerProxy, MasterPkgDef, Ressourcen (insbesondere die .winprf-Datei), Anwendung und PkgDefs.  
  
### <a name="registry-entries"></a>Registrierungseinträge  
 Die Shell (isoliert)-Projektvorlage enthält ein *ProjectName*reg-Datei für die Registrierungsschlüssel für die Installation zusammenführen. Diese Registrierungseinträge müssen die MSI-Datei für die Installation und Bereinigung Zwecke angehören. Außerdem müssen Sie entsprechende Registrierung Blöcke in ApplicationRegistry.wxs erstellen.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Integrieren Sie Registrierungseinträge in die MSI-Datei  
  
1.  In der **Shell Anpassung** Ordner *ProjectName*. reg.  
  
2.  Ersetzen Sie alle Instanzen des Tokens $ $RootFolder, durch den Pfad des Ziel-Installationsverzeichnisses.  
  
3.  Fügen Sie keine andere Registrierungseinträge, die Ihre Anwendung erforderlich sind.  
  
4.  Öffnen Sie ApplicationRegistry.wxs.  
  
5.  Für jeden Registrierungseintrag in *ProjectName*reg, fügen Sie als das folgende Beispiel zeigt einen entsprechenden Block für die Registrierung hinzu.  
  
    |*ProjectName*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @="PhotoStudio DTE Object"|\<RegistryKey Id='DteClsidRegKey' Root='HKCR' Key='$(var.DteClsidRegKey)' Action='createAndRemoveOnUninstall'><br /><br /> \<RegistryValue Typ = 'String' Name =' @' Wert = "$(" var ". ShortProductName) DTE-Objekt "/ ><br /><br /> \</RegistryKey>|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}\LocalServer32]<br /><br /> @="$RootFolder$\PhotoStudio.exe"|\<RegistryKey Id='DteLocSrv32RegKey' Root='HKCR' Key='$(var.DteClsidRegKey)\LocalServer32' Action='createAndRemoveOnUninstall'><br /><br /> \<RegistryValue Typ = 'String' Name = "@" Wert = "[INSTALLATIONSVERZEICHNIS] $(" var ". ShortProductName) .exe "/ ><br /><br /> \</RegistryKey>|  
  
     In diesem Beispiel löst Var.DteClsidRegKey in den Registrierungsschlüssel in der obersten Zeile auf. Var.ShortProductName löst in `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Erstellen einen Setup-Bootstrapper  
 Der vollständige MSI installiert nur dann, wenn zunächst die erforderlichen Komponenten installiert sind. Um die Endbenutzer zu vereinfachen, erstellen Sie ein Setupprogramm, das erfasst und alle erforderlichen Komponenten installiert, bevor sie Ihre Anwendung installiert. Um eine erfolgreiche Installation sicherzustellen, müssen führen Sie folgende Aktionen aus:  
  
-   Die Installation von Administrator zu erzwingen.  
  
-   Erkennen Sie, ob Visual Studio Shell (isoliert) installiert ist.  
  
-   Führen Sie eine oder beide Shell-Installationsprogramme in der Reihenfolge an.  
  
-   Verarbeiten Sie Neustart-Anfragen.  
  
-   Führen Sie die MSI-Datei.  
  
### <a name="enforcing-installation-by-administrator"></a>Erzwingen der Installation von Administrator  
 Dieses Verfahren ist erforderlich, aktivieren Sie das Setup-Programm den Zugriff auf erforderliche Verzeichnisse wie z. B. \Program Files\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Installation vom Administrator erzwungen werden  
  
1.  Öffnen Sie das Kontextmenü für das Setup-Projekt, und wählen Sie dann **Eigenschaften**.  
  
2.  Klicken Sie unter **Konfigurationsdatei für die Eigenschaften/Linker/Manifest**legen **UAC-Ausführungsebene** zu **"requireAdministrator"**.  
  
     Diese Eigenschaft legt das Attribut, das das Programm als Administrator ausgeführt werden soll, in der eingebetteten manifest-Datei erforderlich ist.  
  
### <a name="detecting-shell-installations"></a>Erkennen von Shell-Installationen  
 Um zu bestimmen, ob Visual Studio Shell (isoliert) installiert werden müssen, sollten Sie zunächst zu bestimmen, ob es bereits installiert ist, anhand des Registrierungswerts von HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
>  Diese Werte werden auch vom Shell-Erkennung im Product.wxs Block gelesen werden.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder gibt den Speicherort der Visual Studio-Shell installiert wurde, und sehen Sie sich für die Dateien an.  
  
 Ein Beispiel wie eine Shellinstallation erkannt wird, finden Sie unter den `GetProductDirFromReg` Funktion der Utilities.cpp im Beispiel-Shell-Bereitstellung.  
  
 Wenn mindestens eines der Visual Studio-Shells, die Ihr Paket erfordert, ist nicht auf dem Computer installiert, müssen Sie diese der Liste der zu installierenden Komponenten hinzufügen. Ein Beispiel finden Sie unter den `ComponentsPage::OnInitDialog` Funktion der ComponentsPage.cpp im Beispiel-Shell-Bereitstellung.  
  
### <a name="running-the-shell-installers"></a>Die Shell-Installer ausführen  
 Führen Sie die Shell-Installationsprogramme rufen Sie die Visual Studio Shell verteilbaren Komponenten mit den richtigen Befehlszeilenargumenten. Sie müssen mindestens die Befehlszeilenargumente verwenden **/q/norestart /** und sehen Sie sich für den Rückgabecode, um zu bestimmen, was als Nächstes ausgeführt werden soll. Im folgende Beispiel wird die Shell (isoliert) redistributable ausgeführt.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Die Shell Language Pack-Installer ausführen  
 Wenn Sie stattdessen feststellen, dass der Shell oder Shells installiert wurde, und nur ein Language pack muss-, können Sie die Language Packs installieren, wie im folgenden Beispiel gezeigt.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Entschlüsselt die Rückgabe von Werten  
 Bei einigen Betriebssystemen wird die Visual Studio Shell (isoliert)-Installation ein Neustart erforderlich. Diese Bedingung kann bestimmt werden, indem Sie den Rückgabecode des Aufrufs von `ExecCmd`.  
  
|Rückgabewert|Beschreibung|  
|------------------|-----------------|  
|ERROR_SUCCESS|Installation wurde abgeschlossen. Sie können nun Ihre Anwendung installieren.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Installation wurde abgeschlossen. Sie können Ihre Anwendung installieren, nach dem Neustart des Computers.|  
|3015|Installation wird ausgeführt. Ein Neustart des Computers ist erforderlich, um die Installation fortzusetzen.|  
  
### <a name="handling-restarts"></a>Behandeln von Neustarts  
 Beim Ausführen der Shell-Installer mithilfe der **/norestart /** Argument angegeben, dass sie den Computer neu starten oder bitten Sie für den Computer neu gestartet werden, wäre nicht. Jedoch kann ein Neustart erforderlich sein, und Sie müssen sicherstellen, dass Ihr Installer weiterhin nach dem Neustart des Computers.  
  
 Neustart ordnungsgemäß behandeln, vergewissern Sie sich, nur eine Setup-Programm ist auf fortsetzen und der Prozess fortsetzen ordnungsgemäß behandelt werden.  
  
 Wenn entweder ERROR_SUCCESS_REBOOT_REQUIRED oder 3015 zurückgegeben wird, sollten Ihren Code auf den Computer neu, bevor die Installation fortgesetzt wird.  
  
 Um Neustarts zu behandeln, können führen Sie folgende Aktionen aus:  
  
-   Legen Sie den Registrierungsschlüssel, die Installation fortgesetzt, wenn Windows gestartet wird.  
  
-   Führen Sie den Bootstrapper doppelte neu gestartet.  
  
-   Löschen Sie die Shell Installer ResumeData-Schlüssel.  
  
-   Starten Sie Windows neu.  
  
-   Setzen Sie den Startpfad, der die MSI-Datei zurück.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Festlegen der Registrierungs, um das Setup fortgesetzt werden soll, wenn Windows gestartet wird.  
 Der Registrierungsschlüssel HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ beim Systemstart mit Administratorberechtigungen ausgeführt wird und anschließend gelöscht wird. HKEY_CURRENT_USER einen ähnlichen Schlüssel enthält, aber es als normaler Benutzer ausgeführt wird und nicht für Installationen geeignet. Sie können die Installation fortsetzen, indem Sie dies ist einen Zeichenfolgenwert in den RunOnce-Schlüssel, der das Installationsprogramm aufruft. Allerdings wird empfohlen, dass Sie den Installer mit Aufrufen einer **/restart** oder ähnliche Parameter an die Anwendung zu benachrichtigen, die sie statt der Wiederaufnahme. Sie können auch Parameter zum angeben, wo Sie bei der Installation, handelt es sich insbesondere für Installationen, die ggf. mehrere Neustarts erfordert einschließen.  
  
 Das folgende Beispiel zeigt eine RunOnce-Registrierungsschlüsselwert für eine Installation fortsetzen.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Doppelte Neustart des Bootstrappers installieren  
 Wenn Setup direkt über RunOnce verwendet wird, werden der Desktop kann nicht vollständig geladen. Um die vollständige Benutzeroberfläche verfügbar zu machen, müssen Sie erstellen eine weitere Ausführung des Setups und die RunOnce-Instanz zu beenden.  
  
 Sie müssen das Setup-Programm erneut ausführen, damit er die erforderlichen Berechtigungen erhält, und sie genügend Informationen vermitteln müssen, zu wissen, in denen Sie vor dem Neustart, wie im folgenden Beispiel gezeigt wurde beendet.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Die Shell Installer ResumeData-Schlüssel wird gelöscht.  
 Das Shell-Installationsprogramm legt fest, den HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData-Registrierungsschlüssel mit Daten, um nach dem Neustart das Setup fortsetzen. Da es sich bei der Wiederaufnahme Ihrer Anwendung, die nicht im Shell-Installer, löschen Sie diesen Registrierungsschlüssel, wie im folgenden Beispiel gezeigt.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Neustarten von Windows  
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
 Das aktuelle Verzeichnis ist der Speicherort der Ihrem Setup-Programm vor dem Neustart aber nach dem Neustart wird des Speicherorts das Verzeichnis "System32". Das Setupprogramm sollten das aktuelle Verzeichnis vor jedem Aufruf des MSI-Datei, wie im folgenden Beispiel gezeigt zurücksetzen.  
  
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
 Nachdem das Installationsprogramm für Visual Studio Shell ERROR_SUCCESS zurückgegeben hat, können Sie die MSI-Datei für Ihre Anwendung ausführen. Da das Setupprogramm die Benutzeroberfläche bereitstellt, starten Sie Ihre MSI-Datei im stillen Modus (**/q /**) und mit der Protokollierung (**/l**), wie im folgende Beispiel gezeigt.  
  
```cpp#  
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
