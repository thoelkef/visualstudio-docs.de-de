---
title: 'IDebugBinder3:: gettypeer Arguments | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f7b6038013370ad85a665d9899d367e621aa991
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192281"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]
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

#### <a name="parameters"></a>Parameter

 `skip`

 in Anzahl der Felder, die vor dem erhalten von Argument Typen übersprungen werden.

 `count`

 in Die Anzahl der zurück zugebende Argument Felder (gibt auch die Größe des `ppFields` Arrays an).

 `ppFields`

 [in, out] Ein Array von Feldern, die bei der Rückgabe dieser Methode ausgefüllt werden.

 `pFetched`

 vorgenommen Die Anzahl der Argumenttyp Felder, die tatsächlich zurückgegeben werden (optional).

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Anzahl von Argument Typen kann im Voraus mit [gettyetargumentcount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)abgerufen werden.

## <a name="see-also"></a>Weitere Informationen

- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)