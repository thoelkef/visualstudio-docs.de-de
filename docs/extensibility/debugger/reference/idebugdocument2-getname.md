---
title: IDebugDocument2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2af7f4dc01ee3a2fe3fb5026602a0b5d4f766b17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731970"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Ruft den Namen des Dokuments in einem von mehreren Formularen ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

## <a name="parameters"></a>Parameter
`gnType`\
[in] Ein Wert [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) aus der GETNAME_TYPE-Enumeration, der den zurückzugebenden Namentyp bestimmt.

`pbstrFileName`\
[out] Gibt eine Zeichenfolge zurück, die den Dokumentnamen enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode kann z. B. den Namen des Dokuments als Titel oder als Dateinamen oder sogar als Teil eines Dateinamens zurückgeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
