---
title: IDebugObject::SetValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
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
ms.openlocfilehash: 7249c2bc64afea2ca1037cc7fa1cf617357341d7
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Legt den Wert des Objekts aus einer Reihe aufeinander folgenden Bytes fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pValue`  
 [in] Ein Array von Bytes, die den neuen Wert darstellt.  
  
 `nSize`  
 [in] Die Größe des Werts in Bytes.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte im Array werden in diese kopiert [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt, und Ersetzen Sie dabei alle vorhandenen Werte. Die Größe des neuen Werts kann größer oder kleiner als der vorhandene Wert sein. Dies `IDebugObject` darf nicht null-Verweis sein.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
