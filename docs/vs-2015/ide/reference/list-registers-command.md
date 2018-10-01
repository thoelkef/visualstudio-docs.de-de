---
title: Befehl „Register auflisten“ | Microsoft-Dokumentation
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
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c9ff1287bb4c92d074c0a0e123d48ddb7e61cc90
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515321"
---
# <a name="list-registers-command"></a>Befehl "Registrierungen auflisten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [auflisten (Befehl) registriert](https://docs.microsoft.com/visualstudio/ide/reference/list-registers-command).  
  
  
Zeigt den Wert des ausgewählten Registers an und ermöglicht es Ihnen, die Liste der anzuzeigenden Register zu ändern  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## <a name="switches"></a>Schalter  
 /Display [{`register`|`registerGroup`}...]  
 Zeigt die Werte des angegebenen `register` oder `registerGroup` an. Wenn weder `register` noch `registerGroup` angegeben ist, wird die Standardregisterliste angezeigt. Wenn kein Schalter angegeben ist, ist das Verhalten identisch. Zum Beispiel:  
  
 `Debug.ListRegisters /Display eax`  
  
 für die folgende Syntax:  
  
 `Debug.ListRegisters eax`  
  
 /List  
 Zeigt alle Registergruppen in der Liste an  
  
 /Watch [{`register`|`registerGroup`}...]  
 Fügt der Liste einen oder mehrere `register`- oder `registerGroup`-Werte hinzu  
  
 /Unwatch [{`register`|`registerGroup`}...]  
 Entfernt einen oder mehrere `register`- oder `registerGroup`-Werte aus der Liste  
  
## <a name="remarks"></a>Hinweise  
 Der Alias `r` kann anstelle von `Debug.ListRegisters` verwendet werden.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird das `Debug.ListRegisters`-Alias `r` verwendet, um die Werte der Registergruppe `Flags` anzuzeigen.  
  
```  
r /Display Flags  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Grundlagen des Debuggens: Fenster „Register“](../../debugger/debugging-basics-registers-window.md)   
 [Gewusst wie: Verwenden des Fensters "Register"](../../debugger/how-to-use-the-registers-window.md)



