---
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28ff6065bbe83852b5acc3ffe253a0bdabcc67ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725100"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Startet eine ausführbare Datei.

## <a name="syntax"></a>Syntax

```cpp
HRESULT LaunchSuspended( 
   LPCOLESTR        pszExe,
   LPCOLESTR        pszArgs,
   LPCOLESTR        pszDir,
   BSTR             bstrEnv,
   DWORD            hStdInput,
   DWORD            hStdOutput,
   DWORD            hStdError,
   IDebugProcess2** ppPortProcess
);
```

```csharp
int LaunchSuspended( 
   string             pszExe,
   string             pszArgs,
   string             pszDir,
   string             bstrEnv,
   uint               hStdInput,
   uint               hStdOutput,
   uint               hStdError,
   out IDebugProcess2 ppPortProcess
);
```

## <a name="parameters"></a>Parameter
`pszExe`\
[in] Der Name der ausführbaren Datei, die gestartet werden soll. Dies kann ein vollständiger Pfad oder relativ `pszDir` zum im Parameter angegebenen Arbeitsverzeichnis sein.

`pszArgs`\
[in] Die Argumente, die an die ausführbare Datei übergeben werden sollen. Kann ein Nullwert sein, wenn keine Argumente vorhanden sind.

`pszDir`\
[in] Der Name des Arbeitsverzeichnisses, das von der ausführbaren Datei verwendet wird. Kann ein NULL-Wert sein, wenn kein Arbeitsverzeichnis erforderlich ist.

`bstrEnv`\
[in] Umgebungsblock von null-terminierten Zeichenfolgen, gefolgt von einem zusätzlichen NULL-Terminator.

`hStdInput`\
[in] Handle zu einem alternativen Eingabestream. Kann 0 sein, wenn keine Umleitung erforderlich ist.

`hStdOutput`\
[in] Handle zu einem alternativen Ausgabestream. Kann 0 sein, wenn keine Umleitung erforderlich ist.

`hStdError`\
[in] Behandeln Sie einen alternativen Fehlerausgabestream. Kann 0 sein, wenn keine Umleitung erforderlich ist.

`ppPortProcess`\
[out] Gibt ein [IDebugPendingBreakpoint2-Objekt](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) zurück, das den gestarteten Prozess darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode sollte den Prozess starten, damit er angehalten wird und kein Code ausgeführt wird. Die [ResumeProcess-Methode](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) wird aufgerufen, um den Prozess fortzusetzen.

 Ein Programm kann auch von einem Debugmodul gestartet werden. Weitere Informationen finden Sie unter [Starten eines Programms](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Starten eines Programms](../../../extensibility/debugger/launching-a-program.md)
