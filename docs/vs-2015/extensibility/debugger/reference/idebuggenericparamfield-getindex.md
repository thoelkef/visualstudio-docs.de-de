---
title: IDebugGenericParamField::GetIndex | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugGenericParamField::GetIndex
ms.assetid: 8e0bdb26-1247-44d9-8d80-ec6e35187fb4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0b1e91e4dcf7429a9d803ede22cde8f71d431ec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814363"
---
# <a name="idebuggenericparamfieldgetindex"></a>IDebugGenericParamField::GetIndex
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Index dieses generischen Parameters ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetIndex(  
   DWORD* pIndex  
);  
```  
  
```csharp  
int GetIndex(  
   out uint pIndex  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pIndex`  
 [out] Der Indexwert des dieser generische Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Klicken Sie beispielsweise für Dictionary(K,V), K ist Index 0, V Index 1 ist.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CDebugGenericParamFieldType** -Objekt, das macht die [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) Schnittstelle.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)

