---
title: "Exemplarische Vorgehensweise: Erstellen einer Build-Umgebung für mehrere Computer | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
ms.assetid: ae5391b1-3eec-42f5-beb3-f28630615a9e
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 76b88d48b78ebab2058a2fa13feef327908f2b24
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2018
---
# <a name="walkthrough-creating-a-multiple-computer-build-environment"></a>Exemplarische Vorgehensweise: Erstellen einer Build-Umgebung für mehrere Computer

Sie können eine Buildumgebung in der Organisation erstellen, indem Sie Visual Studio auf einem Hostcomputer installieren und anschließend verschiedene Dateien und Einstellungen zu einem anderen Computer kopieren, sodass er mit den Builds verwendet werden kann. Visual Studio muss auf dem anderen Computer nicht installiert werden.  
  
Dieses Dokument berichtigt nicht zur externen Weiterverteilung der Software oder zum Bereitstellung der Buildumgebung an Drittanbieter.  
  
> Haftungsausschluss<br /><br /> Dieses Dokument wird wie besehen bereitgestellt. Obwohl die aufgeführten Schritte getestet wurden, kann nicht jede Konfiguration vollständig getestet werden. Wir bemühen uns, das Dokument mit jeder neugewonnenen Information aktuell zu halten. Die in diesen Unterlagen zum Ausdruck gebrachten Informationen und Ansichten, einschließlich URLs und anderer Verweise auf Internetwebsites, können ohne vorherige Ankündigung geändert werden. Microsoft gibt keine Garantie, weder ausdrücklich noch impliziert, hinsichtlich der hier bereitgestellten Informationen. Sie tragen das alleinige Verwendungsrisiko.<br /><br /> Dieses Dokument stellt keinerlei Rechtsansprüche auf geistiges Eigentum in Microsoft-Produkten jeglicher Art bereit. Sie dürfen Dokument für interne Informationszwecke kopieren.<br /><br /> Sie unterliegen keinerlei Verpflichtung, Microsoft Vorschläge, Kommentare oder anderes Feedback ("Feedback") in Bezug auf dieses Dokument zu unterbreiten. Jegliches von Ihnen freiwillig bereitstellte Feedback kann in Microsoft-Produkten und zugehöriger Spezifikation oder weiterer Dokumentationen (zusammen, "Microsoft-Angebote") die möglicherweise wiederum von weiteren Drittanbietern für die Entwicklung eigener Produkte genutzt werden. Bei Abgabe von Feedback an Microsoft zu jeglicher Version dieses Dokuments oder den Microsoft-Angeboten, für die diese gelten, stimmen Sie folgenden Punkten zu: (a) Microsoft darf Ihr Feedback frei verwenden, reproduzieren, lizenzieren verteilen und Ihr Feedback in jeglichen Microsoft-Angeboten auf andere Weise kommerziell im Handel nutzen; (b) Sie gewähren auch Drittanbietern gratis nur solche Patentrechte, die erforderlich sind, um anderen Produkte die Verwendung von bzw. das Herstellen einer Verbindung mit jeglichen spezifischen Teilen eines Microsoft-Produkts, für das Ihr Feedback genutzt wird, zu ermöglichen; und (c) Sie geben Microsoft kein Feedback, bei dem Sie (i) Anlass zur Annahme haben, dass es einem Patent, Urheberrecht, geistigem Eigentum oder den Rechten eines Drittanbieters unterliegt; oder dass es (ii) Lizenzbedingungen unterliegt, die erfordern, dass ein dieses Feedback integrierendes oder davon abgeleitetes Microsoft-Angebot, oder anderes geistiges Eigentum von Microsoft, lizenziert oder auf andere Art und Weise für Drittanbieter freigegeben wird.

Diese exemplarische Vorgehensweise ist für die folgenden Betriebssysteme überprüft worden, indem MSBuild auf der Befehlszeile ausgeführt und mit Team Foundation Build verwendet wurde.  
  
-   Windows 8 (x86 und x64)  
  
-   Windows 7 Ultimate  
  
-   Windows Server 2008 R2 Standard  
  
 Nachdem Sie die Schritte in dieser exemplarischen Vorgehensweise abgeschlossen haben, können Sie die Mehrcomputerumgebung zum Erstellen dieser Arten von Apps verwenden:  
  
