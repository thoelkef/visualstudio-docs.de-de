---
title: IDebugDisassemblyStream2::Suchen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4954b3b278b3c7a6b798a4ffda3856ab8bb200c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732081"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Verschiebt den Lesezeiger im Demontagestream um eine bestimmte Anzahl von Anweisungen relativ zu einer angegebenen Position.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

## <a name="parameters"></a>Parameter
`dwSeekStart`\
[in] Ein Wert [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) aus der SEEK_START-Enumeration, der die relative Position angibt, um den Suchprozess zu beginnen.

`pCodeContext`\
[in] Das [IDebugCodeContext2-Objekt,](../../../extensibility/debugger/reference/idebugcodecontext2.md) das den Codekontext darstellt, zu dem der Suchvorgang relativ ist. Dieser Parameter wird `dwSeekStart`  =  `SEEK_START_CODECONTEXT`nur verwendet, wenn ; Andernfalls wird dieser Parameter ignoriert und kann ein NULL-Wert sein.

`uCodeLocationId`\
[in] Der Codepositionsbezeichner, zu dem der Suchvorgang relativ ist. Dieser Parameter wird `dwSeekStart`  =  `SEEK_START_CODELOCID`verwendet, wenn ; Andernfalls wird dieser Parameter ignoriert und kann auf 0 gesetzt werden. Eine Beschreibung eines Codepositionsbezeichners finden Sie im Abschnitt "Hinweise" für die [GetCodeLocationId-Methode.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)

`iInstructions`\
[in] Die Anzahl der Anweisungen, die relativ `dwSeekStart`zu der in angegebenen Position verschoben werden sollen. Dieser Wert kann negativ sein, um rückwärts zu bewegen.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn die Suchposition an einen Punkt lag, der über die Liste der verfügbaren Anweisungen hinausging. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn die Suche an einer Position vor dem Anfang der Liste war, wird die Leseposition auf die erste Anweisung in der Liste festgelegt. Wenn sich die Anzeige nach dem Ende der Liste an einer Position befand, wird die Leseposition auf die letzte Anweisung in der Liste festgelegt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
