---
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45916edbef4368c58f83426d6c73f3c692236cb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722435"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Gibt die GUIDs für alle möglichen Debug-Engines (DE) zurück, die dieses Programm debuggen können.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumPossibleEngines( 
   DWORD  celtBuffer,
   GUID*  rgguidEngines,
   DWORD* pceltEngines
);
```

```csharp
int EnumPossibleEngines( 
   uint      celtBuffer,
   GUID[]    rgguidEngines,
   ref DWORD pceltEngines
);
```

## <a name="parameters"></a>Parameter
`celtBuffer`\
[in] Die Anzahl der zurückzurückzugebenden DE-GUIDs. Dadurch wird auch die maximale `rgguidEngines` Größe des Arrays angegeben.

`rgguidEngines`\
[in, out] Ein Array von DE-GUIDs, die ausgefüllt werden sollen.

`pceltEngines`\
[out] Gibt die tatsächliche Anzahl der zurückgegebenen DE-GUIDs zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` oder [C'] 0x8007007A zurück, wenn der Puffer nicht groß genug ist.

## <a name="remarks"></a>Bemerkungen
 Um zu bestimmen, wie viele Module vorhanden sind, rufen Sie diese Methode einmal auf, wobei der `celtBuffer` Parameter auf 0 und der `rgguidEngines` Parameter auf einen Nullwert festgelegt ist. Dadurch `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` wird die erforderliche Größe des Puffers zurückgegeben (0x8007007A für C-Code), und der `pceltEngines` Parameter gibt die erforderliche Größe des Puffers zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
