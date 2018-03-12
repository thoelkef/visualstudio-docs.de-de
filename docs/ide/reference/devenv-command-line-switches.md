---
title: Devenv-Befehlszeilenschalter in Visual Studio | Microsoft-Dokumentation
ms.date: 02/28/2018
ms.technology: vs-ide-general
ms.topic: article
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b507ff8710e3257f2da61a32baa81a18441c3aff
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="devenv-command-line-switches"></a>Devenv-Befehlszeilenschalter

Mit Devenv können Sie von der Befehlszeile aus verschiedene Optionen für die integrierte Entwicklungsumgebung (IDE) festlegen sowie Projekte erstellen, debuggen und bereitstellen. Verwenden Sie diese Schalter, um die IDE von einem Skript oder einer BAT-Datei aus auszuführen, z.B. einem über Nacht ausgeführten Buildskript, oder um die IDE in einer bestimmten Konfiguration zu starten.

> [!NOTE]
> Für buildbezogene Tasks wird empfohlen, dass Sie MSBuild anstelle von Devenv verwenden. Weitere Informationen finden Sie unter [MSBuild-Befehlszeilenreferenz](../../msbuild/msbuild-command-line-reference.md).

## <a name="devenv-switch-syntax"></a>Syntax des Devenv-Schalters

Devenv-Befehle übergeben Schalter standardmäßig an das Hilfsprogramm devenv.com. Das Hilfsprogramm „devenv.com“ stellt Ausgaben über standardmäßige Systemdatenströme bereit, z.B. `stdout` und `stderr`. Das Hilfsprogramm bestimmt die entsprechende E/A-Umleitung, wenn es die Ausgabe beispielsweise in einer TXT-Datei erfasst.

Befehle, die andererseits mit `devenv.exe` beginnen, können dieselben Schalter verwenden, das Hilfsprogramm „devenv.com“ wird jedoch umgangen.

Die Syntaxregeln für `devenv`-Schalter ähneln jenen für andere DOS-Befehlszeilenhilfsprogramme. Die folgenden Syntaxregeln gelten für alle `devenv`-Schalter und ihre Argumente:

- Befehle beginnen mit `devenv`.

- Bei Schaltern wird nicht zwischen Groß–/Kleinschreibung unterschieden.

- Bei Angabe einer Projektmappe oder eines Projekts ist das erste Argument der Name der Projektmappendatei oder der Projektdatei, einschließlich Dateipfad.

- Wenn das erste Argument eine Datei ist, die keine Projektmappe bzw. kein Projekt ist, wird die Datei im entsprechenden Editor in einer neuen Instanz der IDE geöffnet.

- Wenn Sie anstelle des Namens einer Projektmappendatei den einer Projektdatei angeben, wird der übergeordnete Ordner der Projektdatei von einem `devenv`-Befehl nach einer Projektmappendatei mit demselben Namen durchsucht. Beispielsweise durchsucht der Befehl `devenv /build myproject1.vbproj` den übergeordneten Ordner nach einer Projektmappendatei mit dem Namen „myproject1.sln“.

    > [!NOTE]
    > In diesem übergeordneten Ordner darf genau eine Projektmappendatei enthalten sein, die auf dieses Projekt verweist. Wenn der übergeordnete Ordner keine oder zwei bzw. mehr Projektmappendateien enthält, die auf das Projekt verweisen, wird in diesem Ordner eine temporäre Projektmappendatei erstellt.

- Dateipfade und Dateinamen, die Leerzeichen enthalten, müssen in Anführungszeichen ("") eingeschlossen werden. Zum Beispiel: „c:\Projekt A\\“.

- Fügen Sie zwischen Schaltern und Argumenten auf der gleichen Zeile ein Leerzeichen ein. Der Befehl **devenv /log output.txt** öffnet z.B. die IDE und gibt alle Protokollinformationen für diese Sitzung in „output.txt“ aus.

- In `devenv`-Befehlen kann keine Syntax zum Mustervergleich verwendet werden.

## <a name="devenv-switches"></a>Devenv-Schalter

Die folgenden Befehlszeilenschalter zeigen die IDE an und führen die beschriebene Aufgabe aus.

