---
title: 'IDebugProcess3:: gethostingprocesslanguage | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::GetHostingProcessLanguage
ms.assetid: 52fca002-a9ef-43b1-9192-afbe7bb59ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b27be0850755a1a2808c8c5c758a3ad59b41d7e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723618"
---
# <a name="idebugprocess3gethostingprocesslanguage"></a>IDebugProcess3::GetHostingProcessLanguage
Diese Methode gibt einen zurück, `GUID` der die Sprache dieses Prozesses darstellt, die durch einen-Befehl von [sethostingprocesslanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)festgelegt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetHostingProcessLanguage(
   GUID* pguidLang
);
```

```csharp
int GetHostingProcessLanguage(
   out Guid pguidLang
);
```

## <a name="parameters"></a>Parameter
`pguidLang`\
vorgenommen Der der `GUID` Sprache dieses Prozesses. `GUID_NULL` (C++) oder `Guid.Empty` (c#) bedeutet, dass die Sprache nicht festgelegt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)
