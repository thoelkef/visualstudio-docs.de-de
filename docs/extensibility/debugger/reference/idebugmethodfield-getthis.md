---
title: 'Idebugmethodfield:: GetThis | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727162"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Ruft den `this` ( `Me` in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] )-Zeiger des-Objekts ab, das die-Methode enthält.

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
vorgenommen Gibt ein [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt zurück, das den "This"-Zeiger darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 In objektorientierten Sprachen gibt es in der Regel einen impliziten Zeiger auf die aktuelle Instanziierung einer Klasse. Dies wird `this` in c#/C + + und as in als `Me` bezeichnet [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .

## <a name="see-also"></a>Weitere Informationen
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
