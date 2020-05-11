---
title: IDebugPortSupplier2::CanAddPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5d0c67d62f57076f29f2c2ef60d456f517ae97fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724749"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Überprüft, ob ein Portlieferant neue Ports hinzufügen kann.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Rückgabewert
 Wenn der Port hinzugefügt `S_OK`werden kann, kehrt zurück; Andernfalls können `S_FALSE` diesem Portlieferanten keine Ports hinzugefügt werden, um anzuzeigen.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie diese Methode auf, bevor Sie die [AddPort-Methode](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) aufrufen, da die letztgenannte Methode den Port erstellt und hinzufügt, was ein zeitaufwändiger Vorgang sein könnte.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
