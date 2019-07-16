---
title: IDebugMethodField::GetThis | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 426fc0c74b44b1f137752814f9b6aaeff150baa8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324065"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Ruft die `this` (`Me` in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]) Zeiger, der das Objekt, das die Methode enthält.

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
[out] Gibt eine [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Objekt, das die "this"-Zeigers darstellt.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 In objektorientierten Sprachen ist in der Regel ein impliziter Zeiger auf die aktuelle Instanziierung einer Klasse. Dies bezeichnet man als `this` in C#-/ C++ und als `Me` in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].

## <a name="see-also"></a>Siehe auch
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)