---
title: -Project („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- project Devenv switch (/project)
- Devenv, /project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c73167c5529eda0f97f414e7c0e2d76083b7bb0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921613"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
Identifiziert ein einzelnes Projekt innerhalb der angegebenen Projektmappenkonfiguration, das erstellt, bereinigt, neu erstellt oder bereitgestellt werden soll

## <a name="syntax"></a>Syntax

```cmd
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumente
 /build

 Erstellt das durch `/project` `ProjName` angegebene Projekt

 /clean

 Bereinigt alle Zwischendateien und Ausgabeverzeichnisse, die während eines Builds erstellt werden

 /rebuild

 Bereinigt und erstellt das durch `/project` `ProjName` angegebene Projekt

 /deploy

 Gibt an, dass das Projekt nach dem Erstellen oder Neuerstellen bereitgestellt werden soll

 `SolnConfigName`

 Erforderlich. Der Name der Projektmappenkonfiguration, die auf die in `SolutionName` benannte Projektmappe angewendet wird

 `SolutionName`

 Erforderlich. Der vollständige Pfad und Name der Projektmappendatei

 /project `ProjName`

 Dies ist optional. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Sie können einen relativen Pfad vom `SolutionName`-Ordner zur Projektdatei, dem Anzeigenamen des Projekts oder dem vollständigen Pfad und Namen der Projektdatei eingeben.

 /projectconfig `ProjConfigName`

 Dies ist optional. Der Name der Projektbuildkonfiguration für die Anwendung auf das benannte `/project`

## <a name="remarks"></a>Hinweise

-   Muss als Teil der Befehle `devenv /build`, /`clean`, `/rebuild` oder `/deploy` verwendet werden

-   Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.

-   Zusammenfassende Informationen für Builds, inklusive Fehlermeldungen, können im Fenster **Befehl** oder in einer Protokolldatei, die durch den Schalter `/out` angegeben wird, angezeigt werden.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird das Projekt `CSharpConsoleApp` mithilfe der `Debug`-Projektbuildkonfiguration in der `Debug`-Projektmappenkonfiguration von `MySolution` erstellt.

```cmd
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)