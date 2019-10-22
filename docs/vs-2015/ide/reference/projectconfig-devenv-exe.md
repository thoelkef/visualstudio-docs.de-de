---
title: /ProjectConfig („devenv.exe“) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a33c7cbaef473e75631bb4ac6c0d217198cbf250
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662085"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt eine Projektbuildkonfiguration an, die beim Erstellen, Bereinigen, Neuerstellen oder Bereitstellen des im `/project`-Argument benannten Projekts angewendet werden soll.

## <a name="syntax"></a>Syntax

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumente
 /Build erstellt das Projekt, das von `/project` `ProjName` angegeben wird.

 /Clean bereinigt alle zwischen Dateien und Ausgabe Verzeichnisse, die während eines Builds erstellt wurden.

 /Rebuild bereinigt erstellt dann das Projekt, das von `/project` `ProjName` angegeben wird.

 /Deploy gibt an, dass das Projekt nach einem Build oder einer Neuerstellung bereitgestellt wird.

 `SolnConfigName` ist erforderlich. Der Name der Projektmappenkonfiguration, die auf die in `SolutionName` benannte Projektmappe angewendet wird

 `SolutionName` ist erforderlich. Der vollständige Pfad und Name der Projektmappendatei

 /project: `ProjName` ist optional. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Sie können einen relativen Pfad vom `SolutionName`-Ordner zur Projektdatei, dem Anzeigenamen des Projekts oder dem vollständigen Pfad und Namen der Projektdatei eingeben.

 /projectconfig: `ProjConfigName` ist optional. Der Name der Projektbuildkonfiguration für die Anwendung auf das benannte `/project`

## <a name="remarks"></a>Anmerkungen

- Muss zusammen mit dem `/project`-Schalter als Teil eines `devenv /build`-, /`clean`-, `/rebuild`- oder `/deploy`-Befehls verwendet werden.

- Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.

- Zusammenfassende Informationen für Builds, inklusive Fehlermeldungen, können im Fenster **Befehl** oder in einer Protokolldatei, die durch den Schalter `/out` angegeben wird, angezeigt werden.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird das Projekt `CSharpConsoleApp` mithilfe der `Debug`-Projektbuildkonfiguration in der `Debug`-Projektmappenkonfiguration von `MySolution` erstellt.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Siehe auch
 Debug- [Befehls Zeilenschalter](../../ide/reference/devenv-command-line-switches.md) [/Project ("abvenv. exe")](../../ide/reference/project-devenv-exe.md) [/Build ("abvenv. exe")](../../ide/reference/build-devenv-exe.md) [/clean ("Debug". exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild ("Debug v. exe")](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (](../../ide/reference/deploy-devenv-exe.md) "Debug v. exe") [/out ("Debug v. exe")](../../ide/reference/out-devenv-exe.md)
