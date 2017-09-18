---
title: "IDebugGenericFieldDefinition::GetFormalTypeParams | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetFormalTypeParams"
  - "IDebugGenericFieldDefinition::GetFormalTypeParams"
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugGenericFieldDefinition::GetFormalTypeParams
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Typparameter angesichts der Anzahl von Parametern ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetFormalTypeParams(  
   ULONG32                   cParams,  
   IDebugGenericParamField** ppParams,  
   ULONG32*                  pcParams  
);  
```  
  
```c#  
int GetFormalTypeParams(  
   uint                          cParams,  
   out IDebugGenericParamField[] ppParams,  
   ref uint                      pcParams  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cParams`  
 [in] Die Anzahl von Parametern.  
  
 `ppParams`  
 [out] Ein Array von Typparametern.  
  
 `pcParams`  
 [in, out] Anzahl von Parametern in der `ppParams` Array.  
  
## <a name="return-value"></a>Rückgabewert  
 Bei erfolgreicher Ausführung gibt `S_OK`andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der Typparameter in der Reihenfolge von links nach rechts zurück. So gibt z. B. Dictionary \< K, V > IDebugFormalGenericParameters {K, V} zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)