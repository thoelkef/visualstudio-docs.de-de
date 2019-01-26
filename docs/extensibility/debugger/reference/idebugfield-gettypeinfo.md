---
title: IDebugField::GetTypeInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 931589bd319c86c17b2db2e9acbaccc556725263
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983299"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Diese Methode ruft die typunabhängig-Informationen über das Symbol oder einen Typ ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetTypeInfo(   
   TYPE_INFO* pTypeInfo  
);  
```  
  
```csharp  
int GetTypeInfo(  
   TYPE_INFO[] pTypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pTypeInfo`  
 [out] Gibt die Typinformationen in der angegebenen [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Struktur.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Typunabhängig Informationen, z. B. gehören der AppDomain, das Modul und Klasse, die das Symbol enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)