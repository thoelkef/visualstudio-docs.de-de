---
title: 'IDebugBinder3:: GetMemoryContext64 | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetMemoryContext64
- IDebugBinder3::GetMemoryContext64
ms.assetid: f021fd16-9fc7-4c41-86af-e54e6224cfbb
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 212ef0435ef8ecd82273a8165c0571025ac01669
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193011"
---
# <a name="idebugbinder3getmemorycontext64"></a>IDebugBinder3::GetMemoryContext64
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Konvertiert entweder einen Objekt Speicherort oder eine 64-Bit-Speicheradresse in einen Speicher Kontext.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetMemoryContext64 (  
   IDebugField*           pField,  
   UINT64                 uConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int GetMemoryContext64 (  
   IDebugField              pField,  
   ulong                    uConstant,  
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pField`  
 in Ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) , das das zu suchende Objekt beschreibt. Wenn `NULL` , dann verwenden Sie `dwConstant` stattdessen.  
  
 `uConstant`  
 in Eine 64-Bit-Speicheradresse, z. b. 0x50.000.000.  
  
 `ppMemCxt`  
 vorgenommen Gibt die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) -Schnittstelle zurück, die die Adresse des-Objekts darstellt, oder die Adresse im Arbeitsspeicher.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 In den folgenden Beispielen wird ein Objekt erstellt, das die [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md) -Schnittstelle implementiert und diese Methode verwendet, um den Arbeitsspeicher Kontext abzurufen.  
  
```cpp#  
HRESULT CValueProperty::GetMemoryContext ( IDebugMemoryContext2** out_ppMemoryContext )  
{  
    // precondition  
    REQUIRE( NULL != out_ppMemoryContext );  
  
    if (NULL == out_ppMemoryContext)  
        return E_POINTER;  
  
    *out_ppMemoryContext = NULL;  
  
    INVARIANT( this );  
  
    if (!this->ClassInvariant())  
        return E_UNEXPECTED;  
  
    if (VT_EMPTY == this->m_VarValue.vt)  
    {  
        return E_FAIL;  
    }  
  
    // function body  
    if (NULL != this->m_pBinder)  
    {  
        UINT64 dwOffset = 0;  
  
        DEBUG_PROPERTY_INFO dpInfo;  
        HRESULT HR = this->GetPropertyInfo(DEBUGPROP_INFO_VALUE,  
                                           10, // RADIX  
                                           DEFAULT_TIMEOUT,  
                                           NULL,  
                                           0,  
                                           &dpInfo);  
        if (ENSURE( S_OK == HR ))  
        {  
            REQUIRE( NULL != dpInfo.bstrValue );  
            REQUIRE( NULL == dpInfo.bstrName );  
            REQUIRE( NULL == dpInfo.bstrFullName );  
            REQUIRE( NULL == dpInfo.bstrType );  
            REQUIRE( NULL == dpInfo.pProperty );  
  
            wchar_t * end;  
            dwOffset = _wcstoui64(dpInfo.bstrValue, &end, 0); // base 0 to allow 0x if it's ever output  
            ::SysFreeString(dpInfo.bstrValue);  
        }  
  
        if (CComQIPtr<IDebugBinder3> binder3 = this->m_pBinder)  
            HR = binder3->GetMemoryContext64(NULL, dwOffset, out_ppMemoryContext);  
        else  
            HR = this->m_pBinder->GetMemoryContext(NULL, (DWORD)(__int32)dwOffset, out_ppMemoryContext);  
  
        if (ENSURE( S_OK == HR ))  
        {  
            REQUIRE( NULL != *out_ppMemoryContext );  
        }  
    }  
  
    // postcondition  
    INVARIANT( this );  
  
    HRESULT HR = E_FAIL;  
  
    if (NULL != *out_ppMemoryContext)  
    {  
        HR = S_OK;  
    }  
  
    return HR;  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
