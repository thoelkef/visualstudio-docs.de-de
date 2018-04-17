---
title: IDebugSymbolProviderDirect::GetAppIDFromAddress | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetAppIDFromAddress
- GetAppIDFromAddress
ms.assetid: d76a0f36-79c4-4c58-9db3-880b00d11610
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b27ddc4e385aa19d9a760b5cf1a278ddaf1b401d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolproviderdirectgetappidfromaddress"></a>IDebugSymbolProviderDirect::GetAppIDFromAddress
Ruft den Bezeichner der Anwendungsdomäne der Debug-Adresse ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetAppIDFromAddress(  
   IDebugAddress* pAddress,  
   DWORD*         pAppID  
);  
```  
  
```csharp  
int GetAppIDFromAddress(  
   IDebugAddress pAddress,  
   out uint      pAppID  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pAddress`  
 [in] Debuggen Sie die Adresse, die durch dargestellt ist die [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle.  
  
 `pAppID`  
 [out] Der Bezeichner der Anwendungsdomäne.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)