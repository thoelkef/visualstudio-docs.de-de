---
title: IEnumDebugCodeContexts2::Next | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugCodeContexts2::Next
helpviewer_keywords: IEnumDebugCodeContexts2::Next
ms.assetid: 0d8aa2db-0994-4166-b364-2e25d936fffc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 63484e42f79e11ca4f3d42b95e5fdef02cba2de5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugcodecontexts2next"></a>IEnumDebugCodeContexts2::Next
Gibt den nächsten Satz von Elementen aus der Enumeration zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Next(  
   ULONG                celt,  
   IDebugCodeContext2** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                 celt,  
   IDebugCodeContext2[] rgelt,  
   ref uint             pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der abzurufenden Elemente. Außerdem gibt die maximale Größe von der `rgelt` Array.  
  
 `rgelt`  
 [in, out] Array von [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Elemente ausgefüllt werden.  
  
 `pceltFetched`  
 [out] Gibt die Anzahl der Elemente, die tatsächlich im zurückgegebenen `rgelt`.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` Wenn weniger als die angeforderte Anzahl von Elementen zurückgegeben werden konnte; andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)