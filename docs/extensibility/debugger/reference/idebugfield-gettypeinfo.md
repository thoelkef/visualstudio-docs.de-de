---
title: IDebugField::GetTypeInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetTypeInfo
helpviewer_keywords: IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9f1ec3adf1f71d5d7f7e916b261555ca8aeb9d31
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Diese Methode ruft die typunabhängig Informationen über das Symbol oder den Typ ab.  
  
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
 [out] Gibt die Typinformationen im bereitgestellten [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Struktur.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Typunabhängig Informationen zählen, z. B. der AppDomain, das Modul und die Klasse, die das Symbol enthält.  
  
## <a name="see-also"></a>Siehe auch  
 ["GetType"](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)