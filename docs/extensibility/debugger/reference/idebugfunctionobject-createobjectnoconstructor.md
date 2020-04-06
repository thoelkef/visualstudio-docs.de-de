---
title: IDebugFunctionObject::CreateObjectNoConstructor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad95f9273276830b59ebc77214f3920a687d41ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728574"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
Erstellt ein Objekt ohne Konstruktor.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateObjectNoConstructor( 
   IDebugField*   pClassObject,
   IDebugObject** ppObject
);
```

```csharp
int CreateObjectNoConstructor(
   IDebugField      pClassField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parameter
`pClassObject`\
[in] Ein [IDebugField-Objekt,](../../../extensibility/debugger/reference/idebugfield.md) das den Typ des zu erstellenden Objekts darstellt.

`ppObject`\
[out] Gibt ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) zurück, das das neu erstellte Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das eine Instanz einer Struktur oder eines komplexen Typs darstellt (die keinen Konstruktor erfordert), der ein Parameter für die Funktion ist, die durch die [IDebugFunctionObject-Schnittstelle](../../../extensibility/debugger/reference/idebugfunctionobject.md) dargestellt wird.

 Wenn der Objektparameter einen Konstruktor erfordert, rufen Sie die [CreateObject-Methode](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
