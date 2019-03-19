---
title: IDebugApplicationNode100::SetFilterForEventSink | Microsoft-Dokumentation
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
ms.openlocfilehash: f1a59f57daad90e5a7df1a8d8fa8d1ecd8c5c3bf
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154295"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Legt den Filter für eine bestimmte [IDebugApplicationNodeEvents-Schnittstelle](../../winscript/reference/idebugapplicationnodeevents-interface.md) Implementierung. Sie können die Skriptdebugger, um vom Compiler generierten untergeordneten Anwendungsknoten zu filtern, damit das PDM mehr senden, werden Ereignisse aus, wenn diese erstellt oder entfernt werden. Standardmäßig werden alle Knoten gesendet.  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100-Schnittstelle](../../winscript/reference/idebugapplicationnode100-interface.md) wird implementiert von PDM v10. 0 und höher. Gefunden in activdbg100.h.  
  
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