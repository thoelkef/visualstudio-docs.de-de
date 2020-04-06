---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d529bb80f79a3f2972e9349a2679bb528cc10463
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732913"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Aktiviert das automatische Anfügen für die angegebenen Debugmodule.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Parameter
`rgguidSpecificEngines`\
[in] Array von GUIDs für jedes Debugmodul, das als automatische anfügend markiert werden soll.

`celtSpecificEngines`\
[in] Die Anzahl der `rgguidSpecificEngines`in angegebenen Motoren.

`pszStartPageUrl`\
[in] Die Start-URL, die beim automatischen Anfügen verwendet werden soll.

`pbstrSessionID`\
[out] ID der Sitzung, die automatisch angefügt wurde.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben. Ein Fehlercode `E_AUTO_ATTACH_NOT_REGISTERED`ist , was darauf hinweist, dass die Factory der Auto-Attach-Klasse nicht registriert wurde.

## <a name="remarks"></a>Bemerkungen
 Wenn ein Programm gestartet wird, das der angegebenen URL zugeordnet ist, werden die angegebenen Debugmodule automatisch gestartet und angefügt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