|Befehlszeilenschalter|description|
|-------------------------|-----------------|
|[/Command](../../ide/reference/command-devenv-exe.md)|Startet die IDE und führt den angegebenen Befehl aus.|
|[/DebugExe](../../ide/reference/debugexe-devenv-exe.md)|Lädt eine ausführbare C++-Datei unter der Kontrolle des Debuggers. Dieser Schalter ist für ausführbare Visual Basic- oder C#-Dateien nicht verfügbar. Weitere Informationen finden Sie unter [Prozess im Debugger automatisch starten](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|
|[/LCID oder /l](../../ide/reference/lcid-devenv-exe.md)|Legt die Standardsprache für die IDE fest. Wenn die angegebene Sprache in der Installation von Visual Studio nicht enthalten ist, wird diese Einstellung ignoriert.|
|[/Log](../../ide/reference/log-devenv-exe.md)|Startet Visual Studio und protokolliert sämtliche Aktivitäten in der Protokolldatei.|
|[/Run oder /r](../../ide/reference/run-devenv-exe.md)|Kompiliert die angegebene Projektmappe und führt sie aus.|
|[/Runexit](../../ide/reference/runexit-devenv-exe.md)|Kompiliert die angegebene Projektmappe und führt sie aus, minimiert die IDE bei der Ausführung der Projektmappe und schließt die IDE nach beendeter Ausführung der Projektmappe.|
|[/UseEnv](../../ide/reference/useenv-devenv-exe.md)|Führt dazu, dass die IDE für die C++-Kompilierung die Umgebungsvariablen PATH, INCLUDE und LIB anstelle der im Dialogfeld **Optionen** unter **Projekte** im Abschnitt „VC++-Verzeichnisse“ angegebenen Einstellungen verwendet. Dieser Schalter wird mit der Workload **Desktopentwicklung mit C++** installiert. Weitere Informationen finden Sie unter [Festlegen der Pfad- und Umgebungsvariablen für Befehlszeilenbuilds](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|
|[/Edit](../../ide/reference/edit-devenv-exe.md)|Öffnet die angegebenen Dateien in einer ausgeführten Instanz dieser Anwendung. Wenn keine ausgeführten Instanzen vorhanden sind, wird eine neue Instanz mit einem vereinfachten Fensterlayout gestartet.|
|[/SafeMode](../../ide/reference/safemode-devenv-exe.md)|Startet Visual Studio im abgesicherten Modus und lädt nur die Standardumgebung und die Standarddienste sowie im Lieferumfang enthaltene Versionen von Drittanbieterpaketen.|
|[/ResetSkipPkgs](../../ide/reference/resetskippkgs-devenv-exe.md)|Entfernt alle SkipLoading-Tags, die VSPackages von Benutzern hinzugefügt wurden, die das Laden von problematischen VSPackages verhindern möchten.|
|[/Setup](../../ide/reference/setup-devenv-exe.md)|Erzwingt, dass Ressourcenmetadaten zur Beschreibung von Menüs, Symbolleisten und Befehlsgruppen aus allen verfügbaren VSPackages von Visual Studio zusammengeführt werden. Sie müssen diesen Befehl als Administrator ausführen.|

Durch die folgenden Befehlszeilenschalter wird die IDE nicht angezeigt.

|Befehlszeilenschalter|description|
|-------------------------|-----------------|
|[/?](../../ide/reference/q-devenv-exe.md)|Zeigt Hilfe für devenv-Schalter im **Eingabeaufforderungsfenster** an.<br /><br /> **Devenv /?**|
|[/Build](../../ide/reference/build-devenv-exe.md)|Erstellt die angegebene Projektmappe oder das angegebene Projekt entsprechend der Konfiguration der angegebenen Projektmappe.<br /><br /> **Devenv myproj.csproj /build**|
|[/Clean](../../ide/reference/clean-devenv-exe.md)|Löscht vom Buildbefehl erstellte Dateien, ohne die Quelldateien zu beeinflussen.<br /><br /> **Devenv myproj.csproj /clean**|
|[/Deploy](../../ide/reference/deploy-devenv-exe.md)|Erstellt die Lösung mit für die Bereitstellung notwendigen Dateien gemäß der Lösungskonfiguration.<br /><br /> **Devenv myproj.csproj /deploy**|
|[/Diff](../../ide/reference/diff.md)|Vergleicht zwei Dateien. Benötigt vier Parameter: SourceFile, TargetFile, SourceDisplayName (optional), TargetDisplayName (optional).|
|[/Out](../../ide/reference/out-devenv-exe.md)|Ermöglicht die Angabe einer Datei für Fehlermeldungen, wenn ein Build erstellt wird.<br /><br /> **Devenv myproj.csproj /build /out log.txt**|
|[/Project](../../ide/reference/project-devenv-exe.md)|Das zu erstellende, bereinigende oder bereitzustellende Projekt. Dieser Schalter kann nur verwendet werden, wenn auch einer der Schalter /build, /rebuild, /clean oder /deploy angegeben wurde.|
|[/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)|Gibt die zu erstellende oder bereitzustellende Projektkonfiguration an. Dieser Schalter kann nur verwendet werden, wenn auch der Schalter /project angegeben wurde.|
|[/Rebuild](../../ide/reference/rebuild-devenv-exe.md)|Bereinigt die angegebene Projektmappe oder das angegebene Projekt und erstellt diese bzw. dieses entsprechend der Konfiguration der angegebenen Projektmappe durch.|
|[/ResetSettings](../../ide/reference/resetsettings-devenv-exe.md)|Stellt die Visual Studio-Standardeinstellungen wieder her. Setzt die Einstellungen optional auf die der angegebenen VSSETTINGS-Datei zurück.|
|[/Upgrade](../../ide/reference/upgrade-devenv-exe.md)|Aktualisiert die angegebene Projektmappendatei und alle zugehörigen Projektdateien bzw. die angegebene Projektdatei mit den aktuellen, für diese Dateien gültigen Visual Studio-Formaten.|

## <a name="see-also"></a>Siehe auch

* [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)