---
title: /DebugExe („devenv.exe“) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f472add6b821693d1d48397e878db19e707e2868
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660802"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Öffnet die angegebene ausführbare Datei, die debuggt werden soll.

## <a name="syntax"></a>Syntax

```
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Argumente
 `ExecutableFile` ist erforderlich. Der Pfad und Dateiname einer EXE-Datei.

 Wenn die EXE-Datei nicht gefunden wurde oder nicht vorhanden ist, wird keine Warnung oder Fehlermeldung angezeigt und [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] startet normal.

## <a name="remarks"></a>Bemerkungen
 Alle Zeichenfolgen, die dem `ExecutableFile`-Parameter folgen, werden dieser Datei als Argumente übergeben.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Datei `MyApplication.exe` zum Debuggen geöffnet.

```
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Weitere Informationen
 [Debug-Befehls Zeilenschalter](../../ide/reference/devenv-command-line-switches.md)
