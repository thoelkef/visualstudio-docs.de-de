---
title: "APPLICATION_NODE_EVENT_FILTER-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "APPLICATION_NODE_EVENT_FILTER-Konstanten"
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# APPLICATION_NODE_EVENT_FILTER-Schnittstelle
Gibt die Typen von Knoten an, um auszuschließen, wenn, Codedokumente Filtern.  Wird in [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) und in [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Diese Konstanten werden durch PDM v10.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Syntax  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {  
    FILTER_EXCLUDE_NOTHING = 0,  
    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,  
    FILTER_EXCLUDE_EVAL_CODE = 0x2  
} APPLICATION_NODE_EVENT_FILTER;  
  
```  
  
## Mitglieder  
  
|Member|Wert|Description|  
|------------|----------|-----------------|  
|FILTER\_EXCLUDE\_NOTHING|0x00000000|Senden Sie alle Ereignisse.|  
|FILTER\_EXCLUDE\_ANONYMOUS\_CODE|0x00000001|Schließen Sie anonyme Codeknoten aus.  Diese Knoten werden von der JScript\-Runtime für `new Function([args,] <code>)'` verwendet.|  
|FILTER\_EXCLUDE\_EVAL\_CODE|0x00000002|Schließen Sie eval Codeknoten aus.  Diese Knoten werden von der JScript\-Runtime für eval Unterstützung verwendet.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script\-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)