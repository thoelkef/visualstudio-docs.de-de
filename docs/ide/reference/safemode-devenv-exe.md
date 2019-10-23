---
title: -SafeMode („devenv.exe“)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abaeded184db78085a9629da0e763b2f76dbd328
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655516"
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