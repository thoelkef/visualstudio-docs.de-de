---
title: "IDebugStackFrameSnifferEx::EnumStackFramesEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrameSnifferEx::EnumStackFramesEx"
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSnifferEx::EnumStackFramesEx
Gibt einen Enumerator von Stapelrahmen für den aktuellen Thread zurück.  
  
## Syntax  
  
```  
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### Parameter  
 `dwSpMin`  
 \[in\] Die niedrigere Adressengrenze zum Auflisten von Stapelrahmen.  
  
 `ppedsf`  
 \[out\] Enumerator von Stapelrahmen für den aktuellen Thread.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Der Stapelrahmenenumerator gibt die Rahmen zuletzt beginnend am Anfang des Stapels, mit den gedrückten Frames zurück.  Der Enumerator enthält nur Stapelrahmen mit Adressen größer oder gleich `dwSpMin`.  
  
## Siehe auch  
 [IDebugStackFrameSnifferEx\-Schnittstelle](../../winscript/reference/idebugstackframesnifferex-interface.md)