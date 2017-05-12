---
title: "IObjectIdentity::IsEqualObject | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IObjectIdentity.IsEqualObject
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IsEqualObject-Methode"
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IObjectIdentity::IsEqualObject
Bestimmt, ob ein Objekt gleich dem aktuellen Objekt ist.  
  
## Syntax  
  
```  
HRESULT IsEqualObject(  
  IUnknown*  punk  
);  
```  
  
#### Parameter  
 `punk`  
 \[in\] Adresse des mit dem aktuellen Objekt zu vergleichen, Objekts.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Objekte sind gleich.|  
|`S_FALSE`|Die Objekte sind nicht gleich.|  
  
## Hinweise  
 Eine Implementierung der `IsEqualObject`\-Methode sollte `S_OK` zurückgeben, wenn die Objekte identisch sind.  
  
## Siehe auch  
 [IObjectIdentity\-Schnittstelle](../../winscript/reference/iobjectidentity-interface.md)