---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9359637a4a1bbd1650a80c8210f615964703d68
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907767"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Um zu bestimmen, warum ein Auto-attach fehlgeschlagenen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```csharp  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszUrl`  
 [in] Derzeit nicht verwendet. sollte immer auf einen null-Wert festgelegt werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Im folgenden finden andere typische Rückgabecodes:  
  
|Code|Beschreibung|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Kann nicht ermitteln, warum der Remoteserver zum Starten des Debuggings fehlgeschlagen ist.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Kann nicht auf Remoteserver, möglicherweise aufgrund unzureichender Berechtigungen debuggen, oder weil das DEBUG-Verb nicht aktiviert ist.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Der Webserver wurde gesperrt und blockiert das DEBUG-Verb, ist erforderlich, um Debuggen zu aktivieren.|  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

