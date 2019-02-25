---
title: IDebugSettingsCallback2::EnumEEs | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05d64a568f4df1e4e1705e90ba186287c0b96a85
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708211"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
Listet die verfügbaren ausdrucksauswertungen die Sprache und den Anbieter-IDs angegeben.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumEEs(
   DWORD  celtBuffer,
   GUID*  rgguidLang,
   GUID*  rgguidVendor,
   DWORD* pceltEEs
);
```

```csharp
public int EnumEEs(
   uint       celtBuffer,
   ref Guid   rgguidLang,
   ref Guid   rgguidVendor,
   ref uint[] pceltEEs
);
```

#### <a name="parameters"></a>Parameter
 `celtBuffer`

 [in] Anzahl der Elemente in der `pceltEEs` Puffer.

 `rgguidLang`

 [in, out] Eindeutiger Bezeichner für die Programmiersprache.

 `rgguidVendor`

 [in, out] Eindeutiger Bezeichner für den Anbieter.

 `pceltEEs`

 [in, out] Array von der ausdrucksauswertung.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)