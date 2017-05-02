---
title: "DEBUG_TEXT-Konstanten | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# DEBUG_TEXT-Konstanten
Verwendet während [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## Syntax  
  
```  
typedef DWORD DEBUG_TEXT;  
  
```  
  
## Konstanten  
  
|Konstante|Wert|Beschreibung|  
|---------------|----------|------------------|  
|DWORD DEBUG\_TEXT\_ISEXPRESSION|0x00000001|Gibt an, dass der Text ein Ausdruck ist und keine Anweisung.  Dieses Flag kann sich darauf auswirken, wie der Text von einigen Sprachen analysiert wird.|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|Wenn ein Rückgabewert verfügbar ist, wird er vom Aufrufer verwendet.|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|Lässt keine Nebeneffekte zu.  Wenn dieses Flag festgelegt ist, sollte die Auswertung des Ausdrucks keinen Laufzeitzustand ändern.|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|Erlaubt Haltepunkte während der Auswertung des Texts.  Wenn dieses Flag nicht festgelegt ist, werden Haltepunkte während der Auswertung des Texts ignoriert.|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|Erlaubt Fehlerberichte während der Auswertung des Texts.  Wenn dieses Flag nicht festgelegt ist, werden Fehler nicht während der Auswertung an den Host gemeldet.|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|Gibt an, dass der Ausdruck in einen Codekontext ausgewertet werden soll statt den Ausdruck auszuführen.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script\-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)