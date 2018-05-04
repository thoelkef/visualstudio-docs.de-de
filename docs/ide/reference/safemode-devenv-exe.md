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
ms.openlocfilehash: eaf137b699b7a02a0ee79099e937767262fce4e9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Startet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus und lädt nur die Standardumgebung und -dienste

## <a name="syntax"></a>Syntax

```
devenv /SafeMode
```

## <a name="remarks"></a>Hinweise
 Dieser Schalter verhindert, dass beim Start von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackages von Drittanbietern geladen werden und stellt dadurch eine stabile Ausführung sicher.

## <a name="description"></a>description
 Das folgende Beispiel zeigt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] im abgesicherter Modus.

## <a name="code"></a>Code

```
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)