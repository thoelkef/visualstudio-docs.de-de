---
title: -SafeMode („devenv.exe“)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b794c80768990a3abac85d3ea3b93699f3b220dd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970434"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Startet Visual Studio im abgesicherten Modus und lädt nur die Standardumgebung und -dienste.

## <a name="syntax"></a>Syntax

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Hinweise

Dieser Schalter verhindert, dass beim Start von Visual Studio VSPackages von Drittanbietern geladen werden und ermöglicht so eine stabile Ausführung.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird Visual Studio im abgesicherten Modus gestartet.

```shell
devenv /safemode
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)