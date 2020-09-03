---
title: 'IDebugDefaultPort2:: queryislocal | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c06230f7bbd1825fe73a22f9b1fdc35aea35c499
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732328"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
Diese Methode bestimmt, ob sich dieser Port auf dem lokalen Computer befindet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Rückgabewert
 Gibt zurück, `S_OK` Wenn es sich um einen lokalen Port handelt (auf demselben Computer wie der Aufrufer) oder `S_FALSE` Wenn sich der Port auf einem anderen Computer befindet.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
