---
title: IDebugMethodField::GetThis | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b29252d1586d039084ec1d21f1fc4967aea68baf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727162"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Ruft `this` den`Me` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]Zeiger ( in ) des Objekts ab, das die Methode enthält.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parameter
`ppClass`\
[out] Gibt ein [IDebugClassField-Objekt](../../../extensibility/debugger/reference/idebugclassfield.md) zurück, das den "this"-Zeiger darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 In objektorientierten Sprachen gibt es in der Regel einen impliziten Zeiger auf die aktuelle Instanziierung einer Klasse. Dies wird `this` als in C-/C++ und als in `Me` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]bezeichnet.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
