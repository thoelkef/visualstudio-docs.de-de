---
title: 'IDebugProcess3:: Einstellungs Sprache | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a16f2c39fa2d53ffc4d113666ef7630557e61861
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723567"
---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
Mit dieser Methode wird die Sprache festgelegt, unter der der Prozess gehostet wird. Diese Sprache kann dann von der Debug-Engine (de) zum Laden der entsprechenden Ausdrucks Auswertung verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetHostingProcessLanguage(
   REFGUID guidLang
);
```

```csharp
int SetHostingProcessLanguage(
   ref Guid guidLang
);
```

## <a name="parameters"></a>Parameter
`guidLang`\
[in] `GUID` der Sprache, die von der de verwendet werden soll. Geben `GUID_NULL` Sie (C++) oder `Guid.Empty` (c#) an, damit der de die Standardsprache verwendet.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
- [Gethostingprocesslanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) kann verwendet werden, um die aktuelle Spracheinstellung abzurufen.

## <a name="see-also"></a>Siehe auch
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)
