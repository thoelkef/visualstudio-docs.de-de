---
title: Befehl „Haltepunkt ein/aus“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c7dd3bd7a4d42b8135aed034464223af53091f87
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509374"
---
# <a name="toggle-breakpoint-command"></a>Befehl "Haltepunkt ein/aus"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Befehl "Haltepunkt umschalten"](https://docs.microsoft.com/visualstudio/ide/reference/toggle-breakpoint-command).  
  
  
Schaltet den Haltepunkt entweder ein oder aus, je nach seinem aktuellen Status an der aktuellen Position in der Datei.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## <a name="arguments"></a>Argumente  
 `text`  
 Dies ist optional. Wenn Text angegeben ist, wird die Zeile als benannter Haltepunkt markiert. Andernfalls wird die Zeile als unbenannter Haltepunkt markiert. Ähnliches geschieht, wenn Sie F9 drücken.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der aktuelle Haltepunkt umgeschaltet.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)



