---
title: /Rebuild („devenv.exe“) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 008169829a6cf76e959d00f010959239a5f390b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665647"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bereinigt und erstellt die angegebene Projektmappenkonfiguration

## <a name="syntax"></a>Syntax

```
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumente
 `SolnConfigName` ist erforderlich. Der Name der Projektmappenkonfiguration, die für das Erstellen der Projektmappe verwendet wird, die in `SolutionName` benannt wurde

 `SolutionName` ist erforderlich. Der vollständige Pfad und Name der Projektmappendatei.

 /project: `ProjName` ist optional. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Sie können einen relativen Pfad vom `SolutionName`-Ordner zur Projektdatei, dem Anzeigenamen des Projekts oder dem vollständigen Pfad und Namen der Projektdatei eingeben.

 /projectconfig: `ProjConfigName` ist optional. Der Name der Projektbuildkonfiguration für die Neuerstellung des benannten `/project`.

## <a name="remarks"></a>Bemerkungen

- Dieser Schalter führt dieselbe Funktion aus wie der Menübefehl **Projektmappe neu erstellen** in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE).

- Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelte Anführungszeichen ein.

- Zusammenfassende Informationen für Bereinigungen und Builds, inklusive Fehlermeldungen, können im **Befehlsfenster** oder durch den `/out`-Schalter in einer Protokolldatei angezeigt werden.

## <a name="example"></a>Beispiel
 Dieses Beispiel bereinigt und erstellt das Projekt `CSharpWinApp` mithilfe der Projektbuildkonfiguration `Debug` in der `Debug`-Projektmappenkonfiguration von `MySolution` neu.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Weitere Informationen
 Debug- [Befehls Zeilenschalter](../../ide/reference/devenv-command-line-switches.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
