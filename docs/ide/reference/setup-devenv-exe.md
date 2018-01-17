---
title: "Setup-Schalter „devenv.exe“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93f03de74540d130d66ce123b355691e0828b93e
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2018
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

Der /Setup-Schalter zwingt Visual Studio dazu, die Ressourcenmetadaten zur Beschreibung von Menüs, Symbolleisten und Befehlsgruppen aus allen verfügbaren VSPackages zusammenzuführen.

## <a name="syntax"></a>Syntax

```
devenv /setup
```

## <a name="remarks"></a>Hinweise

Der Schalter verwendet keine Argumente. Der Befehl `devenv /setup` wird in der Regel als letzter Schritt der Installation angegeben. Bei Verwendung des Schalters `/setup` wird Visual Studio nicht gestartet.

Sie müssen `devenv` als Administrator ausführen, um die Schalter [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) und [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) verwenden zu können.

## <a name="example"></a>Beispiel

In diesem Beispiel wird der letzte Schritt der Installation einer Version von Visual Studio dargestellt, die VSPackages enthält.

```
devenv /setup
```

## <a name="see-also"></a>Siehe auch

[Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)