---
title: -DebugExe („devenv.exe“)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
ms.openlocfilehash: 1badcaba6f6461f6a2c6b73580d8d12c50481c2b
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948776"
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