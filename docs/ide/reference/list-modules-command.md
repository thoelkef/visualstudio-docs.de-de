---
title: "Befehl &quot;Module auflisten&quot; | Microsoft Docs"
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
  - "debug.listmodules"
helpviewer_keywords: 
  - "Debug.ListModules-Befehl"
  - "Module auflisten (Befehl)"
  - "ListModules-Befehl"
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Befehl &quot;Module auflisten&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Listet die Module für den aktuellen Prozess auf.  
  
## Syntax  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### Parameter  
 \/Address:`yes|no`  
 Optional.  Gibt an, ob die Speicheradressen der Module angezeigt werden sollen.  Der Standardwert lautet `yes`.  
  
 \/Name:`yes|no`  
 Optional.  Gibt an, ob die Namen der Module angezeigt werden sollen.  Der Standardwert lautet `yes`.  
  
 \/Order:`yes|no`  
 Optional.  Gibt an, ob die Reihenfolge der Module angezeigt werden soll.  Der Standardwert lautet `no`.  
  
 \/Path:`yes|no`  
 Optional.  Gibt an, ob die Pfade der Module angezeigt werden sollen.  Der Standardwert lautet `yes`.  
  
 \/Process:`yes|no`  
 Optional.  Gibt an, ob die Prozesse der Module angezeigt werden sollen.  Der Standardwert lautet `no`.  
  
 \/SymbolFile:`yes|no`  
 Optional.  Gibt an, ob die Symboldateien der Module angezeigt werden sollen.  Der Standardwert lautet `no`.  
  
 \/SymbolStatus:`yes|no`  
 Optional.  Gibt an, ob Symbolstatusinformationen zu den Modulen angezeigt werden sollen.  Der Standardwert lautet `yes`.  
  
 \/Timestamp:`yes|no`  
 Optional.  Gibt an, ob die Timestamps der Module angezeigt werden sollen.  Der Standardwert lautet `no`.  
  
 \/Version:`yes|no`  
 Optional.  Gibt an, ob die Versionen der Module angezeigt werden sollen.  Der Standardwert lautet `no`.  
  
## Hinweise  
  
## Beispiel  
 In diesem Beispiel werden die Modulnamen, Adressen und Timestamps für den aktuellen Prozess aufgelistet.  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Gewusst wie: Verwenden des Fensters Module](../../debugger/how-to-use-the-modules-window.md)