---
title: -Build („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba1d23302cc0c3b9d14b23bd8547f33eb21ce0c3
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
Erstellt mithilfe einer angegebenen Konfigurationsdatei eine Projektmappe

## <a name="syntax"></a>Syntax

```cmd
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Argumente
 `SolutionName` ist erforderlich. Der vollständige Pfad und Name der Projektmappendatei

 `SolnConfigName` ist erforderlich. Der Name der Projektmappenkonfiguration, die für das Erstellen der Projektmappe verwendet wird, die in `SolutionName` benannt wurde

 /project: `ProjName` ist optional. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Sie können einen relativen Pfad vom `SolutionName`-Ordner zur Projektdatei, dem Anzeigenamen des Projekts oder dem vollständigen Pfad und Namen der Projektdatei eingeben.

 /projectconfig: `ProjConfigName` ist optional. Der Name der Projektbuildkonfiguration für die Erstellung des benannten `/project`.

## <a name="remarks"></a>Hinweise
 Dieser Schalter führt dieselbe Funktion aus wie der Menübefehl **Projektmappe erstellen** in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE).

 Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelte Anführungszeichen ein.

 Zusammenfassende Informationen für Builds, inklusive Fehlermeldungen, können im Fenster **Befehl** oder in einer Protokolldatei, die durch den Schalter `/out` angegeben wird, angezeigt werden.

 Dieser Befehl erstellt nur Projekte, die seit dem letzten Build geändert wurden. Um alle Projekte in einer Projektmappe zu erstellen, verwenden Sie [/Rebuild („devenv.exe“)](../../ide/reference/rebuild-devenv-exe.md).

## <a name="example"></a>Beispiel
 In diesem Beispiel wird das Projekt `CSharpConsoleApp` mithilfe der `Debug`-Projektbuildkonfiguration in der `Debug`-Projektmappenkonfiguration von `MySolution` erstellt.

```cmd
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Siehe auch

- [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)