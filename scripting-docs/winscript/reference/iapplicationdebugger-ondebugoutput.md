---
title: "IApplicationDebugger::onDebugOutput | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onDebugOutput
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onDebugOutput"
ms.assetid: 978d8bcf-16dc-4f24-a6bc-206adee2b2e9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onDebugOutput
Behandelt ein Debug\- Ausgabeereignis.  
  
## Syntax  
  
```  
HRESULT onDebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### Parameter  
 `pstr`  
 \[in\] im Debugger anzuzeigen, Zeichenfolge.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Der Debugger zeigt in der Regel `pstr` in einem Ausgabefenster an.  
  
 Diese Methode wird aufgerufen, wenn `IDebugApplication::DebugOutput` aufgerufen wird.  
  
## Siehe auch  
 [IApplicationDebugger\-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)