---
title: "IDebugStackFrame::GetDescriptionString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetDescriptionString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetDescriptionString"
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetDescriptionString
Gibt eine kurze oder lange Textbeschreibung des Stapelrahmens zurück.  
  
## Syntax  
  
```  
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### Parameter  
 `fLong`  
 \[in\] Gibt Flag, in dem `TRUE` eine lange Beschreibung und `FALSE` zurückgibt, eine kurze Beschreibung zurück.  
  
 `pbstrDescription`  
 \[out\] Die Beschreibung des Stapelrahmens.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Normalerweise werden `fLong``FALSE` ist, gibt diese Methode nur den Namen der Funktion an, die dem Stapelrahmen zugeordnet ist.  Wenn `fLong``TRUE` ist, stellt diese Methode auch die Funktionsparameter und andere relevante Informationen.  
  
## Siehe auch  
 [IDebugStackFrame\-Schnittstelle](../../winscript/reference/idebugstackframe-interface.md)