---
title: Befehl „Gehe zu“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 010d2c395d77be590b3d8d3bc26fc83aaa63adfa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199265"
---
# <a name="go-to-command"></a>Befehl "Gehe zu"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bewegt den Cursor in die angegebene Zeile.  
  
## <a name="syntax"></a>Syntax  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Argumente  
 `linenumber`  
 Optional. Eine ganze Zahl, die die Zeilennummer, zu der Sie springen wollen, angibt.  
  
## <a name="remarks"></a>Anmerkungen  
 Die Zeilennummerierung beginnt bei eins. Wenn der Wert von `linenumber` kleiner als eins ist, wird die erste Zeile angezeigt. Wenn der Wert von `linenumber` größer als die Nummer der letzten Zeile ist, wird die letzte Zeile angezeigt.  
  
 Wenn für `linenumber` kein Wert angegeben wird, wird das **Gehe zu Zeile**-Dialogfeld angezeigt.  
  
 Der Alias dieses Befehls lautet „GoToLn“.  
  
## <a name="example"></a>Beispiel  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
