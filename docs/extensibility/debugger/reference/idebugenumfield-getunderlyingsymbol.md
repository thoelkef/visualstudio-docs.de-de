---
title: 'Idebugenenfield:: getunderlyingsymbol | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 14cac9d3f761e95b821179137f2efc23ef61b91b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730273"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
Diese Methode gibt ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) zurück, das den Namen der Enumeration darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetUnderlyingSymbol(
   IDebugField** ppField
);
```

```csharp
int GetUnderlyingSymbol(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parameter
`ppField`\
vorgenommen Gibt das [idebugfeld](../../../extensibility/debugger/reference/idebugfield.md) zurück, das den Namen dieser Enumeration beschreibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Name der-Enumeration enthält auch den Typ der-Enumeration, der mithilfe von [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)an eine Speicheradresse gebunden wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Zwick](../../../extensibility/debugger/reference/idebugbinder-bind.md)
