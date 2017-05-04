---
title: "IRemoteDebugApplication110::SetDebuggerOptions | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110::SetDebuggerOptions"
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplication110::SetDebuggerOptions
Wird aufgerufen, um Debuggeroptionen zu aktualisieren.  Diese Methode sollte auf [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md) aufgerufen werden.  Die Methode setzt [IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) automatisch zu den Standardoptionen.  Der Optionsstandard auf 0 \(SDO\_NONE\).  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication\-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md) wird durch PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Syntax  
  
```cpp  
HRESULT SetDebuggerOptions(  
        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,  
        [in] enum SCRIPT_DEBUGGER_OPTIONS value  
    );  
  
```  
  
#### Parameter  
 `mask`  
 Die [SCRIPT\_DEBUGGER\_OPTIONS\-Enumeration](../../winscript/reference/script-debugger-options-enumeration.md) Maske.  
  
 `value`  
 Der [SCRIPT\_DEBUGGER\_OPTIONS\-Enumeration](../../winscript/reference/script-debugger-options-enumeration.md)\-Wert.  
  
## Siehe auch  
 [IRemoteDebugApplication\-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110\-Schnittstelle](../../winscript/reference/iremotedebugapplication110-interface.md)