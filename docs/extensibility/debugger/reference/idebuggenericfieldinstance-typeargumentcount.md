---
title: "IDebugGenericFieldInstance::TypeArgumentCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TypeArgumentCount"
  - "IDebugGenericFieldInstance::TypeArgumentCount"
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugGenericFieldInstance::TypeArgumentCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Anzahl der Parameterargumente für diese Instanz zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT TypeArgumentCount(  
   ULONG32* pcArgs  
);  
```  
  
```c#  
int TypeArgumentCount(  
   ref uint pcArgs  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcArgs`  
 [in, out] Die Anzahl von Typargumenten für Parameter für diese Instanz.  
  
## <a name="return-value"></a>Rückgabewert  
 Bei erfolgreicher Ausführung gibt `S_OK`andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Z. B. wenn Liste \< Int>, diese Methode gibt 1 zurück, und, wenn die Liste \< Int, float2 > Diese Methode gibt 2 zurück. Diese Methode gibt 0 zurück, wenn es keine Typargumente sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)