---
title: "ICanHandleException::CanHandleException | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ICanHandleException.CanHandleException
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ICanHandleException::CanHandleException"
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ICanHandleException::CanHandleException
Bestimmt, ob der Aufrufer des Skriptmoduls eine bestimmte Ausnahme behandeln kann.  
  
## Syntax  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### Parameter  
 `pExcepInfo`  
 \[in\] Zeiger auf eine `EXCEPINFO`\-Struktur, die die Informationen enthält, die gemeldet werden, wenn kein Ausnahmehandler gefunden wird.  
  
 `pvar`  
 \[in\] Ein der Ausnahme zugeordneter Wert, beispielsweise der Wert ausgelöst durch eine `throw`\-Anweisung.  Dieser Parameter kann `NULL` sein.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Der Aufrufer kann die Ausnahme behandeln|  
|`E_FAIL`|Der Aufrufer kann die Ausnahme nicht behandeln.|  
  
## Hinweise  
 Wenn ein Aufruf `IDispatchEx::InvokeEx` oder eine ähnliche Methode, eine Ausnahme ergibt, die Skriptmodulüberprüfungen für einen Aufrufer in der Anruferkette des Skripts, die die `ICanHandleException`\-Schnittstelle unterstützt und angibt, dass die Ausnahme behandeln kann.  Wenn kein Aufrufer die Ausnahme behandeln kann, die Skriptmodulhalte.  
  
## Siehe auch  
 [ICanHandleException\-Schnittstelle](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)