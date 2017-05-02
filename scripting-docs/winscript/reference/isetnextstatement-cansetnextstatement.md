---
title: "ISetNextStatement::CanSetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISetNextStatement.CanSetNextStatement
apilocation: scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# ISetNextStatement::CanSetNextStatement
Diese Methode bestimmt, ob sich der Ausführungspunkt, der die folgende Anweisung des auszuführenden Code bestimmt, festgelegt werden kann der angegebenen Position.  
  
## Syntax  
  
```  
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### Parameter  
 `pStackFrame`  
 \[in\] Zeiger auf einen Stapelrahmenobjekt.  
  
 `pCodeContext`  
 \[in\] Zeiger auf einen Codekontextobjekt.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die folgende Anweisung kann zum angegebenen Codekontext aktualisiert werden.|  
|`S_FALSE`|Die folgende Anweisung kann nicht auf den angegebenen Codekontext aktualisiert werden.|  
  
## Hinweise  
  
## Siehe auch  
 [ISetNextStatement\-Schnittstelle](../../winscript/reference/isetnextstatement-interface.md)