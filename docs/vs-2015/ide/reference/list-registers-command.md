---
title: Befehl „Register auflisten“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 6f9eaa1299ec49cf20713723e822f8fc641401d8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199137"
---
# <a name="list-registers-command"></a>Befehl "Registrierungen auflisten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zeigt den Wert des ausgewählten Registers an und ermöglicht es Ihnen, die Liste der anzuzeigenden Register zu ändern  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## <a name="switches"></a>Schalter  
 /Display [{`register`|`registerGroup`}...]  
 Zeigt die Werte des angegebenen `register` oder `registerGroup` an. Wenn weder `register` noch `registerGroup` angegeben ist, wird die Standardregisterliste angezeigt. Wenn kein Schalter angegeben ist, ist das Verhalten identisch. Beispiel:  
  
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
 [Debuggrundlagen: Fenster "Register"](../../debugger/debugging-basics-registers-window.md)   
 [Vorgehensweise: Verwenden des Fensters „Register“](../../debugger/how-to-use-the-registers-window.md)
