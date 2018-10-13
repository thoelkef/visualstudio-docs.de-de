---
title: Aktuellen Prozess festlegen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0baea39c341e8034ff222de32548d0518f115e82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246661"
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
  
## <a name="remarks"></a>Hinweise  
 Sie können beim Debuggen mit mehreren Prozessen verbunden sein, es ist jedoch jeweils nur ein Prozess im Debugger aktiv. Zum Festlegen des aktiven Prozesses können Sie den Befehl `SetCurrentProcess` verwenden.  
  
## <a name="example"></a>Beispiel  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



