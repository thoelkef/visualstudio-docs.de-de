---
title: IDebugBinder::ResolveRuntimeType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder::ResolveRuntimeType
helpviewer_keywords: IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fcaca4e27f7a4e986222e3fa6767a106ef6d90d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Diese Methode bestimmt den Laufzeittyp eines Objekts.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```csharp  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pObject`  
 [in] Die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) aufgelöst werden.  
  
 `ppResolved`  
 [out] Gibt den Typ des Objekts als ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der Laufzeittyp eines Objekts ist nicht immer zum Zeitpunkt der Kompilierung bekannt. Beispielsweise kann mithilfe von Polymorphie, ein Argument werden an eine Funktion wie seine Basisklasse, z. B. eine Schaltflächenklasse übergeben. Das tatsächliche Argument möglicherweise eine abgeleitete Klasse, z. B. eine Radio Button-Klasse.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)