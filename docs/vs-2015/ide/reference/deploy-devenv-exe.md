---
title: -Deploy („devenv.exe“) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 620be9ea458d55a8c9610079b357cc9466a03f56
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660772"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stellt eine Projektmappe nach einer Erstellung oder Neuerstellung bereit. Gilt nur für Projekte mit verwaltetem Code.

## <a name="syntax"></a>Syntax

```
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]
```

## <a name="arguments"></a>Argumente
 `SolnConfigName` ist erforderlich. Der Name der Projektmappenkonfiguration, die für das Erstellen der Projektmappe verwendet wird, die in `SolutionName` benannt wurde

 `SolutionName` ist erforderlich. Der vollständige Pfad und Name der Projektmappendatei

 /project: `ProjName` ist optional. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Sie können einen relativen Pfad vom `SolutionName`-Ordner zur Projektdatei, dem Anzeigenamen des Projekts oder dem vollständigen Pfad und Namen der Projektdatei eingeben.

 /projectconfig: `ProjConfigName` ist optional. Der Name der Projektbuildkonfiguration für die Erstellung des benannten `/project`.

## <a name="remarks"></a>Anmerkungen
 Das angegebene Projekt muss ein Bereitstellungsprojekt sein. Wenn das angegebene Projekt kein Bereitstellungsprojekt ist und das erstellte Projekt zur Bereitstellung übergeben wird, schlägt der Vorgang mit einer Fehlermeldung fehl.

 Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.

 Zusammenfassende Informationen für Builds, inklusive Fehlermeldungen, können im Fenster **Befehl** oder in einer Protokolldatei, die durch den Schalter `/out` angegeben wird, angezeigt werden.

## <a name="example"></a>Beispiel
 Dieses Beispiel stellt das Projekt `CSharpConsoleApp` mithilfe der Projektbuildkonfiguration `Release` in der Projektmappenkonfiguration `Release` von `MySolution` bereit.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Siehe auch
 Debug- [Befehls Zeilenschalter](../../ide/reference/devenv-command-line-switches.md) [/Project ("abvenv. exe")](../../ide/reference/project-devenv-exe.md) [/Build ("abvenv. exe")](../../ide/reference/build-devenv-exe.md) [/clean ("abvenv. exe")](../../ide/reference/clean-devenv-exe.md) [/Rebuild ("Debug v. exe")](../../ide/reference/rebuild-devenv-exe.md) [/out (](../../ide/reference/out-devenv-exe.md) "" "" "" "" "" "
