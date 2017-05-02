---
title: "IDebugStackFrame::GetLanguageString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrame.GetLanguageString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrame::GetLanguageString"
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame::GetLanguageString
Gibt eine kurze oder lange Textbeschreibung der Sprache zurück.  
  
## Syntax  
  
```  
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### Parameter  
 `fLong`  
 \[in\] Gibt Flag, in dem `TRUE` eine lange Beschreibung und `FALSE` zurückgibt, eine kurze Beschreibung zurück.  
  
 `pbstrLanguage`  
 \[out\] Die Beschreibung der Sprache.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Normalerweise werden `fLong``FALSE` ist, gibt diese Methode nur den Namen der Sprache an, die dem Stapelrahmen zugeordnet ist.  Wenn `fLong``TRUE` ist, stellt diese Methode eine vollständige Produktbeschreibung bereit.  
  
## Siehe auch  
 [IDebugStackFrame\-Schnittstelle](../../winscript/reference/idebugstackframe-interface.md)