---
title: IDebugEngine3::SetJustMyCodeState | Microsoft-Dokumentation
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
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a57dba60a4a2bebafa222a7b7dcabf620f18b399
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289600"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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

