---
title: IDebugEngine3::SetJustMyCodeState | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e612b39bb71465aff50095dfeecf01cd025c4f2d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513153"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugEngine3::SetJustMyCodeState](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengine3-setjustmycodestate).  
  
Diese Methode teilt die Debug-Engine zu den JustMyCode-Status-Informationen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fUpdate`  
 [in] Ungleich Null (`TRUE`) um aktuelle Informationen zu aktualisieren, NULL (`FALSE`) alle Informationen, die (wird ignoriert, alle zuvor festgelegten) zurücksetzen.  
  
 `dwModules`  
 [in] Anzahl der Informationsstrukturen in `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in] Array von [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Strukturen verwenden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.  
  
## <a name="remarks"></a>Hinweise  
 JustMyCode ist das Konzept der nur den Code Debuggen, der zu einem Benutzer gehört, und wird ignoriert, alle temporären Code wie z. B. Systemcode – selbst wenn der Quellcode für diesen Systemcode verfügbar ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)

