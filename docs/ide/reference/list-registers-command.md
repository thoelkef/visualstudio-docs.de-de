---
title: "Befehl &quot;Registrierungen auflisten&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listregisters"
helpviewer_keywords: 
  - "Debug.ListRegisters-Befehl"
  - "Registrierungen auflisten (Befehl)"
  - "ListRegisters-Befehl"
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Befehl &quot;Registrierungen auflisten&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Zeigt den Wert der ausgewählten Registrierungen an und bietet die Möglichkeit, die Liste der anzuzeigenden Registrierungen zu ändern.  
  
## Syntax  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## Schalter  
 \/Display \[{`register`&#124;`registerGroup`}...\]  
 Zeigt die Werte von `register` oder `registerGroup` an.  Wenn `register` oder `registerGroup` nicht angegeben ist, wird die Standardliste mit Registrierungen angezeigt.  Wenn kein Schalter angegeben wird, ist das Verhalten identisch.  Beispiele:  
  
 `Debug.ListRegisters /Display eax`  
  
 der folgenden Syntax:  
  
 `Debug.ListRegisters eax`  
  
 \/List  
 Zeigt alle Registrierungsgruppen in der Liste an.  
  
 \/Watch \[{`register`&#124;`registerGroup`}...\]  
 Fügt der Liste einen oder mehrere `register`\-Werte oder `registerGroup`\-Werte hinzu.  
  
 \/Unwatch \[{`register`&#124;`registerGroup`}...\]  
 Entfernt einen oder mehrere `register`\-Werte oder `registerGroup`\-Werte aus der Liste.  
  
## Hinweise  
 Der Alias `r` kann anstelle von `Debug.ListRegisters` verwendet werden.  
  
## Beispiel  
 In diesem Beispiel wird der `Debug.ListRegisters`\-Alias `r` verwendet, um die Werte der Registrierungsgruppe `Flags` anzuzeigen.  
  
```  
r /Display Flags  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Grundlagen des Debuggens: Fenster "Register"](../../debugger/debugging-basics-registers-window.md)   
 [Gewusst wie: Verwenden des Fensters "Register"](../../debugger/how-to-use-the-registers-window.md)