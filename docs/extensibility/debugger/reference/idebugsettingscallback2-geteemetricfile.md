---
title: IDebugSettingsCallback2::GetEEMetricFile | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricFile
ms.assetid: 3a0bf9e5-bbd2-4d15-840d-8244732787fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e800d8d57d34c0ed99cb3cfa9a3f6a7b871a034d
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458606"
---
# <a name="idebugsettingscallback2geteemetricfile"></a>IDebugSettingsCallback2::GetEEMetricFile
Ruft die Expression Evaluator Metrik Datei erhält den Namen oder die Metrik ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEEMetricFile(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   BSTR*   pbstrValue
);
```

```csharp
private int GetEEMetricFile(
   ref Guid   guidLang,
   ref Guid   guidVendor,
   string     pszMetric,
   out string pbstrValue
);
```

## <a name="parameters"></a>Parameter
 `guidLang`\

 [in] Eindeutiger Bezeichner der Programmiersprache.

 `guidVendor`\

 [in] Eindeutiger Bezeichner des Herstellers.

 `pszMetric`\

 [in] Der Name der Metrik.

 `pbstrValue`\

 [out] Gibt den Inhalt der Datei Metrik als Zeichenfolge zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)