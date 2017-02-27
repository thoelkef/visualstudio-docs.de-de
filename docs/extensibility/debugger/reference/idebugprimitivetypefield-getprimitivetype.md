---
title: "IDebugPrimitiveTypeField::GetPrimitiveType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetPrimitiveType"
  - "IDebugPrimitiveTypeField::GetPrimitiveType"
ms.assetid: a186c922-bbfe-478c-a744-b21eb4672d8f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPrimitiveTypeField::GetPrimitiveType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den primitiven Typ, der mit diesem Feld zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetPrimitiveType (  
   DWORD* pdwType  
);  
```  
  
```c#  
int GetPrimitiveType (  
   out uint pdwType  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwType`  
 [out] Der Wert aus der [CorElementType-Enumeration](CorElementType%20Enumeration.xml) der den primitiven Typ darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)