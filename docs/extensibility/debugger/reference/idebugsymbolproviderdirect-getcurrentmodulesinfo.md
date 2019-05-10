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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1225729ceb6d1a874f4ca5bedef287ababbdb962
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457441"
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

## <a name="parameters"></a>Parameter
 `pCount`\

 [in] Anzahl der Module in der `ppGuids` Array.

 `ppGuids`\

 [in] Ein Array, das die eindeutigen Bezeichner für die Module enthält.

 `pADIds`\

 [in] Der Bezeichner für Anwendungsdomänen.

 `pCurrentState`\

 [in] Aktuellen Status der Gruppe "Symbol".

 `ppCDModItfs`\

 [out] Gibt ein Objekt, das die Module in der Gruppe "Symbol" enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)