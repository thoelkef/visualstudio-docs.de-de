---
title: IDebugDocumentText2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edc4a209537ca4bd54d3f6d9343d1496ab7c0e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731593"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Ruft die Größe des Textes an dieser Position im Dokument ab.

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
[out] Gibt die Anzahl der Textzeilen zurück.

`pcNumChars`\
[out] Gibt die Anzahl der Zeichen des Textes zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen

 [Nur C++ Wenn ein bestimmter Wert nicht gewünscht ist, übergeben Sie einen NULL für den Parameter.

 [Nur C-Code] Beide Parameter müssen angegeben werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
