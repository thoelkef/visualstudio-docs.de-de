---
title: Befehl „Start“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c334f52ba080329ef5cbd6dfde1e3e3beed1dc70
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62551272"
---
# <a name="start-command"></a>Befehl "Start"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Startet das Debuggen des Startup-Projekts.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.Start [address]  
```  
  
## <a name="arguments"></a>Argumente  
 `address`  
 Dies ist optional. Die Adresse, an der das Programm die Ausführung anhält, ähnlich wie ein Breakpoint im Quellcode. Dieses Argument ist nur im Debugmodus gültig.  
  
## <a name="remarks"></a>Anmerkungen  
 Der Befehl **Start** führt bei der Ausführung einen RunToCursor-Vorgang auf die angegebene Adresse aus.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird der Debugger gestartet und ignoriert alle auftretenden Ausnahmen.  
  
```  
>Debug.Start  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
