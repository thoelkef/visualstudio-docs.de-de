---
title: "IDebugSessionProviderEx:CanJITDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSessionProviderEx:CanJITDebug
apilocation: scrobj.dll
ms.assetid: 68f91bed-ca69-46b5-b517-ca9ca80b8803
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDebugSessionProviderEx:CanJITDebug
Bestimmt, ob ein gegebener Prozess mit Just\-in\-timedebugging gedebuggt werden kann.  
  
## Syntax  
  
```  
HRESULT CanJITDebug(  
   DWORD  pid  
);  
```  
  
#### Parameter  
 `pid`  
 \[in\] Die Prozess\-ID, damit der Prozess gedebuggt werden kann.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IDebugSessionProviderEx\-Schnittstelle](../../winscript/reference/idebugsessionproviderex-interface.md)