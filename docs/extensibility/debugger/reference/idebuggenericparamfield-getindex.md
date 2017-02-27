---
title: "IDebugGenericParamField::GetIndex | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugGenericParamField::GetIndex"
ms.assetid: 8e0bdb26-1247-44d9-8d80-ec6e35187fb4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugGenericParamField::GetIndex
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Index dieses generischen Parameters ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetIndex(  
   DWORD* pIndex  
);  
```  
  
```c#  
int GetIndex(  
   out uint pIndex  
);  
```  
  
#### Parameter  
 `pIndex`  
 \[out\]  Indexwert des generischen Parameters.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Zum Beispiel für Wörterbuch \(K, V\), K ist Index 0, V ist Index 1.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein **CDebugGenericParamFieldType\-Objekt** implementiert, das die [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::GetIndex(DWORD* pIndex)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetIndex );  
  
    IfFalseGo(pIndex, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    *pIndex = m_index;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetIndex, hr );  
    return hr;  
}  
```  
  
## Siehe auch  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)