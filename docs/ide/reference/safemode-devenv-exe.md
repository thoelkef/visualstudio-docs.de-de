---
title: -SafeMode („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6df78ec4be1fc94951634b84a98e80dc1403a41b
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948737"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Startet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus und lädt nur die Standardumgebung und -dienste

## <a name="syntax"></a>Syntax

```cmd
devenv /SafeMode
```

## <a name="remarks"></a>Hinweise
 Dieser Schalter verhindert, dass beim Start von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackages von Drittanbietern geladen werden und stellt dadurch eine stabile Ausführung sicher.

## <a name="description"></a>Beschreibung 
 Das folgende Beispiel zeigt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] im abgesicherter Modus.

## <a name="code"></a>Code

```cmd
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)