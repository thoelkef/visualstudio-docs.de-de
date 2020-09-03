---
title: 'IDebugMemoryContext2:: GetName | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetName
helpviewer_keywords:
- IDebugMemoryContext2::GetName method
- GetName method
ms.assetid: 8c212556-7d9e-4d68-b2a9-8212f50d0287
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b8a13c078340eafcff9440e41afd468ba95f9849
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727455"
---
# <a name="idebugmemorycontext2getname"></a>IDebugMemoryContext2::GetName
Ruft den vom Benutzer anzeigbaren Namen für diesen Kontext ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parameter
`pbstrName`\
vorgenommen Gibt den Namen des Speicher Kontexts zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Name eines Speicher Kontexts wird normalerweise nicht verwendet.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
