---
title: "Befehl „Register auflisten“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 016de257d1ce4e6d2aa95284adbe762a5c54eacf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="list-registers-command"></a>Befehl "Registrierungen auflisten"
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