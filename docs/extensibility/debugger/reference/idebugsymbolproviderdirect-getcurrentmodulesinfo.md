---
title: IDebugSymbolProviderDirect::GetCurrentModulesInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetCurrentModulesInfo
- GetCurrentModulesInfo
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95dc42b0e65ad0f849dd95e0ffead122e4cd1ebf
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699547"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesinfo"></a>IDebugSymbolProviderDirect::GetCurrentModulesInfo
Ruft Informationen über die Module in der Gruppe "Symbol" ab.

## <a name="syntax"></a>Syntax

```cpp
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
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)