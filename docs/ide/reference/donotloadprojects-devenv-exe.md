---
title: -DoNotLoadProjects („devenv.exe“)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51e3341082ff354fc8bc87a89b3d7bc56e4e7887
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569854"
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