-   C++-Desktop-Apps, die das Windows 8-SDK verwenden  
  
-   Visual Basic- oder C#-Desktop-Apps, die auf .NET Framework 4.5 ausgerichtet sind  
  
 Die Mehrcomputerumgebung kann nicht zum Erstellen dieser Arten von Apps verwendet werden:  
  
-   UWP-Apps. Zum Erstellen von UWP-Apps müssen Sie Visual Studio auf dem Buildcomputer installieren.  
  
-   Desktop-Apps, die auf .NET Framework 4 oder früher ausgerichtet sind. Um diese Arten von Apps zu erstellen, müssen Sie Visual Studio oder die .NET-Verweisassemblys und - Tools (aus dem Windows 7.1-SDK) auf dem Buildcomputer installieren.  
  
 Diese exemplarische Vorgehensweise ist in folgende Teile gegliedert:  
  
-   [Installieren von Software auf den Computern](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingSoftware)  
  
-   [Kopieren von Dateien vom Buildcomputer zum Hostcomputer](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles)  
  
-   [Erstellen von Registrierungseinstellungen](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingRegistry)  
  
-   [Einstellungsumgebungsvariablen auf dem Buildcomputer](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#SettingEnvVariables)  
  
-   [Installieren von MSBuild-Assemblys zum globalen Assemblycache (GAC) auf dem Buildcomputer](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)  
  
-   [Erstellen von Projekten](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#BuildingProjects)  
  
-   [Erstellen der Buildumgebung zum Einchecken in die Quellcodeverwaltung](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingForSourceControl)  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
-   Eine lizenzierte Kopie von Visual StudioUltimate, Visual Studio Premium oder Visual Studio Professional  
  
-   Eine Kopie des .NET Framework 4.5.1, das Sie von der [Visual Studio](http://www.microsoft.com/visualstudio/eng/downloads#d-additional-software)-Website herunterladen können.  
  
##  <a name="InstallingSoftware"></a> Installieren von Software auf den Computern  
 Richten Sie zunächst den Hostcomputer ein, und installieren Sie anschließend den Buildcomputer.  
  
 Mit der Installation von Visual Studio auf dem Hostcomputer werden die Dateien und Einstellungen, die Sie später auf den Buildcomputer kopieren, erstellt. Sie können Visual Studio auf x86- oder x64-Computern installieren, die Architektur des Buildcomputers muss allerdings mit der Architektur des Hostcomputers übereinstimmen.  
  
#### <a name="to-install-software-on-the-computers"></a>So installieren Sie Software auf den Computern  
  
1.  Installieren Sie Visual Studio auf dem Hostcomputer.  
  
2.  Installieren Sie .NET Framework 4.5 auf dem Buildcomputer. Um zu überprüfen, dass es installiert wurde, stellen Sie sicher, dass der Wert des Registrierungsschlüssels HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full@Version mit „4,5“ beginnt.  
  
##  <a name="CopyingFiles"></a> Kopieren von Dateien vom Buildcomputer zum Hostcomputer  
 In diesem Abschnitt wird das Kopieren bestimmter Dateien, Compilern, Buildtools, MSBuild-Ressourcen und von Registrierungseinstellungen vom Hostcomputer zum Buildcomputer behandelt. Bei diesen Anweisungen wird vorausgesetzt, dass Visual Studio auf dem Hostcomputer im Standardspeicherort installiert wurde. Wurde es in einem anderen Speicherort installiert, passen Sie die Schritte entsprechend an.  
  
-   Auf einem x86-Computer lautet der Standardspeicherort "C:\Programme\Microsoft Visual Studio 11.0 \"  
  
-   Auf einem x64-Computer lautet der Standardspeicherort "C:\Programme (x86)\Microsoft Visual Studio 11.0 \"  
  
 Beachten Sie, dass der Name des Programmdateiordners vom installierten Betriebssystem abhängt. Auf einem x86-Computer lautet der Name \Programme\\; auf einem x64-Computer lautet der Name \Programme(x86)\\. Ungeachtet der Systemarchitektur wird der Ordner "Programme" in dieser exemplarischen Vorgehensweise als "%ProgramFiles%" bezeichnet.  
  
> [!NOTE]
>  Auf dem Buildcomputer müssen sich alle relevanten Dateien auf dem gleichen Laufwerk befinden. Der Laufwerkbuchstabe des Laufwerks darf sich allerdings von dem Laufwerkbuchstaben für das Laufwerk, in dem Visual Studio auf dem Hostcomputer installiert ist, unterscheiden. Auf jeden Fall müssen Sie den Speicherort der Dateien berücksichtigen, wenn Sie , wie weiter unten in diesem Dokument beschrieben, Registrierungseinträge erstellen.  
  
#### <a name="to-copy-the-windows-sdk-files-to-the-build-computer"></a>So kopieren Sie die Windows SDK-Dateien auf den Buildcomputer  
  
1.  Ist nur das Windows SDK für Windows 8 installiert, kopieren Sie diese Ordner rekursiv vom Hostcomputer auf den Buildcomputer:  
  
    -   %ProgramFiles%\Windows Kits\8.0\bin\  
  
    -   %ProgramFiles%\Windows Kits\8.0\Catalogs\  
  
    -   %ProgramFiles%\Windows Kits\8.0\DesignTime\  
  
    -   %ProgramFiles%\Windows Kits\8.0\include\  
  
    -   %ProgramFiles%\Windows Kits\8.0\Lib\  
  
    -   %ProgramFiles%\Windows Kits\8.0\Redist\  
  
    -   %ProgramFiles%\Windows Kits\8.0\References\  
  
     Wenn Sie über weitere Windows 8-Kits verfügen...  
  
    -   Microsoft Windows Assessment and Deployment Kit  
  
    -   Microsoft Windows-Treiberkit  
  
    -   Microsoft Windows Hardware Certification Kit  
  
     ... wurden möglicherweise Dateien in die Ordner "%ProgramFiles%\Windows Kits\8.0\" installiert, die im vorherigen Schritt aufgeführt wurden, und ihre Lizenzbedingungen gestatten möglicherweise keine Buildserverrechte für diese Dateien. Überprüfen Sie die Lizenzbestimmungen für jedes installierte Windows-Kit, um zu überprüfen, ob möglicherweise Dateien auf den Buildcomputer kopiert wurden. Wenn die Lizenzbestimmungen keine Buildserverrechte ermöglichen, entfernen Sie die Dateien vom Buildcomputer.  
  
2.  Kopieren Sie die folgenden Ordner rekursiv vom Hostcomputer auf den Buildcomputer:  
  
    -   %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\  
  
    -   %ProgramFiles%\Common Files\Merge Modules\  
  
    -   %ProgramFiles%\Microsoft Visual Studio 11.0\VC\  
  
    -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\ProjectComponents\  
  
    -   %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\V110\  
  
    -   %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5\  
  
    -   %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\.NETFramework\v4.5\  
  
3.  Kopieren Sie diese Dateien vom Hostcomputer auf den Buildcomputer:  
  
    -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\msobj110.dll  
  
    -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdb110.dll  
  
    -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdbcore.dll  
  
    -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdbsrv.exe  
  
    -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\msvcdis110.dll  
  
    -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\makehm.exe  
  
    -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\VCVarsQueryRegistry.bat  
  
    -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\vsvars32.bat  
  
4.  Die folgenden Visual C++-Laufzeitbibliotheken sind nur erforderlich, wenn Sie Buildausgaben auf den Build Computer ausführen. z. B. als Teil automatisierter Tests. Die Dateien befinden sich abhängig von der Systemarchitektur in der Regel in Unterordnern unter dem Ordner "%ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x86" oder dem Ordner "%ProgramFiles%\ Microsoft Visual Studio 11.0\VC\redist\x64\". Kopieren Sie die x86-Binärdateien auf x86-Systemen in den Ordner "\Windows\ System32\". Kopieren Sie die x86-Binärdateien auf x64-Systemen in den Ordner "Windows\SysWOW64\" und die x64-Binärdateien in den Ordner "Windows\System32\".  
  
    -   \Microsoft.VC110.ATL\atl110.dll  
  
    -   \Microsoft.VC110.CRT\msvcp110.dll  
  
    -   \Microsoft.VC110.CRT\msvcr110.dll  
  
    -   \Microsoft.VC110.CXXAMP\vcamp110.dll  
  
    -   \Microsoft.VC110.MFC\mfc110.dll  
  
    -   \Microsoft.VC110.MFC\mfc110u.dll  
  
    -   \Microsoft.VC110.MFC\mfcm110.dll  
  
    -   \Microsoft.VC110.MFC\mfcm110u.dll  
  
    -   \Microsoft.VC110.MFCLOC\mfc110chs.dll  
  
    -   \Microsoft.VC110.MFCLOC\mfc110cht.dll  
  
    -   \Microsoft.VC110.MFCLOC\mfc110deu.dll  
  
    -   \Microsoft.VC110.MFCLOC\mfc110enu.dll  
  
    -   \Microsoft.VC110.MFCLOC\mfc110esn.dll  
  
    -   \Microsoft.VC110.MFCLOC\mfc110fra.dll  
  
    -   \Microsoft.VC110.MFCLOC\mfc110ita.dll  
  
    -   \Microsoft.VC110.MFCLOC\mfc110jpn.dll  
  
    -   \Microsoft.VC110.MFCLOC\mfc110kor.dll  
  
    -   \Microsoft.VC110.MFCLOC\mfc110rus.dll  
  
    -   \Microsoft.VC110.OPENMP\vcomp110.dll  
  
5.  Kopieren Sie die folgenden Dateien aus dem Ordner „Debug_NonRedist\x86\“ oder dem Ordner „\Debug_NonRedist\x64\“ wie in [Vorbereiten eines Testcomputers zum Ausführen einer ausführbaren Debugdatei](/cpp/ide/preparing-a-test-machine-to-run-a-debug-executable) beschrieben zum Buildcomputer. Keine anderen Dateien dürfen kopiert werden.  
  
    -   \Microsoft.VC110.DebugCRT\msvcp110d.dll  
  
    -   \Microsoft.VC110.DebugCRT\msvcr110d.dll  
  
    -   \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll  
  
    -   \Microsoft.VC110.DebugMFC\mfc110d.dll  
  
    -   \Microsoft.VC110.DebugMFC\mfc110ud.dll  
  
    -   \Microsoft.VC110.DebugMFC\mfcm110d.dll  
  
    -   \Microsoft.VC110.DebugMFC\mfcm110ud.dll  
  
    -   \Microsoft.VC110.DebugOpenMP\vcomp110d.dll  
  
##  <a name="CreatingRegistry"></a> Erstellen von Registrierungseinstellungen  
 Sie müssen zum Konfigurieren von Einstellungen für MSBuild Registrierungseinträge erstellen.  
  
#### <a name="to-create-registry-settings"></a>So erstellen Sie Registrierungseinstellungen  
  
1.  Identifizieren Sie den übergeordneten Ordner für Registrierungseinträge. Alle Registrierungseinträge werden unter dem gleichen übergeordneten Schlüssel erstellt. Auf einem x86-Computer lautet der übergeordnete Schlüssel „HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Auf einem x64-Computer lautet der übergeordnete Schlüssel „HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\“. Ungeachtet der Systemarchitektur wird der übergeordnete Schlüssel in dieser exemplarischen Vorgehensweise als "%RegistryRoot%" bezeichnet.  
  
    > [!NOTE]
    >  Wenn sich die Architektur des Hostcomputers von der Ihres Buildcomputers unterscheidet, stellen Sie sicher, dass der entsprechende übergeordneten Schlüssel auf jedem Computer verwendet wird. Dies ist insbesondere dann wichtig, wenn Sie den Exportvorgang automatisieren.  
    >   
    >  Wenn Sie auf dem Buildcomputer zudem einen anderen Laufwerkbuchstaben als auf dem Hostcomputer verwenden, stellen Sie sicher, die Registrierungseinträge entsprechend zu ändern, damit sie übereinstimmen.  
  
2.  Erstellen Sie auf dem Buildcomputer die folgenden Registrierungseinträge. Alle diese Einträge sind Zeichenfolgen (Typ "== REG_SZ" in der Registrierung). Legen Sie die Werte dieser Einträge entsprechend der Werte der vergleichbaren Einträge auf dem Hostcomputer fest.  
  
    -   %RegistryRoot%\\.NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild Public Assemblies@(Default)  
  
    -   %RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder  
  
    -   %RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder  
  
    -   %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder  
  
    -   %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder  
  
    -   %RegistryRoot%\VisualStudio\11.0@Source Directories  
  
    -   %RegistryRoot%\VisualStudio\11.0\Setup\VC@ProductDir  
  
    -   %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir32  
  
    -   %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir64  
  
    -   %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer32  
  
    -   %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer64  
  
    -   %RegistryRoot%\VisualStudio\SxS\VC7@11.0  
  
    -   %RegistryRoot%\VisualStudio\SxS\VS7@11.0  
  
    -   %RegistryRoot%\Windows Kits\Installed Roots@KitsRoot  
  
    -   %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath  
  
    -   %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10  
  
    -   %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11  
  
     Auf einem x64-Buildcomputer erstellen Sie zudem folgenden Registrierungseintrag und beachten den Hostcomputer, um zu bestimmen, wie diese festzulegen sind.  
  
    -   %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder  
  
     Wenn es sich um einen x64-Buildcomputer handelt und Sie die 64-Bit-Version von MSBuild verwenden möchten, oder wenn Sie einem Team Foundation Server-Builddienst auf einem x64-Computer verwenden, müssen die folgenden Registrierungseinträgen in der nativen 64-Bit-Registrierung erstellt werden. Beziehen Sie sich auf den Hostcomputer, um zu bestimmen, wie diese Einträge festzulegen sind.  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11  
  
##  <a name="SettingEnvVariables"></a> Einstellungsumgebungsvariablen auf dem Buildcomputer  
 Um MSBuild auf dem Buildcomputer zu verwenden, müssen die PATH-Umgebungsvariablen festgelegt werden. Sie können "vcvarsall.bat" zum Festlegen der Variablen verwenden, oder sie können sie manuell konfigurieren.  
  
#### <a name="to-use-vcvarsallbat-to-set-environment-variables"></a>So verwenden Sie "vcvarsall.bat" zum Festlegen der Umgebungsvariablen  
  
-   Öffnen Sie auf dem Buildcomputer ein Eingabeaufforderungsfenster und führen Sie "%Program Files%\Microsoft Visual Studio 11.0\VC\vcvarsall.bat" aus. Sie können ein Befehlszeilenargument verwenden, um das Toolset, das Sie verwenden möchten, anzugeben: "x86", "systemeigenes x64" oder "x64-Cross-Compiler". Wenn Sie kein Befehlszeilenargument angeben, wird das x86-Toolset verwendet.  
  
     In dieser Tabelle werden die unterstützten Argumente für "vcvarsall.bat" beschrieben:  
  
    |Vcvarsall.bat-Argument|Compiler|Buildcomputerarchitektur|Buildausgabearchitektur|  
    |----------------------------|--------------|---------------------------------|-------------------------------|  
    |x86 (Standard)|32-Bit systemeigen|x86, x64|x86|  
    |x86_amd64|x64 Cross|x86, x64|x64|  
    |amd64|x64 (Systemeigen)|x64|x64|  
  
     Wenn „vcvarsall.bat“ erfolgreich ausgeführt wird, d.h., es werden keine Fehlermeldung angezeigt, können Sie den nächsten Schritt überspringen und mit dem Abschnitt [Installieren von MSBuild-Assemblys auf den globalen Assemblycache (GAC) auf dem Buildcomputer](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC) dieses Dokuments fortfahren.   
  
#### <a name="to-manually-set-environment-variables"></a>So legen Sie Umgebungsvariablen manuell fest  
  
1.  Zur manuellen Konfiguration der Befehlszeilenumgebung fügen Sie der PATH-Umgebungsvariable diesen Pfad hinzu:  
  
    -   %Program Files%\Microsoft Visual Studio 11.0\Common7\IDE  
  
2.  Optional können Sie der PATH-Variable auch die folgenden Pfade hinzufügen, um die Verwendung von MSBuild zum Erstellen der Lösungen zu vereinfachen.  
  
     Wenn Sie das systemeigene MSBuild mit 32-Bit verwenden möchten, fügen Sie der PATH-Variable diese Pfade hinzu:  
  
    -   %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools  
  
    -   %windir%\Microsoft.NET\Framework\v4.0.30319  
  
     Wenn Sie das native MSBuild mit 64-Bit verwenden möchten, fügen Sie der PATH-Variable diese Pfade hinzu:  
  
    -   %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\x64  
  
    -   %windir%\Microsoft.NET\Framework64\v4.0.30319  
  
##  <a name="InstallingMSBuildToGAC"></a> Installieren von MSBuild-Assemblys zum globalen Assemblycache (GAC) auf dem Buildcomputer  
 Für MSBuild ist die Installation einiger zusätzlicher Assemblys zum GAC auf dem Buildcomputer erforderlich.  
  
#### <a name="to-copy-assemblies-from-the-host-computer-and-install-them-on-the-build-computer"></a>So kopieren Sie Assemblys vom Hostcomputer und installieren sie auf dem Buildcomputer  
  
1.  Kopieren Sie die folgenden Assamblys vom Hostcomputer auf den Buildcomputer. Da sie zum GAC installiert werden, ist es nicht unerheblich, wo die Assemblys auf dem Buildcomputer gespeichert werden.  
  
    -   %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll  
  
    -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll  
  
    -   %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll  
  
2.  Um die Assemblys zum GAC zu installieren, suchen Sie auf dem Buildcomputer die Datei „gacutil.exe“. In der Regel befindet sie sich unter „%ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\\“. Wenn Sie diesen Ordner nicht finden können, wiederholen Sie die Schritte aus dem Abschnitt [Kopieren von Dateien vom Buildcomputer zum Hostcomputer](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) dieser exemplarischen Vorgehensweise.  
  
     Öffnen Sie ein Eingabeaufforderungsfenster mit Administratorrechten und führen Sie für jede Datei diesen Befehl aus:  
  
     **gacutil -i \<file>**  
  
    > [!NOTE]
    >  Möglicherweise ist zum vollständigen Installieren einer Assembly in den GAC ein Neustart erforderlich.  
  
##  <a name="BuildingProjects"></a> Erstellen von Projekten  
 Sie können Team Foundation Build zum Erstellen von [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]-Projekten und Projektmappen verwenden, oder Sie können sie in der Befehlszeile erstellen. Bei der Verwendung von Team Foundation Build zum Erstellen von Projekten wird die der Systemarchitektur entsprechende ausführbare MSBuild-Datei aufgerufen.  In der Befehlszeile können Sie entweder die MSBuild-Version mit 32-Bit oder mit 64-Bit verwenden, und Sie können die MSBuild-Architektur auswählen, indem Sie die PATH-Umgebungsvariable festlegen oder direkt die architekturspezifische ausführbare MSBuild-Datei aufrufen.  
  
 Führen Sie zum Verwenden von „msbuild.exe“ an der Eingabeaufforderung den folgenden Befehl aus, wobei *solution.sln* ein Platzhalter für den Namen der Projektmappe ist.  
  
 **msbuild** *solution.sln*  
  
 Weitere Informationen zum Verwenden von MSBuild an der Befehlszeile finden Sie unter [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md)  
  
> [!NOTE]
>  Zum Erstellen von [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]-Projekten müssen Sie die "v110"-Plattform Toolsets verwenden. Wenn Sie die [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]-Projektdateien nicht bearbeiten möchten, können Sie die Plattform Toolset mithilfe dieses Befehlszeilenarguments festlegen:  
>   
>  **msbuild** *solution.sln* **/p:PlatformToolset=v110**  
  
##  <a name="CreatingForSourceControl"></a> Erstellen der Buildumgebung zum Einchecken in die Quellcodeverwaltung  
 Sie können eine Buildumgebung erstellen, die auf verschiedenen Computern bereitgestellt werden kann, ohne dass Dateien in den GAC installiert oder Registrierungseinstellungen geändert werden müssen. Die folgenden Schritte stellen nur eine Möglichkeit dar, das zu erreichen. Passen Sie diese Schritte den eindeutigen Eigenschaften der aktuellen Buildumgebung an.  
  
> [!NOTE]
>  Sie müssen den inkrementellen Buildvorgang deaktivieren, sodass von der Datei "tracker.exe" während eines Builds kein Fehler ausgelöst wird. Legen Sie zum Deaktivieren des inkrementellen Buildvorgangs diesen Buildparameter fest:  
>   
>  **msbuild** *solution.sln* **/p:TrackFileAccess=false**  
  
#### <a name="to-create-a-build-environment-that-can-be-checked-into-source-control"></a>So erstellen Sie eine Buildumgebung, die in die Quellcodeverwaltung eingecheckt werden kann  
  
1.  Erstellen Sie auf dem Hostcomputer ein "Depot"-Verzeichnis.  
  
     Diese Schritte beziehen auf das Verzeichnis als %Depot%.  
  
2.  Kopieren Sie die Verzeichnisse und Dateien wie im Abschnitt [Kopieren von Dateien vom Buildcomputer zum Hostcomputer](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) dieser exemplarischen Vorgehensweise beschrieben, aber fügen Sie sie unter dem grade von Ihnen erstellte Verzeichnis %Depot% ein. Kopieren Sie aus „%ProgramFiles%\Windows Kits\8.0\bin\“ z.B. nach „%Depot%\Windows Kits\8.0\bin\\“.  
  
3.  Wenn die Dateien unter "%Depot%" eingefügt wurden, nehmen Sie folgende Änderungen vor:  
  
    -   Ändern Sie unter „%Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets\\“, „\Microsoft.cppbuild.targets\\“ und „\Microsoft.CppCommon.targets\\“ jede Instanz von  
  
         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
  
         auf  
  
         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".  
  
         Die frühere Benennung beruht auf der Tatsache, dass die Assembly in den GAC installiert wird.  
  
    -   Ändern Sie unter %Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets, jede Instanz von  
  
         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
  
         auf  
  
         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".  
  
4.  Erstellen Sie eine PROPS-Datei, z. B. Partner.AutoImports.props, - und legen Sie sie im Stammverzeichnis des Ordners ab, in dem die Projekte enthalten sind. Diese Datei wird zum Festlegen der Variablen verwendet, die von MSBuild zum Suchen verschiedene Ressourcen verwendet werden. Wenn die Variablen von dieser Datei nicht festgelegt werden, werden sie von anderen PROPS- und TARGETS-Dateien festgelegt, die auf Registrierungswerten basieren. Da keine Registrierungswerte festlegt werden, wären diese Variablen leer und der Build würde einen Fehler verursachen. Fügen Sie stattdessen der Datei "Partner.AutoImports.props" Folgendes hinzu:  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <!-- This file must be imported by all project files at the top of the project file. -->  
    <Project ToolsVersion="4.0"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>  
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>  
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>  
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>  
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio 11.0\VC\</VCInstallDir_110>  
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>  
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>  
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>  
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>  
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>  
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>  
    </PropertyGroup>  
    </Project>  
    ```  
  
5.  Fügen Sie in jeder Projektdatei oben nach der `<Project Default Targets...>`-Zeile folgende Zeile hinzu.  
  
    ```  
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>  
    ```  
  
6.  Ändern Sie die Befehlszeilenumgebung, wie folgt:  
  
    -   Set Depot=*Speicherort des Depot-Verzeichnisses, das Sie in Schritt 1 erstellt haben*  
  
    -   Set path=%path%;*Ort von MSBuild auf dem Computer*;%Depot%\Windows\System32;%Depot%\Windows\SysWOW64;%Depot%\Microsoft Visual Studio 11.0\Common7\IDE\  
  
         Für systemeigenes Erstellen mit 64-Bit, zeigen Sie auf MSBuild mit 64-Bit.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorbereiten eines Testcomputers zum Ausführen einer ausführbaren Debugdatei](/cpp/ide/preparing-a-test-machine-to-run-a-debug-executable)   
 [Command-Line Reference](../msbuild/msbuild-command-line-reference.md) (MSBuild-Befehlszeilenreferenz)