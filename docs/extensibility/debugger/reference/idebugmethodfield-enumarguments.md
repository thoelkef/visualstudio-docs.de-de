---
title: IDebugMethodField::EnumArgumente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: adbb1ea4c9172a5f1cee877d04b81aed938bf7a5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727259"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Erstellt einen Enumerator für den Typ jedes Arguments, das zum Aufrufen der Methode erforderlich ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parameter
`ppParams`\
[out] Gibt ein [IEnumDebugFields-Objekt](../../../extensibility/debugger/reference/ienumdebugfields.md) zurück, das die Liste der Argumenttypen darstellt. Gibt einen NULL-Wert zurück, wenn keine Argumente vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, gibt S_OK oder S_FALSE zurück, wenn keine Argumente vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jedes Element ist ein [IDebugField-Objekt,](../../../extensibility/debugger/reference/idebugfield.md) das die Typen der einzelnen Parameter darstellt. Rufen Sie die [GetInfo-Methode](../../../extensibility/debugger/reference/idebugfield-getinfo.md) auf, um Informationen über den Typ der einzelnen Parameter abzurufen.

 Wenn der Name des Parameters zusammen mit dem Typ benötigt wird, rufen Sie die [EnumParameters-Methode](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
