---
title: IDebugEngine2::RemoveAllSetExceptions | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords: IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c4a70cf4d0f77ab86bbb919dfcdc40a8ad59dd0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Entfernt die Liste der Ausnahmen, die für eine bestimmte Laufzeit-Architektur oder die Sprache die IDE festgelegt hat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```csharp  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `guidType`  
 [in] Die GUID für die Sprache oder die GUID für das Debugging-Modul, das spezifisch für eine Laufzeit-Architektur ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Ausnahmen, die von dieser Methode entfernt wurden von früheren aufrufen, Festlegen der [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) Methode.  
  
 Um eine bestimmte Ausnahme zu entfernen, rufen Sie die [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)