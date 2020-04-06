---
title: IDebugthread2::SetNextStatement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b390e5c021fa069ae3fb09eef1978caaf9cc8ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718649"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Legt den aktuellen Anweisungszeiger auf den angegebenen Codekontext fest.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int SetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>Parameter
`pStackFrame`\
Reserviert für die zukünftige Verwendung; auf einen NULL-Wert festgelegt.

`pCodeContext`\
[in] Ein [IDebugCodeContext2-Objekt,](../../../extensibility/debugger/reference/idebugcodecontext2.md) das den auszuführenden Codespeicherort und seinen Kontext beschreibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt andere mögliche Werte.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Die nächste Anweisung kann sich nicht tiefer in einem Stapelrahmen auf dem Frame-Stack befinden.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Die nächste Anweisung ist keinem Frame im Stapel zugeordnet.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Einige Debugmodule können die nächste Anweisung nicht nach einer Ausnahme festlegen.|

## <a name="remarks"></a>Bemerkungen
 Der Anweisungszeiger gibt die nächste auszuführende Anweisung oder Anweisung an. Diese Methode wird verwendet, um eine Quellcodezeile erneut auszuprobieren oder die Ausführung z. B. in einer anderen Funktion fortzusetzen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
