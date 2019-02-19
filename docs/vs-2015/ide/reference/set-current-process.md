---
title: Aktuellen Prozess festlegen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: be451ee1a0b4361e44c8be96713872ca0ee3bd76
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54768847"
---
# <a name="set-current-process"></a>Aktuellen Prozess festlegen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Legt den angegebenen Prozess als aktiven Prozess im Debugger fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>Argumente  
 `index`  
 Erforderlich. Der Index des Prozesses.  
  
## <a name="remarks"></a>Anmerkungen  
 Sie können beim Debuggen mit mehreren Prozessen verbunden sein, es ist jedoch jeweils nur ein Prozess im Debugger aktiv. Zum Festlegen des aktiven Prozesses können Sie den Befehl `SetCurrentProcess` verwenden.  
  
## <a name="example"></a>Beispiel  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
