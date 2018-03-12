---
title: "Befehl „Start“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8eb0efae140613c6caa7bd71d72e0ce4cda37db8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="start-command"></a>Befehl "Start"
Startet das Debuggen des Startup-Projekts.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.Start [address]  
```  
  
## <a name="arguments"></a>Argumente  
 `address`  
 Dies ist optional. Die Adresse, an der das Programm die Ausführung anhält, ähnlich wie ein Breakpoint im Quellcode. Dieses Argument ist nur im Debugmodus gültig.  
  
## <a name="remarks"></a>Hinweise  
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
 [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)