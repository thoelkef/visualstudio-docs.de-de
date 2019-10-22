---
title: Devenv-Befehlszeilenschalter | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- builds [Team System], command-line
- applications [Visual Studio], executing
- compiling source code, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
- environment, Devenv commands
- compilers, Devenv commands
- switches
- Devenv, syntax and list of switches
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b8b0683024e2881f76bb6c54d9420d351fced08a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668727"
---
# <a name="devenv-command-line-switches"></a>Devenv-Befehlszeilenschalter
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mit Devenv können Sie von der Befehlszeile aus verschiedene Optionen für die integrierte Entwicklungsumgebung (IDE) festlegen sowie Projekte erstellen, debuggen und bereitstellen. Verwenden Sie diese Schalter, um die IDE von einem Skript oder einer BAT-Datei aus auszuführen, z. B. einem über Nacht ausgeführten Buildskript, oder um die IDE in einer bestimmten Konfiguration zu starten.

> [!NOTE]
> Für buildbezogene Aufgaben wird jetzt empfohlen, dass Sie MSBuild anstelle von Devenv verwenden. Weitere Informationen finden Sie unter [Befehlszeilenreferenz](../../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> Sie müssen „devenv“ als Administrator ausführen, um die Schalter [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) und [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) verwenden zu können.

## <a name="devenv-switch-syntax"></a>Syntax des Devenv-Schalters
 Devenv-Befehle übergeben Schalter standardmäßig an das Hilfsprogramm devenv.com.

 Das Hilfsprogramm devenv.com ermöglicht das Senden von Ausgabedaten über standardmäßige Systemstreams, z. B. `stdout` und `stderr`, und ermittelt beim Erfassen von Ausgabedaten die entsprechende E/A-Umleitung, beispielsweise in eine TXT-Datei. Befehle, die stattdessen mit `devenv.exe` beginnen, können dieselben Schalter verwenden, senden diese jedoch unter Umgehung des Hilfsprogramms devenv.com an das Programm devenv.exe.

 Die Syntaxregeln für `devenv`-Schalter ähneln jenen für andere DOS-Befehlszeilenhilfsprogramme. Die folgenden Syntaxregeln gelten für alle `devenv`-Schalter und ihre Argumente:

- Befehle beginnen mit `devenv`.

- Bei Schaltern wird nicht zwischen Groß–/Kleinschreibung unterschieden.

- Bei Angabe einer Projektmappe oder eines Projekts ist das erste Argument der Name der Projektmappendatei oder der Projektdatei, einschließlich Dateipfad.

- Wenn das erste Argument eine Datei ist, die keine Projektmappe bzw. kein Projekt ist, wird die Datei im entsprechenden Editor in einer neuen Instanz der IDE geöffnet.

- Wenn Sie anstelle des Namens einer Projektmappendatei den einer Projektdatei angeben, wird der übergeordnete Ordner der Projektdatei von einem `devenv`-Befehl nach einer Projektmappendatei mit demselben Namen durchsucht. Beispielsweise durchsucht der Befehl `devenv /build myproject1.vbproj` den übergeordneten Ordner nach einer Projektmappendatei mit dem Namen "myproject1.sln".

    > [!NOTE]
    > In diesem übergeordneten Ordner darf genau eine Projektmappendatei enthalten sein, die auf dieses Projekt verweist. Wenn der übergeordnete Ordner keine oder zwei bzw. mehr Projektmappendateien enthält, die auf das Projekt verweisen, wird in diesem Ordner eine temporäre Projektmappendatei erstellt, die entsprechend dem Projekt benannt wird und darauf verweist.

- Dateipfade und Dateinamen, die Leerzeichen enthalten, müssen in doppelte Anführungszeichen ("") eingeschlossen werden. Zum Beispiel: „c:\Projekt A\\“.

- Fügen Sie zwischen Schaltern und Argumenten auf der gleichen Zeile ein Leerzeichen ein. Der Befehl **devenv /log output.txt** öffnet z.B. die IDE und gibt alle Protokollinformationen für diese Sitzung in „output.txt“ aus.

- In `devenv`-Befehlen kann keine Syntax zum Mustervergleich verwendet werden.

## <a name="devenv-switches"></a>Devenv-Schalter
 Verwenden Sie die folgenden Befehlszeilenschalter, um die IDE anzuzeigen und die beschriebene Aufgabe auszuführen.

|Befehlszeilenschalter|BESCHREIBUNG|
|-------------------------|-----------------|
|[/Command (devenv.exe)](../../ide/reference/command-devenv-exe.md)|Startet die IDE und führt den angegebenen Befehl aus.|
|[/DebugExe (devenv.exe)](../../ide/reference/debugexe-devenv-exe.md)|Lädt eine ausführbare [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Datei unter der Kontrolle des Debuggers. Dieser Schalter ist für ausführbare [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]- oder [!INCLUDE[csprcs](../../includes/csprcs-md.md)]-Dateien nicht verfügbar. Weitere Informationen finden Sie unter [Prozess im Debugger automatisch starten](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|
|[/LCID (devenv.exe)](../../ide/reference/lcid-devenv-exe.md) oder `/l`|Legt die Standardsprache für die IDE fest. Wenn die angegebene Sprache in der Installation von Visual Studio nicht enthalten ist, wird die Einstellung ignoriert.|
|[/Log (devenv.exe)](../../ide/reference/log-devenv-exe.md)|Startet [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und protokolliert sämtliche Aktivitäten in der Protokolldatei.|
|[/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) oder `/r`|Kompiliert die angegebene Projektmappe und führt sie aus.|
|[/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)|Kompiliert die angegebene Projektmappe und führt sie aus, minimiert die IDE bei der Ausführung der Projektmappe und schließt die IDE nach beendeter Ausführung der Projektmappe.|
|[/UseEnv (devenv.exe)](../../ide/reference/useenv-devenv-exe.md)|Führt dazu, dass die IDE für die [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Kompilierung die Umgebungsvariablen PATH, INCLUDE und LIB anstelle der im Dialogfeld **Optionen** unter **Projekte** im Abschnitt „VC++-Verzeichnisse“ angegebenen Einstellungen verwendet. Weitere Informationen finden Sie unter [Festlegen der Pfad- und Umgebungsvariablen für Befehlszeilenbuilds](https://msdn.microsoft.com/library/99389528-deb5-43b9-b99a-03c8773ebaf4).|
|[/Edit (devenv.exe)](../../ide/reference/edit-devenv-exe.md)|Öffnet die angegebenen Dateien in einer ausgeführten Instanz dieser Anwendung. Wenn keine ausgeführten Instanzen vorhanden sind, wird eine neue Instanz mit einem vereinfachten Fensterlayout gestartet.|
|[/ResetAddin (devenv.exe)](../../ide/reference/resetaddin-devenv-exe.md)|Startet eine Instanz der Visual Studio IDE, ohne das angegebene Add-In zu laden.|
|[/SafeMode (devenv.exe)](../../ide/reference/safemode-devenv-exe.md)|Startet [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] im abgesicherten Modus und lädt nur die Standardumgebung und die Standarddienste sowie im Lieferumfang enthaltene Versionen von Drittanbieterpaketen.|
|[/ResetSkipPkgs (devenv.exe)](../../ide/reference/resetskippkgs-devenv-exe.md)|Entfernt alle SkipLoading-Tags, die VSPackages von Benutzern hinzugefügt wurden, die das Laden von problematischen VSPackages verhindern möchten.|
|[/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md)|Erzwingt, dass Ressourcenmetadaten zur Beschreibung von Menüs, Symbolleisten und Befehlsgruppen aus allen verfügbaren VSPackages von Visual Studio zusammengeführt werden.|

 Verwenden Sie die folgenden Befehlszeilenschalter, um die beschriebene Aufgabe auszuführen. Durch diese Befehlszeilenschalter wird die IDE nicht angezeigt.

|Befehlszeilenschalter|BESCHREIBUNG|
|-------------------------|-----------------|
|[/? (devenv.exe)](../../ide/reference/q-devenv-exe.md)|Zeigt Hilfe für devenv-Schalter im **Eingabeaufforderungsfenster** an.<br /><br /> **Devenv /?**|
|[/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)|Erstellt die angegebene Projektmappe oder das angegebene Projekt entsprechend der Konfiguration der angegebenen Projektmappe.<br /><br /> **Devenv myproj.csproj /build**|
|[/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)|Löscht vom Buildbefehl erstellte Dateien, ohne die Quelldateien zu beeinflussen.<br /><br /> **Devenv myproj.csproj /clean**|
|[/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)|Erstellt die Lösung mit für die Bereitstellung notwendigen Dateien gemäß der Lösungskonfiguration.<br /><br /> **Devenv myproj.csproj /deploy**|
|[/Diff](../../ide/reference/diff.md)|Vergleicht zwei Dateien.  Benötigt vier Parameter:SourceFile, TargetFile, SourceDisplayName(optional),TargetDisplayName(optional).|
|[/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md)|Registriert unter „ *\<VisualStudioInstallDir>* \Common7\IDE\ProjectTemplates“ oder „ *\<VisualStudioInstallDir>* \Common7\IDE\ItemTemplates“ gespeicherte Projekt- oder Elementvorlagen, damit in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** darauf zugegriffen werden kann.<br /><br /> **Devenv /InstallVSTemplates**|
|[/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)|Ermöglicht die Angabe einer Datei für Fehlermeldungen, wenn ein Build erstellt wird.<br /><br /> **Devenv myproj.csproj /build /out log.txt**|
|[/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)|Das zu erstellende, bereinigende oder bereitzustellende Projekt. Dieser Schalter kann nur verwendet werden, wenn auch einer der Schalter /build, /rebuild, /clean oder /deploy angegeben wurde.|
|[/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)|Gibt die zu erstellende oder bereitzustellende Projektkonfiguration an. Dieser Schalter kann nur verwendet werden, wenn auch der Schalter /project angegeben wurde.|
|[/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)|Bereinigt die angegebene Projektmappe oder das angegebene Projekt und erstellt diese bzw. dieses entsprechend der Konfiguration der angegebenen Projektmappe durch.|
|[/ResetSettings (devenv.exe)](../../ide/reference/resetsettings-devenv-exe.md)|Stellt die Visual Studio-Standardeinstellungen wieder her. Setzt die Einstellungen optional auf die der angegebenen VSSETTINGS-Datei zurück.|
|[/Updateconfiguration (devenv.exe)](../../ide/reference/updateconfiguration-devenv-exe.md)|Teilt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mit, die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Pakete auf dem System zusammenzuführen und den MEF-Cache auf Änderungen zu prüfen.|
|[/Upgrade (devenv.exe)](../../ide/reference/upgrade-devenv-exe.md)|Aktualisiert die angegebene Projektmappendatei und alle zugehörigen Projektdateien bzw. die angegebene Projektdatei mit den aktuellen, für diese Dateien gültigen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Formaten.|

## <a name="see-also"></a>Siehe auch
 [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)
