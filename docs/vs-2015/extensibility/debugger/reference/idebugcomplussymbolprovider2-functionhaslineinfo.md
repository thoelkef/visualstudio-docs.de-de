---
title: 'IDebugComPlusSymbolProvider2:: functionhaslineingefo | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- FunctionHasLineInfo
- IDebugComPlusSymbolProvider2::FunctionHasLineInfo
ms.assetid: e1b508f1-6521-492f-b110-ab957744a037
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6669d06b75877e548758f08d92fcb8ade7bcb04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205315"
---
# <a name="idebugcomplussymbolprovider2functionhaslineinfo"></a>IDebugComPlusSymbolProvider2::FunctionHasLineInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bestimmt, ob die angegebene Methode über Zeilen Informationen verfügt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT FunctionHasLineInfo(  
   IDebugAddress* pAddress  
);  
```  
  
```csharp  
int FunctionHasLineInfo(  
   IDebugAddress pAddress  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pAddress`  
 in Die Debug-Adresse, die durch eine [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle dargestellt wird. Bei dieser Adresse muss es sich um einen METHOD_ADDRESS handeln.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben `S_FALSE` .  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **cdebugsymbolprovider** -Objekt implementiert wird, das die [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) -Schnittstelle verfügbar macht.  
  
```cpp#  
HRESULT CDebugSymbolProvider::FunctionHasLineInfo(  
    IDebugAddress* pAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
  
    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );  
  
    IfFalseGo( pAddress, E_INVALIDARG );  
  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    if (!pModule->FunctionHasLineInfo( address.addr.addr.addrMethod.tokMethod,  
                                       address.addr.addr.addrMethod.dwVersion))  
    {  
  
        // S_FALSE indicates this method does not have line info  
  
        hr = S_FALSE;  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
