---
title: "SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND-Enumeration
Gibt die Art der ausgelösten Ausnahme an.  Diese Enumeration wird von der [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)\-Methode verwendet.  
  
> [!IMPORTANT]
>  Diese Konstanten werden durch PDM\-Version 11.0 und höher implementiert.  Gefunden in activdbg100.h.  
  
## Syntax  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## Member  
  
|Member|Wert|Beschreibung|  
|------------|----------|------------------|  
|ETK\_FIRST\_CHANCE|0x00000000|Die Ausnahme ist eine Ausnahme der ersten Chance.|  
|ETK\_USER\_UNHANDLED|0x00000001|Die Ausnahme wird im Benutzercode nicht behandelt.|  
|ETK\_UNHANDLED|0x00000002|Die Ausnahme wird im Code nicht behandelt.|  
  
## Siehe auch  
 [IActiveScriptErrorDebug110\-Schnittstelle](../../winscript/reference/iactivescripterrordebug110-interface.md)