---
title: -DoNotLoadProjects („devenv.exe“)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a414fde4dee401016e997fa5d6890da2ae8d9d53
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65083934"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Neu für Visual Studio 2019, Version 16.1**

Öffnet die angegebene Lösung, ohne Projekte zu laden. Weitere Informationen finden Sie unter [Gefilterte Projektmappen in Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Syntax

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Argumente

*SolutionName*

Erforderlich. Der vollständige Pfad und Name der Projektmappe, die geöffnet werden soll.

## <a name="example"></a>Beispiel

Im Beispiel wird die Projektmappe „MySln.sln“ geöffnet, ohne dass Projekte geladen werden.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Siehe auch

- [Gefilterte Projektmappen in Visual Studio](../filtered-solutions.md)
- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
