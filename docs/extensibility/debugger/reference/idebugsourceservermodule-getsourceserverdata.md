---
title: IDebugSourceServerModule::GetSourceServerData | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSourceServerModule::GetSourceServerData
ms.assetid: f15d86aa-1bd9-4b16-a64a-21b01c27db2e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6535944a60af02dc3bb082c08b03795a28a61819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsourceservermodulegetsourceserverdata"></a>IDebugSourceServerModule::GetSourceServerData
Ruft ein Array von Serverinformationen Quelle ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetSourceServerData(  
   ULONG* pDataByteCount,   
   BYTE** ppData  
);  
```  
  
```csharp  
public int GetSourceServerData(  
   out uint  pDataByteCount,   
   out int[] ppData  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pDataByteCount`  
 [out] Anzahl der Bytes im Datenarray.  
  
 `ppData`  
 [out] Verweis auf das Datenarray.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Implementierung dieser Methode für eine **CModule** -Objekt, das macht die [IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md) Schnittstelle.  
  
```cpp  
HRESULT CModule::GetSourceServerData(ULONG* pDataByteCount, BYTE** ppData)  
{  
    HRESULT hr = S_OK;  
    CComPtr<ISymUnmanagedReader> pSymReader;  
    CComPtr<ISymUnmanagedSourceServerModule> pSourceServerModule;  
  
    IfFalseGo( pDataByteCount && ppData, E_INVALIDARG );  
    *pDataByteCount = 0;  
    *ppData = NULL;  
  
    IfFailGo( this->GetUnmanagedSymReader( &pSymReader ) );  
    IfFailGo( pSymReader->QueryInterface( &pSourceServerModule ) );  
  
    IfFailGo( pSourceServerModule->GetSourceServerData( pDataByteCount, ppData ) );  
  
Error:  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)