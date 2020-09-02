---
title: 'Idebugcomplussymbolprovider:: isfunctiondeleted | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::IsFunctionDeleted
ms.assetid: b276bd25-6658-4898-bc36-04ecdf92aa2f
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 904eb54729298f29b98b5ae7dae0aa759a1119de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187213"
---
# <a name="idebugcomplussymbolproviderisfunctiondeleted"></a>IDebugComPlusSymbolProvider::IsFunctionDeleted
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bestimmt, dass die Funktion an der angegebenen debugadresse gelöscht wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT IsFunctionDeleted(  
   IDebugAddress* pAddress  
);  
```  
  
```csharp  
int IsFunctionDeleted(  
   IDebugAddress pAddress  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pAddress`  
 in Die von einer [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle dargestellte debugadresse. Bei dieser Adresse muss es sich um einen METHOD_ADDRESS handeln.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Funktion gelöscht wird, wird zurückgegeben `S_OK` . Wenn die Funktion vorhanden ist, wird zurückgegeben `S_FALSE` .  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **cdebugsymbolprovider** -Objekt implementiert wird, das die [idebugcomplussymbolprovider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) -Schnittstelle verfügbar macht.  
  
```cpp#  
HRESULT CDebugSymbolProvider::IsFunctionDeleted(  
    IDebugAddress* pAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pAddress, IDebugAddress));  
  
    METHOD_ENTRY( CDebugSymbolProvider::IsFunctionDeleted );  
  
    IfFalseGo( pAddress, S_FALSE );  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    if (!pModule->IsFunctionDeleted( address.addr.addr.addrMethod.tokMethod,  
                                     address.addr.addr.addrMethod.dwVersion,  
                                     address.addr.addr.addrMethod.dwOffset ))  
    {  
  
        // S_FALSE indicates the function is not deleted  
  
        hr = S_FALSE;  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::IsFunctionDeleted, hr );  
  
    if (!SUCCEEDED(hr))  
    {  
        hr = S_FALSE;  
    }  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
