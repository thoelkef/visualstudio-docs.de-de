---
title: IDebugEngine2::SetLocale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8616dd827f99dfcfbc337cb5cdf5ac5a7d392e88
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730914"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Legt das Gebietsschema des Debugmoduls (DE) fest.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale( 
   ushort wLangID
);
```

## <a name="parameters"></a>Parameter
`wLangID`\
[in] Gibt das Sprachgebietsschema an. Beispiel: 1033 für Englisch.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird vom Session Debug Manager (SDM) aufgerufen, um die Gebietsschemaeinstellungen der IDE weiterzuleiten, sodass die von der DE zurückgegebenen Zeichenfolgen ordnungsgemäß lokalisiert werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
