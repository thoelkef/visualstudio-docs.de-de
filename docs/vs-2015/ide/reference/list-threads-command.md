---
title: Befehl „Threads auflisten“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 627e361fca63522f47a1d472655573c14a44035a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804607"
---
# <a name="list-threads-command"></a>Befehl "Threads auflisten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Zeigt eine Liste der Threads im aktuellen Programm an.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>Argumente  
 `index`  
 Dies ist optional. Wählt einen Thread nach seinem Index als aktuellen Thread aus  
  
## <a name="remarks"></a>Hinweise  
 Wenn angegeben, kennzeichnet das `index`-Argument den angegebenen Thread als aktuellen Thread. Ein Sternchen (*) wird in der Liste neben dem aktuellen Thread angezeigt.  
  
## <a name="example"></a>Beispiel  
  
```  
>Debug.ListThreads   
```  
  
## <a name="see-also"></a>Siehe auch  
 [Befehl „Aufrufliste auflisten“](../../ide/reference/list-call-stack-command.md)   
 [Befehl „Disassemblierung auflisten“](../../ide/reference/list-disassembly-command.md)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
