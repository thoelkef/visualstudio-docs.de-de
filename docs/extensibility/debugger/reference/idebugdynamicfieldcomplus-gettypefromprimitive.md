---
title: "IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive"
  - "GetTypeFromPrimitive"
ms.assetid: d7f51e2a-1b72-489c-b7b6-4af7b7e4d663
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine einen primitiven Typ angegebenen Typ ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetTypeFromPrimitive(  
   DWORD         dwCorElementType,  
   IDebugField** ppType  
);  
```  
  
```c#  
int GetTypeFromPrimitive(  
   uint            dwCorElementType,  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwCorElementType`  
 [in] Der Wert aus der [CorElementType-Enumeration](CorElementType%20Enumeration.xml) der den primitiven Typ darstellt.  
  
 `ppType`  
 [out] Gibt die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) der den Typ darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Bei erfolgreicher Ausführung gibt `S_OK`andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)