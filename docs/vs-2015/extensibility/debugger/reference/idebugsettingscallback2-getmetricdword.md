---
title: IDebugSettingsCallback2::GetMetricDword | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricDword
ms.assetid: 831a5a1a-c4af-4520-9fdf-3a731aeff85c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af24655561bfd2855f545f42f71b47ed23970662
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155164"
---
# <a name="idebugsettingscallback2getmetricdword"></a>IDebugSettingsCallback2::GetMetricDword
Ruft den Wert einer Metrik anhand des Namens.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMetricDword(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   DWORD*  pdwValue
);
```

```csharp
private int GetMetricDword(
   string   pszType,
   ref Guid guidSection,
   string   pszMetric,
   out uint pdwValue
);
```

#### <a name="parameters"></a>Parameter
 `pszType`

 [in] Der Typ der Metrik.

 `guidSection`

 [in] Eindeutiger Bezeichner des Abschnitts.

 `pszMetric`

 [in] Der Name der Metrik.

 `pdwValue`

 [out] Gibt den Wert der Metrik.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)