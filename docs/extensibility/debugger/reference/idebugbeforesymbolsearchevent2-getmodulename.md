---
title: IDebugBeforeSymbolSearchEvent2::GetModuleName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetModuleName
- IDebugBeforeSymbolSearchEvent2::GetModuleName
ms.assetid: 0b4abeac-2eaf-4b2e-a2d5-c9ec303bc869
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 005b725e3d03166188fa56342c9609707236c08d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865185"
---
# <a name="idebugbeforesymbolsearchevent2getmodulename"></a>IDebugBeforeSymbolSearchEvent2::GetModuleName
Ruft den Namen des Moduls, die gerade gedebuggt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetModuleName(   
   BSTR *pbstrModuleName  
);  
```  
  
```csharp  
public int GetModuleName (  
   string pbstrModuleName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrModuleName`  
 [out] Der Name des Moduls.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CDebugBeforeSymbolSearchEventBase** -Objekt, das macht die [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) Schnittstelle.  
  
```cpp  
STDMETHODIMP CDebugBeforeSymbolSearchEventBase::GetModuleName(BSTR *pbstrModuleName)  
{  
    HRESULT hRes = E_FAIL;  
  
    if (m_bstrModuleName)  
    {  
  
        *pbstrModuleName = SysAllocString( m_bstrModuleName);  
  
        if (*pbstrModuleName)  
        {  
            hRes = S_OK;  
        }  
    }  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)