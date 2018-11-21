---
title: -Rebuild („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0946137cb259386648b7b3ac2883c33f5724352
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948608"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
Bereinigt und erstellt die angegebene Projektmappenkonfiguration

## <a name="syntax"></a>Syntax

```cmd
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumente
 `SolnConfigName`

 Erforderlich. Der Name der Projektmappenkonfiguration, die für das Erstellen der Projektmappe verwendet wird, die in `SolutionName` benannt wurde

 `SolutionName`

 Erforderlich. Der vollständige Pfad und Name der Projektmappendatei

 /project `ProjName`

 Dies ist optional. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Sie können einen relativen Pfad vom `SolutionName`-Ordner zur Projektdatei, dem Anzeigenamen des Projekts oder dem vollständigen Pfad und Namen der Projektdatei eingeben.

 /projectconfig `ProjConfigName`

 Dies ist optional. Der Name der Projektbuildkonfiguration für die Neuerstellung des benannten `/project`.

## <a name="remarks"></a>Hinweise

-   Dieser Schalter führt dieselbe Funktion aus wie der Menübefehl **Projektmappe neu erstellen** in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE).

-   Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.

-   Zusammenfassende Informationen für Bereinigungen und Builds, inklusive Fehlermeldungen, können im **Befehlsfenster** oder durch den `/out`-Schalter in einer Protokolldatei angezeigt werden.

## <a name="example"></a>Beispiel
 Dieses Beispiel bereinigt und erstellt das Projekt `CSharpWinApp` mithilfe der Projektbuildkonfiguration `Debug` in der `Debug`-Projektmappenkonfiguration von `MySolution` neu.

```cmd
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)