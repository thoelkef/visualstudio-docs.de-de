---
title: "ISimpleConnectionPoint::Advise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Advise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Advise"
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Advise
Richtet eine Verbindung zwischen dem einfachen Verbindungspunktobjekt und der Senke des Clients ein.  
  
## Syntax  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### Parameter  
 `pdisp`  
 \[in\] Zeiger auf die `IDispatch`\-Schnittstelle der Advise\-Senke des Clients.  Die Senke des Clients empfängt gehende Gespräche vom einfachen Verbindungspunkt.  
  
 `pdwCookie`  
 \[out\] Zeiger auf einen zurückgegebenen Token, das diese Verbindung eindeutig identifiziert.  Der Aufrufer verwendet dieses Token später, um die Verbindung zu löschen, indem er es an die `ISimpleConnectionPoint::Unadvise`\-Methode übergibt.  Wenn die Verbindung nicht erfolgreich hergestellt wurde, ist dieser Wert Null.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode wird eine Verbindung zwischen dem einfachen Verbindungspunktobjekt und der Senke des Clients ein.  
  
## Siehe auch  
 [ISimpleConnectionPoint\-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)