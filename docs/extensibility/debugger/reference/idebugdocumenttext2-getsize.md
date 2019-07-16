---
title: IDebugDocumentText2::GetSize | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f382b1d27a83e4493431ac8e6cca3d6aef9dd72
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337374"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Ruft die Größe des Texts an dieser Position im Dokument ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSize( 
   ULONG* pcNumLines,
   ULONG* pcNumChars
);
```

```csharp
int GetSize( 
   ref uint pcNumLines,
   ref uint pcNumChars
);
```

## <a name="parameters"></a>Parameter
`pcNumLines`\
[out] Gibt die Anzahl von Textzeilen.

`pcNumChars`\
[out] Gibt die Anzahl der Zeichen des Texts zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise

 [C++ nur] Wenn ein bestimmter Wert nicht gewünscht ist, übergeben Sie NULL für den Parameter.

 [C# nur] Beide Parameter müssen angegeben werden.

## <a name="see-also"></a>Siehe auch
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)