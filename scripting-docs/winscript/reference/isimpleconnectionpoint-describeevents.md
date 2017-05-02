---
title: "ISimpleConnectionPoint::DescribeEvents | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.DescribeEvents
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::DescribeEvents"
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::DescribeEvents
Gibt den DISPID und den Namen für jedes Ereignis in einem angegebenen Bereich von Ereignissen zurück.  
  
## Syntax  
  
```  
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### Parameter  
 `iEvent`  
 \[in\] Index des ersten Ereignisses abzurufen.  
  
 `cEvents`  
 \[in\] Zahl abzurufen Ereignisse.  
  
 `prgid`  
 \[out\] Array Werte des Ereignisses DISPID.  
  
 `prgbstr`  
 \[out\] Array Ereignisnamen.  
  
 `pcEventsFetched`  
 \[out\] Die tatsächliche Anzahl der Ereignisse abgerufen.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`S_FALSE`|Mehrere Ereignisse angefordert wurden, als verfügbar waren.  Nicht verfügbare Ereignisse werden mit DISPID\_NULL und einer NULL BSTR dargestellt.|  
|`E_INVALIDARG`|Keine Elemente können abgerufen werden.|  
  
## Hinweise  
 Diese Methode gibt das DISPID und den Namen für jedes Ereignis in einem angegebenen Bereich von Ereignissen zurück.  
  
## Siehe auch  
 [ISimpleConnectionPoint\-Schnittstelle](../../winscript/reference/isimpleconnectionpoint-interface.md)