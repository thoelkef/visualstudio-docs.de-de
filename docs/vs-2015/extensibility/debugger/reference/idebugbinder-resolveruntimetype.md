---
title: IDebugBinder::ResolveRuntimeType | Microsoft-Dokumentation
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
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e1ac794f7ba3cc3b47cf96dacde850845fd07c9e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513022"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugBinder::ResolveRuntimeType](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder-resolveruntimetype).  
  
Diese Methode bestimmt der Laufzeittyp eines Objekts.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der Laufzeittyp eines Objekts ist nicht immer zum Zeitpunkt der Kompilierung bekannt. Beispielsweise kann Polymorphismus verwendet wird, ein Argument an eine Funktion als Basisklasse, z. B. eine Button-Klasse übergeben werden. Das tatsächliche Argument möglicherweise eine abgeleitete Klasse wie z. B. eine Radio Button-Klasse.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

