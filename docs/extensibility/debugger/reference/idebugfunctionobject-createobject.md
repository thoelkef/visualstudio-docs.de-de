---
title: IDebugFunctionObject::CreateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: beb00bcf932b19ed4e489456236957c55d909ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728599"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Erstellt ein Objekt mit einem Konstruktor.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>Parameter
`pConstructor`\
[in] Ein [IDebugFunctionObject-Objekt,](../../../extensibility/debugger/reference/idebugfunctionobject.md) das den Konstruktor des zu erstellenden Objekts darstellt.

`dwArgs`\
[in] Die Anzahl der `pArg` Parameter im Array. Stellt die Anzahl der Parameter dar, die an den Konstruktor übergeben werden.

`pArg`\
[in] Ein Array von [IDebugObject-Objekten,](../../../extensibility/debugger/reference/idebugobject.md) die die an den Konstruktor übergebenen Parameter darstellen.

`ppObject`\
[out] Gibt `IDebugObject` eine Darstellung des neu erstellten Objekts zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das eine Instanz einer Klasse (oder eines anderen komplexen Typs, der einen Konstruktor erfordert) darstellt, der ein Parameter für die Funktion ist, die durch die [IDebugFunctionObject-Schnittstelle](../../../extensibility/debugger/reference/idebugfunctionobject.md) dargestellt wird.

 Wenn für den Objektparameter kein Konstruktor erforderlich ist, rufen Sie die [CreateObjectNoConstructor-Methode](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
