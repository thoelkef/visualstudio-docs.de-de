---
title: IDebugComPlusSymbolProvider::GetAssemblyName | Microsoft-Dokumentation
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
- IDebugComPlusSymbolProvider::GetAssemblyName
- GetAssemblyName
ms.assetid: a08cd609-b9b9-47bd-bf73-cbf851285907
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3822412961cfced73b6773bab6265016c5924f18
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177113"
---
# <a name="idebugcomplussymbolprovidergetassemblyname"></a>IDebugComPlusSymbolProvider::GetAssemblyName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Namen der Assembly bei Angabe der Modul- und Domäne ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
[C++]  
HRESULT GetAssemblyName(  
   ULONG32 ulAppDomainID,  
   GUID    guidModule,  
   BSTR*   pbstrName  
);  
```  
  
```  
[C#]  
int GetAssemblyName(  
   uint   ulAppDomainID,  
   Guid   guidModule,  
   string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ulAppDomainID`  
 [in] Der Bezeichner für die Anwendungsdomäne.  
  
 `guidModule`  
 [in] Eindeutiger Bezeichner für das Modul.  
  
 `pbstrName`  
 [out] Gibt den Namen der Assembly.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CDebugSymbolProvider** -Objekt, das macht die [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) Schnittstelle.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetAssemblyName(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    BSTR* pbstrName  
)  
{  
    HRESULT hr = S_OK;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    CComPtr<IMetaDataImport> pMetadata;  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetMetadataForModule );  
  
    IfFalseGo( pbstrName, E_INVALIDARG );  
    *pbstrName = NULL;  
  
    IfFailGo( GetMetadata( idModule, &pMetadata ) );  
    IfFailGo( GetAssemblyName( pMetadata, 0, pbstrName ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetMetadataForModule, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)

