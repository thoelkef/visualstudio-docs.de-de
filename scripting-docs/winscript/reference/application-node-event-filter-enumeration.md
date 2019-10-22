---
title: APPLICATION_NODE_EVENT_FILTER-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- APPLICATION_NODE_EVENT_FILTER Constants
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 481e015ec84d833f52220276bffa4ce0163f98ff
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572650"
---
# <a name="application_node_event_filter-enumeration"></a>APPLICATION_NODE_EVENT_FILTER-Schnittstelle
Gibt die Typen von Knoten an, die beim Filtern von Code Dokumenten ausgeschlossen werden sollen. Wird in [IDebugApplicationNode100:: getexcludezddocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) und [IDebugApplicationNode100:: setfilterforeventsink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md) verwendet.  
  
> [!IMPORTANT]
> Diese Konstanten werden von PDM v 10.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {    FILTER_EXCLUDE_NOTHING = 0,    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,    FILTER_EXCLUDE_EVAL_CODE = 0x2} APPLICATION_NODE_EVENT_FILTER;  
```  
  
## <a name="members"></a>Member  
  
|Member|Wert|Beschreibung|  
|------------|-----------|-----------------|  
|FILTER_EXCLUDE_NOTHING|0x00000000|Alle Ereignisse senden.|  
|FILTER_EXCLUDE_ANONYMOUS_CODE|0x00000001|Ausschließen anonymer Code Knoten. Diese Knoten werden von der JScript-Laufzeit für die `new Function([args,] <code>)'` verwendet.|  
|FILTER_EXCLUDE_EVAL_CODE|0x00000002|Ausschließen von eval-Code Knoten. Diese Knoten werden von der JScript-Laufzeit für die Eval-Unterstützung verwendet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)