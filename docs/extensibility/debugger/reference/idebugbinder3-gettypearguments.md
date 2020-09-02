---
title: 'IDebugBinder3:: gettypeer Arguments | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b7667b06348c5e1b2865b24ab49095772808d6c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735698"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
Diese Methode ruft eine Liste von Argument Typen ab, die diesem-Objekt zugeordnet sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetTypeArguments(
   UINT          skip,
   UINT          count,
   IDebugField** ppFields,
   UINT*         pFetched
);
```

```csharp
int GetTypeArguments(
   uint          skip,
   uint          count,
   IDebugField[] ppFields,
   out uint      pFetched
);
```

## <a name="parameters"></a>Parameter
`skip`\
in Anzahl der Felder, die vor dem erhalten von Argument Typen übersprungen werden.

`count`\
in Die Anzahl der zurück zugebende Argument Felder (gibt auch die Größe des `ppFields` Arrays an).

`ppFields`\
[in, out] Ein Array von Feldern, die bei der Rückgabe dieser Methode ausgefüllt werden.

`pFetched`\
[out] \( optional) die Anzahl der Argumenttyp Felder, die tatsächlich zurückgegeben wurden.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Anzahl von Argument Typen kann im Voraus mit [gettyetargumentcount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)abgerufen werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)
