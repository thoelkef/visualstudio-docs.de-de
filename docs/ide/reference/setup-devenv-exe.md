---
title: /Setup-Parameter („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3f1f801d4da451d9357082359a1cf001915e1041
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829273"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

Der /Setup-Schalter zwingt Visual Studio dazu, die Ressourcenmetadaten zur Beschreibung von Menüs, Symbolleisten und Befehlsgruppen aus allen verfügbaren VSPackages zusammenzuführen.

## <a name="syntax"></a>Syntax

```shell
devenv /setup
```

## <a name="remarks"></a>Hinweise

Der Schalter verwendet keine Argumente. Der Befehl `devenv /setup` wird in der Regel als letzter Schritt der Installation angegeben. Bei Verwendung des Schalters `/setup` wird Visual Studio nicht gestartet.

> [!NOTE]
> Sie müssen `devenv` als Administrator ausführen, um die Schalter `/setup` verwenden zu können.

## <a name="example"></a>Beispiel

In diesem Beispiel wird der letzte Schritt der Installation einer Version von Visual Studio dargestellt, die VSPackages enthält.

```shell
devenv /setup
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)