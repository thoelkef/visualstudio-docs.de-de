---
title: /Clean („devenv.exe“) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- clean Devenv switch
- /clean Devenv switch
- Devenv, /clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 043e9373f242523b7925a9ae775be6789f7cfc20
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660886"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bereinigt alle Zwischendateien und Ausgabeverzeichnisse

## <a name="syntax"></a>Syntax

```
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]
```

## <a name="arguments"></a>Argumente
 `FileName` ist erforderlich. Der vollständige Pfad und Name der Projektmappen- oder Projektdatei.

 /project: `ProjName` ist optional. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Sie können einen relativen Pfad vom `SolutionName`-Ordner zur Projektdatei, dem Anzeigenamen des Projekts oder dem vollständigen Pfad und Namen der Projektdatei eingeben.

 /projectconfig: `ProjConfigName` ist optional. Der Name der Projektbuildkonfiguration für die Bereinigung des benannten `/project`.

## <a name="remarks"></a>Anmerkungen
 Dieser Schalter führt dieselbe Funktion aus wie der Menübefehl **Projektmappe bereinigen** in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE).

 Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.

 Zusammenfassende Informationen für Bereinigungen und Builds, inklusive Fehlermeldungen, können im **Befehlsfenster** oder durch den `/out`-Schalter in einer Protokolldatei angezeigt werden.

## <a name="example"></a>Beispiel
 Im ersten Beispiel wird die `MySolution`-Projektmappe mithilfe der in der Projektmappendatei angegebenen Standardkonfiguration bereinigt.

 In diesem Beispiel wird das Projekt `CSharpConsoleApp` mithilfe der Projektbuildkonfiguration `Debug` in der `Debug`-Projektmappenkonfiguration von `MySolution` bereinigt.

```
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean

devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Siehe auch
 Debug- [Befehls Zeilenschalter](../../ide/reference/devenv-command-line-switches.md) [/Build ("")](../../ide/reference/build-devenv-exe.md) ("Debug") [/Rebuild (](../../ide/reference/rebuild-devenv-exe.md) "Debug". exe) [/out (](../../ide/reference/out-devenv-exe.md) "" "" "" "" "" "" "
