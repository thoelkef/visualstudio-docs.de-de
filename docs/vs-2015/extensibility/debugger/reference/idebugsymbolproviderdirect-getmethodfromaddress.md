---
title: 'Idebugsymbolproviderdirect:: getmethodfromaddress | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 16ba628887f1910738df825a0965959715c5d250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155112"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft Informationen zur Methode an der angegebenen debugadresse ab.  
  
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
 in Debug-Adresse, die durch die [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle dargestellt wird.  
  
 `pGuid`  
 vorgenommen Eindeutiger Bezeichner des Moduls.  
  
 `pAppID`  
 vorgenommen Der Bezeichner der Anwendungsdomäne.  
  
 `pTokenClass`  
 vorgenommen Token, das die enthaltende Klasse darstellt.  
  
 `pTokenMethod`  
 vorgenommen Token, das das Modul darstellt.  
  
 `pdwOffset`  
 vorgenommen Ein Offset in Bytes vom Anfang des- `pAddress` Parameters.  
  
 `pdwVersion`  
 vorgenommen Versionsnummer der Methode.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
