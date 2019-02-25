---
title: IDebugSettingsCallback2::GetMetricString | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricString
- GetMetricString
ms.assetid: ecc875a2-8ac6-444c-a839-5191a780fd6b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c92709afbc5341a7507c89dc948daeae1f798b4e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705806"
---
# <a name="idebugsettingscallback2getmetricstring"></a>IDebugSettingsCallback2::GetMetricString
Ruft den Wert der Metrik anhand des Namens ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMetricString(
    LPCWSTR pszType,
    REFGUID guidSection,
    LPCWSTR pszMetric,
    BSTR*   pbstrValue
);
```

```csharp
private int GetMetricString(
    string     pszType,
    ref Guid   guidSection,
    string     pszMetric,
    out string pbstrValue
);
```

#### <a name="parameters"></a>Parameter
 `pszType`

 [in] Der Typ der Metrik.

 `guidSection`

 [in] Eindeutiger Bezeichner des Abschnitts.

 `pszMetric`

 [in] Der Name der Metrik.

 `pbstrValue`

 [out] Gibt die Zeichenfolge den Wert der Metrik zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)