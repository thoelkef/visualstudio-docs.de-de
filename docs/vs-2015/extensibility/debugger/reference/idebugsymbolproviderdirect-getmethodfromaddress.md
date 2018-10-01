---
title: IDebugSymbolProviderDirect::GetMethodFromAddress | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1d89718dd47db7c0a7e38df284414830477a58b0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509561"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugSymbolProviderDirect::GetMethodFromAddress](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress).  
  
Ruft Informationen über die Methode an der angegebenen Debug-Adresse ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```csharp  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pAddress`  
 [in] Debuggen Sie die Adresse, die durch dargestellt wird die [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle.  
  
 `pGuid`  
 [out] Eindeutiger Bezeichner des Moduls.  
  
 `pAppID`  
 [out] Der Bezeichner der Anwendungsdomäne.  
  
 `pTokenClass`  
 [out] Token, die die enthaltende Klasse darstellt.  
  
 `pTokenMethod`  
 [out] Token, die das Modul darstellt.  
  
 `pdwOffset`  
 [out] Ein Offset in Bytes vom Anfang der `pAddress` Parameter.  
  
 `pdwVersion`  
 [out] Die Versionsnummer der Methode.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)

