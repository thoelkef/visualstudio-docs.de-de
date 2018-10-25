---
title: IDebugBinder3::GetTypeArguments | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6ed4e1863313dae173d6737970765ca3d5f0b0b3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879453"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
Diese Methode ruft eine Liste der Argumenttypen, die diesem Objekt zugeordneten ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetTypeArguments(  
   UINT          skip,  
   UINT          count,  
   IDebugField** ppFields,  
   UINT*         pFetched  
);  
```  
  
```csharp  
int GetTypeArguments(  
   uint          skip,  
   uint          count,  
   IDebugField[] ppFields,  
   out uint      pFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `skip`  
 [in] Die Anzahl von Feldern, die vor dem Abrufen von Argumenttypen übersprungen werden.  
  
 `count`  
 [in] Die Anzahl der zurückzugebenden Felder Argument (gibt auch die Größe der an die `ppFields` Array).  
  
 `ppFields`  
 [in, out] Ein Array von Feldern, die bei der Rückgabe dieser Methode gefüllt werden.  
  
 `pFetched`  
 [out] \(optional) Geben Sie die Nummer des Arguments tatsächlich zurückgegebenen Felder.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Anzahl der Argumenttypen erhalten Sie im voraus mit [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)