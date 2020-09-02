---
title: 'IDebugBinder3:: findalias | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a697e39d21b1c25a98c09ad6cc4837cca7a293
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735864"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Diese Methode gibt einen Alias an, wenn ein Name angegeben ist. Dadurch werden alle Aliase im Programm durchsucht.

## <a name="syntax"></a>Syntax

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parameter
`pcstrName`\
in Der Name des zu suchenden Alias.

`ppAlias`\
vorgenommen Alias gefunden (sofern vorhanden), der durch die [idebugalias](../../../extensibility/debugger/reference/idebugalias.md) -Schnittstelle dargestellt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben `S_FALSE` (wenn Alias nicht gefunden wurde), oder es wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode initialisiert das Zielobjekt auf NULL, bevor aufgerufen wird. danach testet er auf einen NULL-Wert, um zu bestimmen, ob der Alias gefunden wurde.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
