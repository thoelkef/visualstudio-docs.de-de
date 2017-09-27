---
title: IDebugObject::IsNullReference | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: dee4f1909ec5f6e66c7f828b5552ff424b4d9edc
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Testet, ob dieses Objekt einen null-Verweis ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```csharp  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pfIsNull`  
 [out] Ungleich 0 (null) zurückgibt (`TRUE`) Wenn dieses Objekt ein Verweis null ist, andernfalls 0 (null) (`FALSE`).  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein null-Verweis bedeutet, dass ein leeres Objekt oder ein Objekt, das nicht zugewiesen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
