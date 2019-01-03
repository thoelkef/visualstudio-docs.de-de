---
title: IEnumDebugCodeContexts2::Reset | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugCodeContexts2::Reset
helpviewer_keywords:
- IEnumDebugCodeContexts2::Reset
ms.assetid: df6cf1e3-2ef8-4d38-81a0-8e9adf151884
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39eb109f03931cb4a499ad7a27580323c7e407b6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898808"
---
# <a name="ienumdebugcodecontexts2reset"></a>IEnumDebugCodeContexts2::Reset
Setzt die Enumeration auf das erste Element zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Nachdem diese Methode aufgerufen wird, wird beim nächsten Aufruf von der [Weiter](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md) Methode gibt das erste Element der Enumeration.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)