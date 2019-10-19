---
title: 'IDebugApplicationNode100:: setfilterforeventsink | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f85241bee7b35d40bf193a613a6fefda4265be6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574724"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Legt den Filter für eine bestimmte [idebugapplicationnodeevents-Schnittstellen](../../winscript/reference/idebugapplicationnodeevents-interface.md) Implementierung fest. Sie ermöglicht es Skript-Debuggern, vom Compiler generierte untergeordnete Anwendungs Knoten herauszufiltern, damit das PDM keine Ereignisse mehr sendet, wenn diese erstellt oder entfernt werden. Standardmäßig werden alle Knoten gesendet.  
  
> [!IMPORTANT]
> Die [IDebugApplicationNode100-Schnittstelle](../../winscript/reference/idebugapplicationnode100-interface.md) wird von PDM v 10.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwCookie`  
 Das Cookie des Filters.  
  
 `filter`  
 Der Filter.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationNode100-Schnittstelle](../../winscript/reference/idebugapplicationnode100-interface.md)