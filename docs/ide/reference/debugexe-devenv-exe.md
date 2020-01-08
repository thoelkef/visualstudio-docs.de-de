---
title: -DebugExe („devenv.exe“)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aeae28288936b6723b53e826142a4888ad0bc8b4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75570140"
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
