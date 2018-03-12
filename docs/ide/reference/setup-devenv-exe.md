---
title: "Setup-Schalter „devenv.exe“ | Microsoft-Dokumentation"
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e37fe50eefc36e7b5396f396d2b614851a0bd9cb
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
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

[Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)