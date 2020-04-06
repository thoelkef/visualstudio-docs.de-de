---
title: IDebugCustomAttribute::GetAttributeBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 621ebf3949a273e06053ced67209aa052c25bce0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732797"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Ruft die Attributinformationen als Bytes-Blob ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAttributeBytes( 
   BYTE*  ppBlob,
   DWORD* pdwLen
);
```

```csharp
int GetAttributeBytes(
   ref byte[] ppBlob,
   ref uint   pdwLen
);
```

## <a name="parameters"></a>Parameter
`ppBlob`\
[in, out] Ein Array, das mit den Attributbytes ausgefüllt wird.

`pdwLen`\
[in, out] Gibt die maximale Anzahl von Bytes `ppBlob` an, die im Array zurückgegeben werden sollen, und gibt die Anzahl der Bytes zurück, die tatsächlich in das Array geschrieben wurden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Legen `ppBlob` Sie den Parameter auf einen Nullwert fest, um die Anzahl der verfügbaren Attribute bytes zurückzugeben. Weisen Sie dann ein Array zu, und übergeben Sie dieses Array für den `ppBlob` Parameter.

 Die Attributbytes stellen die Rohdaten des benutzerdefinierten Attributs dar.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
