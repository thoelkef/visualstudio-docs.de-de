---
title: -DebugExe („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99f256b47125f4e07ca5dc148c4351871389a94b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889409"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Öffnet die angegebene ausführbare Datei, die debuggt werden soll.

## <a name="syntax"></a>Syntax

```cmd
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Argumente
 `ExecutableFile`

 Erforderlich. Der Pfad und Dateiname einer EXE-Datei.

 Wenn die EXE-Datei nicht gefunden wurde oder nicht vorhanden ist, wird keine Warnung oder Fehlermeldung angezeigt und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] startet normal.

## <a name="remarks"></a>Hinweise
 Alle Zeichenfolgen, die dem `ExecutableFile`-Parameter folgen, werden dieser Datei als Argumente übergeben.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Datei `MyApplication.exe` zum Debuggen geöffnet.

```cmd
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)