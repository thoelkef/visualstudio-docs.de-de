---
title: -SafeMode („devenv.exe“)
ms.date: 12/10/2018
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
ms.openlocfilehash: 14b2ac3a80a9e17e0c554f56ae8e31ac32450c5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945478"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Startet Visual Studio im abgesicherten Modus und lädt nur die Standardumgebung und -dienste.

## <a name="syntax"></a>Syntax

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Anmerkungen

Dieser Schalter verhindert, dass beim Start von Visual Studio VSPackages von Drittanbietern geladen werden und ermöglicht so eine stabile Ausführung.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird Visual Studio im abgesicherten Modus gestartet.

```shell
devenv /safemode
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)