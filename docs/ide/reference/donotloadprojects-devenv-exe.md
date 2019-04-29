---
title: -DoNotLoadProjects („devenv.exe“)
ms.date: 03/11/2019
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
ms.openlocfilehash: de757e7022339b11f6d7c04ea7315abf685da24c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428046"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

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
