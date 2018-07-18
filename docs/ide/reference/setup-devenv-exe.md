---
title: /Setup-Parameter („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0f3d78ebb63434df38735bdf24e9d4fcba8f172c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942944"
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