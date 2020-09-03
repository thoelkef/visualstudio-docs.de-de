---
title: -Setup (devenv.exe) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a923d1f3532548ebc6ed651a0739e0e5792f7967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663537"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zwingt [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dazu, die Ressourcenmetadaten zur Beschreibung von Menüs, Symbolleisten und Befehlsgruppen aus allen verfügbaren VSPackages zusammenzuführen.

## <a name="syntax"></a>Syntax

```
devenv /setup
```

## <a name="remarks"></a>Bemerkungen
 Der Schalter verwendet keine Argumente. Der Befehl `devenv /setup` wird in der Regel als letzter Schritt der Installation angegeben. Bei Verwendung des Schalters `/setup` wird [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]nicht gestartet.

 Sie müssen `devenv` als Administrator ausführen, um die Schalter [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) und [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) verwenden zu können.

## <a name="example"></a>Beispiel
 Dieses Beispiel zeigt den letzten Schritt der Installation einer Version von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , die VSPackages enthält.

```
devenv /setup
```

## <a name="see-also"></a>Weitere Informationen
 [Debug-Befehls Zeilenschalter](../../ide/reference/devenv-command-line-switches.md)
