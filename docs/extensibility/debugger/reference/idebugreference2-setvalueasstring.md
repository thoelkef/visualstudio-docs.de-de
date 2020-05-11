---
title: IDebugReference2::SetValueasString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsString
helpviewer_keywords:
- IDebugReference2::SetValueAsString
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c8414ce5f53acec2a30ff681ff0bab8ddc919310
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720292"
---
# <a name="idebugreference2setvalueasstring"></a>IDebugReference2::SetValueAsString
Legt den Wert eines Verweises aus einer Zeichenfolge fest. Für die zukünftige Verwendung reserviert.

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

## <a name="parameters"></a>Parameter
`pszValue`\
[in] Der Wert als Zeichenfolge.

`dwRadix`\
[in] Der Radix, der zum Formatieren numerischer Informationen verwendet werden soll.

`dwTimeout`\
[in] Maximale Wartezeit in Millisekunden, bevor von dieser Methode zurückgegeben wird. Verwenden `INFINITE` Sie diese Verwendung, um auf unbestimmte Zeit zu warten.

## <a name="return-value"></a>Rückgabewert
 Gibt immer `E_NOTIMPL` zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
