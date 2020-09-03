---
title: 'IDebugThread2:: GetName | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d4828b573585969154f2ad1d484c9fcdf767417
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718776"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Ruft den Namen eines Threads ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parameter
`pbstrName`\
vorgenommen Gibt den Namen des Threads zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der abgerufene Name ist immer ein Name, der angezeigt werden kann, und dieser Name beschreibt den Thread. Der Thread Name kann aus einer Lauf Zeit Architektur abgeleitet werden, die benannte Threads unterstützt, oder es kann ein von der Debug-Engine abgeleiteter Name sein. Alternativ kann der Thread Name durch einen Aufrufen der [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) -Methode festgelegt werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
