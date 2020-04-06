---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2bf436d788b517300bee9a13b66b0ca3747bcc43
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724465"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Diese Methode bestimmt, ob der Portlieferant Ports zwischen Aufrufen des Debuggers beibehalten kann (durch Schreiben auf den Datenträger).

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parameter
 Keine.

## <a name="return-value"></a>Rückgabewert
 `S_OK`, wenn Ports beibehalten `S_FALSE` werden können, oder um anzuzeigen, dass Ports nicht beibehalten werden können.

## <a name="remarks"></a>Bemerkungen
 Wenn der Portlieferant Ports beibehalten kann, sollte er dies tun, wenn er zerstört wird, und sie dann erneut laden, wenn er erneut instanziiert wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
