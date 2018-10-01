---
title: IDebugSymbolProviderDirect::GetMetaDataImport | Microsoft-Dokumentation
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
- GetMetaDataImport
- IDebugSymbolProviderDirect::GetMetaDataImport
ms.assetid: b51a492c-af00-4b08-93fb-6c19ee4916aa
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9ad51ea0f71ed9c9b7d3e0127abf7634125c66a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515766"
---
# <a name="idebugsymbolproviderdirectgetmetadataimport"></a>IDebugSymbolProviderDirect::GetMetaDataImport
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugSymbolProviderDirect::GetMetaDataImport](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport).  
  
Ruft die Informationen zum Importieren der Metadaten ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetMetaDataImport (  
    GUID*      guid,  
    DWORD      appID,  
    IUnknown** ppImport  
);  
```  
  
```csharp  
int GetMetaDataImport (  
    Guid       guid,  
    uint       appID,  
    out object ppImport  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `guid`  
 [in] Eindeutiger Bezeichner für das Modul.  
  
 `appID`  
 [in] Der Bezeichner für die Anwendungsdomäne.  
  
 `ppImport`  
 [out] Gibt ein Objekt, das die Metadaten enthält Informationen zu importieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)

