---
title: 'IDebugBinder3:: getexceptionobjectandtype | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e25a0f7b4e1713a072359f1efdd962f36c50b774
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735754"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Diese Methode ruft die Ausnahme ab, die einem Objekt zugeordnet ist, sofern vorhanden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetExceptionObjectAndType(
   IDebugObject** ppException,
   IDebugField**  ppField
);
```

```csharp
int GetExceptionObjectAndType(
   out IDebugObject ppException,
   out IDebugField  ppField
);
```

## <a name="parameters"></a>Parameter
`ppException`\
vorgenommen Gibt das-Objekt zurück, das die Ausnahme darstellt.

`ppField`\
vorgenommen Gibt das-Objekt zurück, das ein bestimmtes Feld darstellt, das möglicherweise die Ausnahme verursacht hat (Dies kann ein NULL-Wert sein).

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

> [!NOTE]
> Um zu überprüfen, ob eine Ausnahme vorliegt, überprüfen Sie den von zurückgegebenen Wert `ppException` : Wenn es sich um einen NULL-Wert handelt, wird diesem-Objekt keine Ausnahme zugeordnet.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
