---
title: "IDebugGenericParamField::ConstraintCount | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ConstraintCount"
  - "IDebugGenericParamField::ConstraintCount"
ms.assetid: 76bef0cb-8a3c-4ce5-87cc-1809de229f33
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugGenericParamField::ConstraintCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Anzahl der Einschränkungen zurück, die bei diesem generischen Parameter zugeordnet sind.  
  
## Syntax  
  
```cpp#  
HRESULT ConstraintCount(  
   ULONG32* pcConst  
);  
```  
  
```c#  
int ConstraintCount(  
   ref uint pcConst  
);  
```  
  
#### Parameter  
 `pcConst`  
 \[in, out\]  Die Anzahl der Einschränkungen, die diesem Feld zugeordnet sind.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein **CDebugGenericParamFieldType\-Objekt** implementiert, das die [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::ConstraintCount(ULONG32* pcConst)  
{  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetadata;  
    CComPtr<IMetaDataImport2> pMetadata2;  
    HCORENUM hEnum = 0;  
    ULONG cConst = 0;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::ConstraintCount );  
  
    IfFalseGo(pcConst, E_INVALIDARG );  
    *pcConst = 0;  
    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );  
    IfFailGo( pMetadata->QueryInterface(IID_IMetaDataImport2, (void**)&pMetadata2) );  
    IfFailGo( pMetadata2->EnumGenericParamConstraints( &hEnum,  
              m_tokParam,  
              NULL,  
              0,  
              &cConst) );  
    IfFailGo( pMetadata->CountEnum(hEnum, &cConst) );  
    pMetadata->CloseEnum(hEnum);  
    hEnum = NULL;  
  
    *pcConst = cConst;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::ConstraintCount, hr );  
    return hr;  
}  
```  
  
## Siehe auch  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)