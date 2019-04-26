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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05266a6f1b5ee0be22e2edc8df1c03b720844f4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968079"
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

## <a name="remarks"></a>Anmerkungen

Alle Zeichenfolgen, die dem *ExecutableFile*-Parameter folgen, werden dieser Datei als Argumente übergeben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Datei `MyApplication.exe` zum Debuggen geöffnet.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)