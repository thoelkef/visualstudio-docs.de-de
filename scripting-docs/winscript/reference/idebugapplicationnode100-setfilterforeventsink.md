---
title: "IDebugApplicationNode100::SetFilterForEventSink | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::SetFilterForEventSink"
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100::SetFilterForEventSink
Legt den Filter auf einer bestimmten [IDebugApplicationNodeEvents\-Schnittstelle](../../winscript/reference/idebugapplicationnodeevents-interface.md) Implementierung fest.  Sie können Skriptdebuggern, um vom Compiler generierte untergeordnete Anwendungsknoten herauszufiltern, damit das PDM nicht mehr Ereignisse sendet, wenn diese erstellt oder entfernt werden.  Standardmäßig werden alle Knoten gesendet.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100\-Schnittstelle](../../winscript/reference/idebugapplicationnode100-interface.md) wird durch PDM v10.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Syntax  
  
```cpp  
HRESULT SetFilterForEventSink(  
        [in] DWORD dwCookie,  
        [in] APPLICATION_NODE_EVENT_FILTER filter  
        );  
  
```  
  
#### Parameter  
 `dwCookie`  
 Das Cookie des Filters.  
  
 `filter`  
 Der Filter.  
  
## Siehe auch  
 [IDebugApplicationNode100\-Schnittstelle](../../winscript/reference/idebugapplicationnode100-interface.md)