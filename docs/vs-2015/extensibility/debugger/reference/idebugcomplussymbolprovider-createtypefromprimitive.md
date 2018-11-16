---
title: IDebugComPlusSymbolProvider::CreateTypeFromPrimitive | Microsoft-Dokumentation
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
- IDebugComPlusSymbolProvider::CreateTypeFromPrimitive
- CreateTypeFromPrimitive
ms.assetid: 37213cc2-a038-42ea-9b28-3ae40d4cfe69
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1a91f29892cba2552462df0ebab96133b04afd78
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750491"
---
# <a name="idebugcomplussymbolprovidercreatetypefromprimitive"></a>IDebugComPlusSymbolProvider::CreateTypeFromPrimitive
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt einen vom angegebenen primitiven Typs.  
  
## <a name="syntax"></a>Syntax  
  
```  
[C++]  
HRESULT CreateTypeFromPrimitive(  
   DWORD          dwPrimType,  
   IDebugAddress* pAddress,  
   IDebugField**  ppType  
);  
```  
  
```  
[C#]  
int CreateTypeFromPrimitive(  
   uint          dwPrimType,  
   IDebugAddress pAddress,  
   IDebugField   ppType  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwPrimType`  
 [in] Wert aus der [CorElementType-Enumeration](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) , den primitiven Typ darstellt.  
  
 `pAddress`  
 [in] Durch dargestellt wird ein Adressobjekt ein [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle.  
  
 `ppType`  
 [in] Gibt eine [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) -Objekt, das den Typ beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CDebugSymbolProvider** -Objekt, das macht die [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) Schnittstelle.  
  
```cpp#  
HRESULT CDebugSymbolProvider::CreateTypeFromPrimitive(  
    DWORD dwPrimType,  
    IDebugAddress* pAddress,  
    IDebugField** ppType)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS addr;  
    const COR_SIGNATURE* pTypeInfo = (const COR_SIGNATURE*) & dwPrimType;  
    CDebugGenericParamScope* pGenScope = NULL;  
  
    //  
    // This function will only work for primitive types  
    //  
  
    METHOD_ENTRY( CDebugSymbolProvider::CreateTypeFromPrimitive );  
  
    IfFailGo( pAddress->GetAddress( &addr ) );  
  
    IfNullGo( pGenScope = new CDebugGenericParamScope(addr.GetModule(), addr.tokClass, addr.GetMethod()), E_OUTOFMEMORY );  
  
    IfFailGo( CreateType( pTypeInfo,  
                          1,  
                          addr.GetModule(),  
                          addr.GetMethod(),  
                          pGenScope,  
                          ppType ) );  
  
    METHOD_EXIT( CDebugSymbolProvider::CreateTypeFromPrimitive, hr );  
  
Error:  
  
    RELEASE( pGenScope );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)

