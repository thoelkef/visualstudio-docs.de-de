---
title: "Befehl „Gehe zu“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 53c45ccf528375bc31b4d61fd6af0193aa295e6c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="go-to-command"></a>Befehl "Gehe zu"
Bewegt den Cursor in die angegebene Zeile.  
  
## <a name="syntax"></a>Syntax  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Argumente  
 `linenumber`  
 Dies ist optional. Eine ganze Zahl, die die Zeilennummer, zu der Sie springen wollen, angibt.  
  
## <a name="remarks"></a>Hinweise  
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
 [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)