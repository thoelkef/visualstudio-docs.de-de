---
title: IDebugMethodField::GetThis | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8fc3c4a37b30d2ce7d4f5228b60d6c411afb5c9f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700548"
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

#### <a name="parameters"></a>Parameter
 `ppClass`

 [out] Gibt eine [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Objekt, das die "this"-Zeigers darstellt.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 In objektorientierten Sprachen ist in der Regel ein impliziter Zeiger auf die aktuelle Instanziierung einer Klasse. Dies bezeichnet man als `this` in C#-/ C++ und als `Me` in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].

## <a name="see-also"></a>Siehe auch
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)