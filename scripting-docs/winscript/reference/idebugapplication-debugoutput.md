---
title: "IDebugApplication::DebugOutput | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.DebugOutput
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::DebugOutput"
ms.assetid: 6c02939c-3c2d-474a-ab15-49a37e22b4a7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::DebugOutput
Ruft die angegebene Zeichenfolge, durch die Debuggerintegrierte Entwicklungsumgebung \(IDE\) angezeigt werden.  
  
## Syntax  
  
```  
HRESULT DebugOutput(  
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
 Mit dieser Methode können Debugging\-Ausgabeunterstützung ein Sprachmodul von implementieren den sprachspezifischen.  Die Zeichenfolge wird in der Regel im Ausgabefenster des Debuggers angezeigt.  
  
 Diese Methode wird `IApplicationDebugger::onDebugOutput` aufgerufen werden.  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)