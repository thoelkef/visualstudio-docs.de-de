---
title: 'IDebugProperty2:: setvalueasstring | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 112ded163f38b93e9918387d8ca6beafb8282647
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721239"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Legt den Wert einer Eigenschaft aus einer angegebenen Zeichenfolge fest.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>Parameter
`pszValue`\
in Eine Zeichenfolge, die den festzulegenden Wert enthält.

`nRadix`\
in Ein Basis, das zum Interpretieren numerischer Informationen verwendet werden soll. Dies kann 0 sein, um zu versuchen, das Basis automatisch zu ermitteln.

`dwTimeout`\
in Gibt die maximale Zeit in Millisekunden an, die gewartet werden soll, bevor diese Methode zurückgegeben wird. Verwenden `INFINITE` Sie, um unbegrenzt zu warten.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben. In der folgenden Tabelle werden andere mögliche Werte angezeigt.

|value|BESCHREIBUNG|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Die Zeichenfolge konnte nicht in einen Eigenschafts Wert konvertiert werden, oder der Eigenschafts Wert konnte nicht festgelegt werden.|
|`E_SETVALUE_VALUE_IS_READONLY`|Die Eigenschaft ist schreibgeschützt.|

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
