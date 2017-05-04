---
title: "ISimpleConnectionPoint::Unadvise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Unadvise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Unadvise"
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Unadvise
Beendet eine Advise\-Verbindung, die zuvor mit `ISimpleConnectionPoint::Advise` eingerichtet wurde.  
  
## Syntax  
  
```  
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### Parameter  
 `dwCookie`  
 \[in\] Token der Verbindung, zu beenden, wie von `ISimpleConnectionPoint::Advise` zurückgegeben.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Wenn eine Advise\-Verbindung beendet wird, ruft der Verbindungspunkt die `Release`\-Methode auf dem Zeiger an, der für die Verbindung während der `ISimpleConnectionPoint::Advise`\-Methode gespeichert wurde.  Dieser Aufruf gibt `AddRef` um, der während `ISimpleConnectionPoint::Advise` ausgeführt wurde, wenn der Verbindungspunkt `QueryInterface` der Advise\-Senke aufruft.  
  
## Siehe auch  
 [ISimpleConnectionPoint\-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)