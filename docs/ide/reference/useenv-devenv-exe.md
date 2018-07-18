---
title: -UseEnv („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e6d04064b9912fbd0592fcaeffd179016ef38c1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944540"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Startet Visual Studio und lädt die Umgebungsvariablen in das Dialogfeld **VC++-Verzeichnisse**.

> [!NOTE]
> Dieser Schalter wird mit der Workload **Desktopentwicklung mit C++** installiert.

## <a name="syntax"></a>Syntax

```shell
Devenv /useenv
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird Visual Studio gestartet, und die Umgebungsvariablen werden in das Dialogfeld **VC++-Verzeichnisse** geladen.

```shell
Devenv.exe /useenv
```

## <a name="see-also"></a>Siehe auch

* [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)