---
title: IDebugReference2::SetValueAsString | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsString
helpviewer_keywords:
- IDebugReference2::SetValueAsString
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 67e3ac6bda70a25baf7546c709849c650372c649
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869017"
---
# <a name="idebugreference2setvalueasstring"></a>IDebugReference2::SetValueAsString
Legt den Wert, der einen Verweis aus einer Zeichenfolge. Für zukünftige Verwendung reserviert.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   DWORD     dwRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   dwRadix,
   uint   dwTimeout
);
```

#### <a name="parameters"></a>Parameter
 `pszValue`

 [in] Der Wert als Zeichenfolge.

 `dwRadix`

 [in] Die Basis bei der Formatierung von numerischen Informationen verwendet werden.

 `dwTimeout`

 [in] Maximale Zeit in Millisekunden, die vor der Rückgabe dieser Methode gewartet. Verwendung `INFINITE` für Warten ohne Timeout.

## <a name="return-value"></a>Rückgabewert
 Gibt immer `E_NOTIMPL` zurück.

## <a name="see-also"></a>Siehe auch
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)