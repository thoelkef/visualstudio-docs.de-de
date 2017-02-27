---
title: "IDebugGenericParamField::GetFlags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetFlags"
  - "IDebugGenericParamField::GetFlags"
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugGenericParamField::GetFlags
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Flags für diesen generischen Parameter ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetFlags(  
   DWORD* pdwFlags  
);  
```  
  
```c#  
int GetFlags(  
   ref uint pdwFlags  
);  
```  
  
#### Parameter  
 `pdwFlags`  
 \[out\]  Gibt die Flags für diesen generischen Parameter zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Flags enthalten Informationen über verschiedene spezielle Einschränkungen.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein **CDebugGenericParamFieldType\-Objekt** implementiert, das die [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::GetFlags(DWORD *pdwFlags)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetFlags );  
  
    IfFalseGo( pdwFlags, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    *pdwFlags = m_dwFlags;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetFlags, hr );  
    return hr;  
}  
```  
  
## Siehe auch  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)