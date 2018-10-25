---
title: DevEnv-Schalter „Build“
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdd510e523aaabc468c1f01626593e51d0ad1558
ms.sourcegitcommit: 9571742f4a808c75b1034aa72fc24b54bc50692e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410961"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Erstellt mithilfe einer angegebenen Konfigurationsdatei eine Projektmappe

## <a name="syntax"></a>Syntax

```cmd
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Argumente

|||
|-|-|
|*SolutionName*|Erforderlich. Der vollständige Pfad und Name der Projektmappendatei|
|*SolnConfigName*|Erforderlich. Der Name der Projektmappenkonfiguration, die für das Erstellen der Projektmappe verwendet wird, die in *SolutionName* benannt wurde. Wenn mehrere Projektmappenplattformen verfügbar sind, müssen Sie auch die Plattform angeben, z.B. **"Debug\|Win32"**.|
|/project *ProjName*|Dies ist optional. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Sie können einen relativen Pfad vom *SolutionName*-Ordner zur Projektdatei, dem Anzeigenamen des Projekts oder dem vollständigen Pfad und Namen der Projektdatei eingeben.|
|/projectconfig *ProjConfigName*|Dies ist optional. Der Name der Projektbuildkonfiguration für die Erstellung des benannten Projekts. Wenn mehrere Projektplattformen verfügbar sind, müssen Sie auch die Plattform angeben, z.B. **"Debug\|Win32"**.|

## <a name="remarks"></a>Hinweise

- Der Schalter **/build** führt dieselbe Funktion aus wie der Menübefehl **Projektmappe erstellen** in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE).

- Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.

- Zusammenfassungsinformationen für Builds, inklusive Fehlermeldungen, können im Befehlsfenster oder in einer Protokolldatei, die durch den **/out**-Schalter angegeben wird, angezeigt werden.

- Der Schalter **/build** erstellt nur Projekte, die seit dem letzten Build geändert wurden. Verwenden Sie stattdessen [/rebuild](../../ide/reference/rebuild-devenv-exe.md), um alle Projekte in einer Projektmappe zu erstellen.

- Wenn Sie die Fehlermeldung **Ungültige Projektkonfiguration** erhalten, stellen Sie sicher, dass Sie eine Projektmappenplattform oder eine Projektplattform angegeben haben, z.B. **"Debug\|Win32"**.

## <a name="example"></a>Beispiel

Mit dem folgenden Befehl wird das Projekt „CSharpConsoleApp“ mithilfe der Projektbuildkonfiguration „Debug“ innerhalb der Projektmappenkonfiguration „Debug“ von „MySolution“ erstellt.

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Siehe auch

- [Erstellen und Bereinigen von Projekten und Projektmappen](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)