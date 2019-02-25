---
title: IDebugEngine2::SetLocale | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28eb188ed5b388ac642399630b1891e165d6c9a2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703395"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Legt das Gebietsschema die Debug-Engine (DE) fest.

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

#### <a name="parameters"></a>Parameter
 `wLangID`

 [in] Gibt das Gebietsschema an. Beispiel: 1033 für Englisch.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird aufgerufen, durch die sitzungsbasierter Debug-Manager (SDM), um den gebietsschemaeinstellungen der IDE weiterzugeben, damit, dass durch die DE zurückgegebene Zeichenfolgen ordnungsgemäß lokalisiert werden.

## <a name="see-also"></a>Siehe auch
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)