---
title: DevEnv-Schalter „ProjectConfig“
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44f5d4479658b450074ba35f2759a273bb584e0a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764653"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Gibt eine Projektbuildkonfiguration an, die beim Erstellen, Bereinigen, Neuerstellen oder Bereitstellen des im **/project**-Argument benannten Projekts angewendet werden soll.

## <a name="syntax"></a>Syntax

```cmd
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumente

|||
|-|-|
|/build|Erstellt das durch das **/project**-Argument angegebene Projekt.|
|/clean|Bereinigt alle Zwischendateien und Ausgabeverzeichnisse, die während eines Builds erstellt werden|
|/rebuild|Bereinigt das durch das **/project**-Argument angegebene Projekt und erstellt es anschließend.|
|/deploy|Gibt an, dass das Projekt nach dem Erstellen oder Neuerstellen bereitgestellt werden soll|
|*SolnConfigName*|Erforderlich. Der Name der Projektmappenkonfiguration, die auf die in *SolutionName* benannte Projektmappe angewendet wird. Wenn mehrere Projektmappenplattformen verfügbar sind, müssen Sie auch die Plattform angeben, z.B. **"Debug\|Win32"**.|
|*SolutionName*|Erforderlich. Der vollständige Pfad und Name der Projektmappendatei|
|/project *ProjName*|Dies ist optional. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Sie können einen relativen Pfad vom *SolutionName*-Ordner zur Projektdatei, dem Anzeigenamen des Projekts oder dem vollständigen Pfad und Namen der Projektdatei eingeben.|
|/projectconfig *ProjConfigName*|Dies ist optional. Der Name der Projektbuildkonfiguration für die Anwendung auf das durch das **/project**-Argument angegebene Projekt. Wenn mehrere Projektmappenplattformen verfügbar sind, müssen Sie auch die Plattform angeben, z.B. **"Debug\|Win32"**.|

## <a name="remarks"></a>Hinweise

Der **/projectconfig**-Schalter muss mit dem **/project**-Schalter als Teil eines **/build**-, **/clean**-, **/rebuild**- oder **/deploy**-Befehls verwendet werden.

Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.

Zusammenfassungsinformationen für Builds, inklusive Fehlermeldungen, können im Befehlsfenster oder in einer Protokolldatei, die durch den **/out**-Schalter angegeben wird, angezeigt werden.

## <a name="example"></a>Beispiel

Mit dem folgenden Befehl wird das Projekt „CSharpConsoleApp“ mithilfe der Projektbuildkonfiguration „Debug“ innerhalb der Projektmappenkonfiguration „Debug“ von „MySolution“ erstellt:

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)