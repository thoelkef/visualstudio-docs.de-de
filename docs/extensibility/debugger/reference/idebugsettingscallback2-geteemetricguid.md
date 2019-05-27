---
title: IDebugSettingsCallback2::GetEEMetricGuid | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricGuid
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d8829afadbd2f02b9b87f2beb84088aeeb447e66
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212108"
---
# <a name="idebugsettingscallback2geteemetricguid"></a>IDebugSettingsCallback2::GetEEMetricGuid
Ruft den eindeutigen Bezeichner für eine Expression Evaluator-Metrik, die anhand des Namens ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEEMetricGuid(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   GUID*   pguidValue
);
```

```csharp
HRESULT GetEEMetricGuid(
   ref Guid guidLang,
   ref Guid guidVendor,
   string   pszMetric,
   out Guid pguidValue
);
```

## <a name="parameters"></a>Parameter
`guidLang`\
[in] Eindeutiger Bezeichner der Programmiersprache.

`guidVendor`\
[in] Eindeutiger Bezeichner des Herstellers.

`pszMetric`\
[in] Der Name der Metrik.

`pguidValue`\
[out] Gibt den eindeutigen Bezeichner der Metrik zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)