---
title: IDebugSymbolProviderDirect::GetCurrentModulesInfo | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetCurrentModulesInfo
- GetCurrentModulesInfo
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4ce4473fca76424f3b737d530997f766da7b219d
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "62421914"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesinfo"></a>IDebugSymbolProviderDirect::GetCurrentModulesInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft Informationen über die Module in der Gruppe "Symbol" ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetCurrentModulesInfo(  
   unsigned long * pCount,  
   GUID *          ppGuids,  
   DWORD *         pADIds,  
   DWORD *         pCurrentState,  
   IUnknown **     ppCDModItfs  
);  
```  
  
```csharp  
int GetCurrentModulesInfo(  
   uint       pCount,  
   Guid       ppGuids,  
   uint       pADIds,  
   uint       pCurrentState,  
   out object ppCDModItfs  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pCount`  
 [in] Anzahl der Module in der `ppGuids` Array.  
  
 `ppGuids`  
 [in] Ein Array, das die eindeutigen Bezeichner für die Module enthält.  
  
 `pADIds`  
 [in] Der Bezeichner für Anwendungsdomänen.  
  
 `pCurrentState`  
 [in] Aktuellen Status der Gruppe "Symbol".  
  
 `ppCDModItfs`  
 [out] Gibt ein Objekt, das die Module in der Gruppe "Symbol" enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
