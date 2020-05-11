---
title: IDebugProgram3::ExecuteonThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 201c08352bc5b616298349c52197529ef3f1a7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722658"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Führt das Debuggerprogramm aus. Der Thread wird zurückgegeben, um den Debuggerinformationen darüber zu geben, welchen Thread der Benutzer beim Ausführen des Programms anzeigt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parameter
`pThread`\
[in] Ein [IDebugThread2-Objekt.](../../../extensibility/debugger/reference/idebugthread2.md)

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Es gibt drei verschiedene Möglichkeiten, wie ein Debugger die Ausführung nach dem Beenden fortsetzen kann:

- Ausführen: Brechen Sie einen vorherigen Schritt ab, und führen Sie bis zum nächsten Haltepunkt usw. aus.

- Schritt: Brechen Sie jeden alten Schritt ab, und führen Sie aus, bis der neue Schritt abgeschlossen ist.

- Weiter: Führen Sie erneut, und lassen Sie jeden alten Schritt aktiv.

  Der übergebene `ExecuteOnThread` Thread ist nützlich, wenn Sie entscheiden, welcher Schritt abgebrochen werden soll. Wenn Sie den Thread nicht kennen, bricht die Ausführung der Ausführung alle Schritte ab. Wenn Sie den Thread kennen, müssen Sie nur den Schritt im aktiven Thread abbrechen.

## <a name="see-also"></a>Weitere Informationen
- [Ausführen](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
