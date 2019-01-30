---
title: -DebugExe („devenv.exe“)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a93a582af62ed0eac8cdc0f5da55ac7bda555152
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008971"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Öffnet die angegebene ausführbare Datei, die debuggt werden soll.

## <a name="syntax"></a>Syntax

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Argumente

- *ExecutableFile*

  Erforderlich. Der Pfad und Dateiname einer `.exe`-Datei. Wenn die `.exe`-Datei nicht gefunden wurde oder nicht vorhanden ist, wird keine Warnung oder Fehlermeldung angezeigt und Visual Studio startet normal.

## <a name="remarks"></a>Hinweise

Alle Zeichenfolgen, die dem *ExecutableFile*-Parameter folgen, werden dieser Datei als Argumente übergeben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Datei `MyApplication.exe` zum Debuggen geöffnet.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)