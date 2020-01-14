---
title: Installieren einer isolierten Shellanwendung | Microsoft-Dokumentation
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
ms.openlocfilehash: 0adc81cfe9ea4462940c31a02c6429be89709565
ms.sourcegitcommit: 9a66f1c31cc9eba0b5231af72da1d18761a9c56a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2020
ms.locfileid: "75944265"
---
# <a name="installing-an-isolated-shell-application"></a>Installieren einer Anwendung der isolierten Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zum Installieren einer Shell-App müssen Sie die folgenden Schritte ausführen.  
  
- Bereiten Sie die Lösung vor.  
  
- Erstellen Sie ein Windows Installer-Paket (MSI) für die Anwendung.  
  
- Erstellen eines Setup-Boots Trappers  
  
  Der gesamte Beispielcode in diesem Dokument stammt aus dem [shellbereitstellungsbeispiel](https://code.msdn.microsoft.com/Sample-setup-program-for-81ca73f7), das Sie aus der Code Galerie auf der MSDN-Website herunterladen können. Das Beispiel zeigt die Ergebnisse der Ausführung der einzelnen Schritte.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um die in diesem Thema beschriebenen Verfahren auszuführen, müssen die folgenden Tools auf dem Computer installiert sein.  
  
- Visual Studio SDK  
  
- Die [Windows Installer XML-Toolsetversion](https://documentation.help/WiX-Toolset/index.html/) 3,6  
  
  Das Beispiel erfordert auch das Microsoft-Visualisierungs-und Modellierungs-SDK, das nicht für alle Shells erforderlich ist.  
  
## <a name="preparing-your-solution"></a>Vorbereiten der Lösung  
 Standardmäßig werden shellvorlagen in VSIX-Paketen erstellt, aber dieses Verhalten ist hauptsächlich für Debugzwecke vorgesehen. Wenn Sie eine Shellanwendung bereitstellen, müssen Sie MSI-Pakete verwenden, um den Registrierungs Zugriff und die Neustarts während der Installation zuzulassen. Führen Sie die folgenden Schritte aus, um die Anwendung für die MSI-Bereitstellung vorzubereiten.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>So bereiten Sie eine Shellanwendung für MSI-Bereitstellung vor  
  
1. Bearbeiten Sie jede vsixmanifest-Datei in der Projekt Mappe.  
  
     Fügen Sie im `Identifier`-Element ein `InstalledByMSI`-Element und ein `SystemComponent`-Element hinzu, und legen Sie dann deren Werte auf `true`fest.  
  
     Diese Elemente verhindern, dass der VSIX-Installer versucht, die Komponenten zu installieren, und der Benutzer wird daran gehindert, Sie mithilfe des Dialog Felds **Erweiterungen und Updates** zu deinstallieren.  
  
2. Bearbeiten Sie für jedes Projekt, das ein VSIX-Manifest enthält, die Buildaufgaben, um den Inhalt an den Speicherort auszugeben, von dem die MSI-Datei installiert wird. Schließen Sie das VSIX-Manifest in die Buildausgabe ein, erstellen Sie jedoch keine vsix-Datei.  
  
## <a name="creating-an-msi-for-your-shell"></a>Erstellen einer MSI für Ihre Shell  
 Zum Erstellen des MSI-Pakets wird empfohlen, dass Sie das [Windows Installer XML-Toolset](https://documentation.help/WiX-Toolset/index.html) verwenden, da es größere Flexibilität bietet als ein Standard-Setup-Projekt.  
  
 Legen Sie in der Datei "Product. wxs" Erkennungs Blöcke und das Layout von Shellkomponenten fest.  
  
 Erstellen Sie dann Registrierungseinträge, sowohl in der reg-Datei für die Projekt Mappe als auch in der Datei "ApplicationRegistry. wxs".  
  
### <a name="detection-blocks"></a>Erkennungs Blöcke  
 Ein Erkennungs Block besteht aus einem `Property`-Element, das eine erforderliche Voraussetzung angibt, und ein `Condition` Element, das eine Meldung angibt, die zurückgegeben werden soll, wenn die Voraussetzung auf dem Computer nicht vorhanden ist. Beispielsweise ist für Ihre Shellanwendung die weitervertreibbare Microsoft Visual Studio Shell erforderlich, und der Erkennungs Block ähnelt dem folgenden Markup.  
  
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
  
### <a name="layout-of-shell-components"></a>Layout von Shellkomponenten  
 Sie müssen Elemente hinzufügen, um die Zielverzeichnis Struktur und die zu installierende Komponenten zu identifizieren.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>So legen Sie das Layout von Shellkomponenten fest  
  
1. Erstellen Sie eine Hierarchie von `Directory` Elementen, die alle Verzeichnisse darstellt, die im Dateisystem auf dem Zielcomputer erstellt werden sollen, wie im folgenden Beispiel gezeigt.  
  
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
  
     Auf diese Verzeichnisse wird `Id` verwiesen, wenn Dateien angegeben werden, die installiert werden müssen.  
  
2. Identifizieren Sie die Komponenten, die für die Shell und die Shellanwendung erforderlich sind, wie im folgenden Beispiel gezeigt.  
  
    > [!NOTE]
    > Einige Elemente können auf Definitionen in anderen wxs-Dateien verweisen.  
  
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
  
    1. Das `ComponentRef`-Element verweist auf eine andere wxs-Datei, mit der die von der aktuellen Komponente benötigten Dateien identifiziert werden. Beispielsweise hat generalprofile die folgende Definition in helpabout. wxs.  
  
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
  
         Das `DirectoryRef` Element gibt an, wo sich diese Dateien auf dem Computer des Benutzers befinden. Das `Directory`-Element gibt an, dass es in einem Unterverzeichnis installiert wird, und jedes `File` Element stellt eine Datei dar, die erstellt wurde oder als Teil der Projekt Mappe vorhanden ist, und gibt an, wo diese Datei beim Erstellen der MSI-Datei gefunden werden kann.  
  
    2. Das `ComponentGroupRef`-Element verweist auf eine Gruppe anderer Komponenten (oder Komponenten und Komponenten Gruppen). Beispielsweise wird `ComponentGroupRef` unter ApplicationGroup in "Application. wxs" wie folgt definiert.  
  
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
    > Erforderliche Abhängigkeiten für Shell (isolierte) Anwendungen sind: debuggerproxy, masterpkgdef, Ressourcen (insbesondere die winprf-Datei), Application und pkgdefs.  
  
### <a name="registry-entries"></a>Registrierungseinträge  
 Die Projektvorlage "Shell (isoliert)" enthält die Datei " *ProjectName*. reg" für Registrierungsschlüssel, die bei der Installation zusammengeführt werden sollen. Diese Registrierungseinträge müssen sowohl bei der Installation als auch bei der Bereinigung Teil der MSI-Version sein. Außerdem müssen Sie in der Datei "ApplicationRegistry. wxs" übereinstimmende Registrierungs Blöcke erstellen.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>So integrieren Sie Registrierungseinträge in die MSI  
  
1. Öffnen Sie im Ordner **shellanpassung** den Ordner *ProjectName*. reg.  
  
2. Ersetzen Sie alle Instanzen des $RootFolder $-Tokens durch den Pfad des Ziel Installationsverzeichnisses.  
  
3. Fügen Sie alle anderen Registrierungseinträge hinzu, die für die Anwendung erforderlich sind.  
  
4. Öffnen Sie die Datei "ApplicationRegistry. wxs".  
  
5. Fügen Sie für jeden Registrierungs Eintrag in *ProjectName*. reg einen entsprechenden Registrierungs Block hinzu, wie in den folgenden Beispielen gezeigt.  
  
    |*ProjectName*. reg|Applicationregisty. wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @ = "PhotoStudio DTE-Objekt"|\<RegistryKey ID = ' dteclsidregkey ' root = ' HKCR ' Key = ' $ (var. Dteclsidregkey) ' Action = ' "|" kreateandremuveonuninstall "><br /><br /> \<REGISTRYVALUE Type = ' String ' Name = ' @ ' value = ' $ (var. ShortProductName) DTE-Objekt '/><br /><br /> \</RegistryKey>|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}\LocalServer32]<br /><br /> @="$RootFolder$\PhotoStudio.exe"|\<RegistryKey ID = ' DteLocSrv32RegKey ' root = ' HKCR ' Key = ' $ (var. Dteclsidregkey) \LocalServer32 ' Action = ' kreateandremuveonuninstall ' ><br /><br /> \<REGISTRYVALUE Type = ' String ' Name = ' @ ' value = ' [INSTALLDIR] $ (var). ShortProductName). exe '/><br /><br /> \</RegistryKey>|  
  
     In diesem Beispiel wird var. dteclsidregkey in den Registrierungsschlüssel in der obersten Zeile aufgelöst. "Var. ShortProductName" wird in "`PhotoStudio`" aufgelöst.  
  
## <a name="creating-a-setup-bootstrapper"></a>Erstellen eines Setup-Boots Trappers  
 Die abgeschlossene MSI-Installation wird nur dann installiert, wenn alle erforderlichen Komponenten zuerst installiert werden. Um die Benutzerfreundlichkeit zu vereinfachen, erstellen Sie ein Setup Programm, das alle Voraussetzungen sammelt und installiert, bevor die Anwendung installiert wird. Führen Sie die folgenden Aktionen aus, um eine erfolgreiche Installation zu gewährleisten:  
  
- Erzwingen Sie die Installation durch den Administrator.  
  
- Erkennen, ob die Visual Studio Shell (isoliert) installiert ist.  
  
- Führen Sie einen oder beide shellinstaller in der richtigen Reihenfolge aus.  
  
- Verarbeiten von Neustart Anforderungen.  
  
- Führen Sie die MSI aus.  
  
### <a name="enforcing-installation-by-administrator"></a>Erzwingen der Installation durch den Administrator  
 Dieses Verfahren ist erforderlich, damit das Setup Programm auf erforderliche Verzeichnisse wie z. b. "\Programme\\" zugreifen kann.  
  
##### <a name="to-enforce-installation-by-administrator"></a>So erzwingen Sie die Installation durch den Administrator  
  
1. Öffnen Sie das Kontextmenü für das Setup-Projekt, und wählen Sie dann **Eigenschaften**aus.  
  
2. Legen Sie unter **Konfigurations Eigenschaften/Linker/Manifest-Datei**die **UAC-Ausführungs Ebene** auf **requiinfoministrator**fest.  
  
     Mit dieser Eigenschaft wird das Attribut, das das Programm erfordert, als Administrator in der eingebetteten Manifest-Datei ausgeführt.  
  
### <a name="detecting-shell-installations"></a>Erkennen von shellinstallationen  
 Um zu ermitteln, ob die Visual Studio Shell (isoliert) installiert werden muss, ermitteln Sie zunächst, ob Sie bereits installiert ist, indem Sie den Registrierungs Wert hklm\software\microsoft\devdiv\vs\servicing\shellversion\isoshell\lcid\install überprüfen.  
  
> [!NOTE]
> Diese Werte werden auch vom shellerkennungs Block in "Product. wxs" gelesen.  
  
 Hklm\software\microsoft\appenv\14.0\shellfolder gibt den Speicherort an, an dem die Visual Studio-Shell installiert wurde, und Sie können dort nach Dateien suchen.  
  
 Ein Beispiel zum Erkennen einer Shellinstallation finden Sie in der `GetProductDirFromReg`-Funktion von Utilities. cpp im Beispiel zur shellbereitstellung.  
  
 Wenn mindestens eine der Visual Studio-Shells, die das Paket erfordert, nicht auf dem Computer installiert ist, müssen Sie Sie der Liste der zu installierenden Komponenten hinzufügen. Ein Beispiel finden Sie in der `ComponentsPage::OnInitDialog`-Funktion von "componentspage. cpp" im shellbereitstellungsbeispiel.  
  
### <a name="running-the-shell-installers"></a>Ausführen der Shell-Installationsprogramme  
 Um die Shell-Installationsprogramme auszuführen, müssen Sie die setzungen von Visual Studio Shell mithilfe der korrekten Befehlszeilenargumente abrufen. Sie müssen mindestens die Befehlszeilenargumente **/norestart/q** verwenden und auf den Rückgabecode achten, um zu bestimmen, was als Nächstes geschehen soll. Im folgenden Beispiel wird die verteilbare Shell (isoliert) ausgeführt.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Ausführen der Shell Language Pack-Installationsprogramme  
 Wenn Sie stattdessen feststellen, dass die Shell oder Shells installiert sind und nur ein Sprachpaket benötigt werden, können Sie die Sprachpakete installieren, wie im folgenden Beispiel gezeigt.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Entschlüsseln von Rückgabe Werten  
 Bei einigen Betriebssystemen ist für die Installation von Visual Studio Shell (isoliert) ein Neustart erforderlich. Diese Bedingung kann durch den Rückgabecode des Aufruf`ExecCmd`bestimmt werden.  
  
|Rückgabewert|Beschreibung|  
|------------------|-----------------|  
|ERROR_SUCCESS|Die Installation wurde abgeschlossen. Sie können nun Ihre Anwendung installieren.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Die Installation wurde abgeschlossen. Nachdem der Computer neu gestartet wurde, können Sie die Anwendung installieren.|  
|3015|Die Installation wird durchgeführt. Zum Fortsetzen der Installation ist ein Neustart des Computers erforderlich.|  
  
### <a name="handling-restarts"></a>Behandeln von Neustarts  
 Wenn Sie den shellinstaller mithilfe des **/norestart** -Arguments ausgeführt haben, haben Sie festgelegt, dass der Computer nicht neu gestartet oder der Computer neu gestartet werden soll. Möglicherweise ist jedoch ein Neustart erforderlich, und Sie müssen sicherstellen, dass das Installationsprogramm nach dem Neustart des Computers fortgesetzt wird.  
  
 Um Neustarts ordnungsgemäß zu behandeln, stellen Sie sicher, dass nur ein Setup Programm fortgesetzt werden kann und dass der Fortschritt ordnungsgemäß verarbeitet wird.  
  
 Wenn ERROR_SUCCESS_REBOOT_REQUIRED oder 3015 zurückgegeben wird, sollte Ihr Code den Computer neu starten, bevor die Installation fortgesetzt wird.  
  
 Führen Sie zum Verarbeiten von Neustarts folgende Aktionen aus:  
  
- Legen Sie fest, dass die Registrierung beim Start von Windows fortgesetzt wird.  
  
- Führen Sie einen doppelten Neustart des Boots Trappers aus.  
  
- Löschen Sie den Schlüssel "Shell Installer resumedata".  
  
- Starten Sie Windows neu.  
  
- Setzen Sie den Startpfad der MSI zurück.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Festlegen der Registrierung zum Fortsetzen des Setups beim Starten von Windows  
 Der Registrierungsschlüssel HKEY_LOCAL_MACHINE \software\microsoft\windows\currentversion\runonce\ wird beim Systemstart mit Administrator Berechtigungen ausgeführt und dann gelöscht. HKEY_CURRENT_USER enthält einen ähnlichen Schlüssel, wird aber als normaler Benutzer ausgeführt und ist nicht für Installationen geeignet. Sie können die Installation fortsetzen, indem Sie einen Zeichen folgen Wert in den RunOnce-Schlüssel einfügen, der das Installationsprogramm aufruft. Es wird jedoch empfohlen, dass Sie den Installer mit einem **/Restart ein** -Parameter oder einem ähnlichen Parameter aufrufen, um die Anwendung darüber zu benachrichtigen, dass Sie fortgesetzt wird, anstatt zu starten. Sie können auch Parameter einschließen, um anzugeben, wo Sie sich im Installationsprozess befinden. Dies ist besonders nützlich bei Installationen, die möglicherweise mehrere Neustarts erfordern.  
  
 Das folgende Beispiel zeigt einen RunOnce-Registrierungsschlüssel Wert zum Fortsetzen einer-Installation.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Installieren eines doppelten Neustarts des Boots Trappers  
 Wenn das Setup direkt von RunOnce verwendet wird, kann der Desktop nicht vollständig geladen werden. Um die vollständige Benutzeroberfläche verfügbar zu machen, müssen Sie eine weitere Ausführung des Setups erstellen und die RunOnce-Instanz beenden.  
  
 Sie müssen das Setup Programm erneut ausführen, damit es die richtigen Berechtigungen erhält, und Sie müssen genügend Informationen angeben, um zu wissen, wo Sie vor dem Neustart angehalten haben, wie im folgenden Beispiel gezeigt.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Löschen des "Shell Installer resumedata"-Schlüssels  
 Das Shell-Installationsprogramm legt den Registrierungsschlüssel hklm\software\microsoft\visualstudio\14.0\setup\resumedata auf Daten fest, um Setup nach dem Neustart fortzusetzen. Da Ihre Anwendung, nicht das Shell-Installationsprogramm, fortgesetzt wird, löschen Sie diesen Registrierungsschlüssel, wie im folgenden Beispiel gezeigt.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Neustarten von Windows  
 Nachdem Sie die erforderlichen Registrierungsschlüssel festgelegt haben, können Sie Windows neu starten. Im folgenden Beispiel werden die Neustart Befehle für verschiedene Windows-Betriebssysteme aufgerufen.  
  
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
  
### <a name="resetting-the-start-path-of-msi"></a>Zurücksetzen des Start Pfads von MSI  
 Vor dem Neustart ist das aktuelle Verzeichnis der Speicherort des Setup Programms, aber nach dem Neustart wird der Speicherort zum Verzeichnis "System32". Das Setup Programm sollte das aktuelle Verzeichnis vor jedem MSI-Befehl Zurücksetzen, wie im folgenden Beispiel gezeigt.  
  
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
  
### <a name="running-the-application-msi"></a>Ausführen der MSI für die Anwendung  
 Nachdem der Visual Studio Shell-Installer ERROR_SUCCESS zurückgegeben hat, können Sie die MSI-Datei für Ihre Anwendung ausführen. Da das Setup Programm die Benutzeroberfläche bereitstellt, starten Sie die MSI im stillen Modus ( **/q**) und mit der Protokollierung ( **/L**), wie im folgenden Beispiel gezeigt.  
  
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
