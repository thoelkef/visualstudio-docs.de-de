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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1edbcddd27f2c3637e0e56dd9b4841e17ace16af
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767562"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Öffnet die angegebene ausführbare Datei, die debuggt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>Argumente  
 `ExecutableFile`  
 Erforderlich. Der Pfad und Dateiname einer EXE-Datei.  
  
 Wenn die EXE-Datei nicht gefunden wurde oder nicht vorhanden ist, wird keine Warnung oder Fehlermeldung angezeigt und [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] startet normal.  
  
## <a name="remarks"></a>Hinweise  
 Alle Zeichenfolgen, die dem `ExecutableFile`-Parameter folgen, werden dieser Datei als Argumente übergeben.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Datei `MyApplication.exe` zum Debuggen geöffnet.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
