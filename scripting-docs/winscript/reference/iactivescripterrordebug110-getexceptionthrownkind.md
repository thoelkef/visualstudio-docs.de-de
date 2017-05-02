---
title: "IActiveScriptErrorDebug110::GetExceptionThrownKind | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug110::QueryIsFirstChance"
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptErrorDebug110::GetExceptionThrownKind
Gibt einen Wert zurück, der die Art der ausgelösten Ausnahme angibt.  
  
> [!IMPORTANT]
>  [IActiveScriptErrorDebug110\-Schnittstelle](../../winscript/reference/iactivescripterrordebug110-interface.md) wird von PDM\-Version 11.0 und höher implementiert.  Gefunden in activdbg100.h.  
  
## Syntax  
  
```  
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### Parameter  
 `pExceptionKind`  
 \[out\] Der Typ der der Ausnahme, die ausgelöst wird \(beispielsweise "erste Chance" oder "unbehandelt"\) bei, dargestellt durch einen [SCRIPT\_ERROR\_DEBUG\_EXCEPTION\_THROWN\_KIND\-Enumeration](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md)\-Enumerationswert.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Mögliches Werte \(aber nicht die Einzigen\) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|----------|------------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Siehe auch  
 [IActiveScriptErrorDebug110\-Schnittstelle](../../winscript/reference/iactivescripterrordebug110-interface.md)