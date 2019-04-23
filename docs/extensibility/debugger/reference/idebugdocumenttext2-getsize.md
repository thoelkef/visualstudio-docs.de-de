---
title: IDebugDocumentText2::GetSize | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f9c46066393a930f6f30208940f0d18b3ed0883
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665573"
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

#### <a name="parameters"></a>Parameter
 `pcNumLines`

 [out] Gibt die Anzahl von Textzeilen.

 `pcNumChars`

 [out] Gibt die Anzahl der Zeichen des Texts zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise

 [C++ nur] Wenn ein bestimmter Wert nicht gewünscht ist, übergeben Sie NULL für den Parameter.

 [C# nur] Beide Parameter müssen angegeben werden.

## <a name="see-also"></a>Siehe auch
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)