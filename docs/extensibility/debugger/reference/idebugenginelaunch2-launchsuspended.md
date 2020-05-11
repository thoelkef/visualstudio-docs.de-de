---
title: IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e802c17d0a93aabbe5c6c0a8573abc6a551944ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730546"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Diese Methode startet einen Prozess über das Debug-Modul (DE).

## <a name="syntax"></a>Syntax

```cpp
HRESULT LaunchSuspended ( 
   LPCOLESTR             pszMachine,
   IDebugPort2*          pPort,
   LPCOLESTR             pszExe,
   LPCOLESTR             pszArgs,
   LPCOLESTR             pszDir,
   BSTR                  bstrEnv,
   LPCOLESTR             pszOptions,
   LAUNCH_FLAGS          dwLaunchFlags,
   DWORD                 hStdInput,
   DWORD                 hStdOutput,
   DWORD                 hStdError,
   IDebugEventCallback2* pCallback,
   IDebugProcess2**      ppDebugProcess
);
```

```csharp
int LaunchSuspended(
   string               pszServer,
   IDebugPort2          pPort,
   string               pszExe,
   string               pszArgs,
   string               pszDir,
   string               bstrEnv,
   string               pszOptions,
   enum_LAUNCH_FLAGS    dwLaunchFlags,
   uint                 hStdInput,
   uint                 hStdOutput,
   uint                 hStdError,
   IDebugEventCallback2 pCallback,
   out IDebugProcess2   ppProcess
);
```

## <a name="parameters"></a>Parameter
`pszMachine`\
[in] Der Name des Computers, auf dem der Prozess gestartet werden soll. Verwenden Sie einen NULL-Wert, um den lokalen Computer anzugeben.

`pPort`\
[in] Die [IDebugPort2-Schnittstelle,](../../../extensibility/debugger/reference/idebugport2.md) die den Port darstellt, in dem das Programm ausgeführt wird.

`pszExe`\
[in] Der Name der ausführbaren Datei, die gestartet werden soll.

`pszArgs`\
[in] Die Argumente, die an die ausführbare Datei übergeben werden sollen. Kann ein Nullwert sein, wenn keine Argumente vorhanden sind.

`pszDir`\
[in] Der Name des Arbeitsverzeichnisses, das von der ausführbaren Datei verwendet wird. Kann ein NULL-Wert sein, wenn kein Arbeitsverzeichnis erforderlich ist.

`bstrEnv`\
[in] Umgebungsblock von NULL-beendeten Zeichenfolgen, gefolgt von einem zusätzlichen NULL-Terminator.

`pszOptions`\
[in] Die Optionen für die ausführbare Datei.

`dwLaunchFlags`\
[in] Gibt die [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) für eine Sitzung an.

`hStdInput`\
[in] Handle zu einem alternativen Eingabestream. Kann 0 sein, wenn keine Umleitung erforderlich ist.

`hStdOutput`\
[in] Handle zu einem alternativen Ausgabestream. Kann 0 sein, wenn keine Umleitung erforderlich ist.

`hStdError`\
[in] Behandeln Sie einen alternativen Fehlerausgabestream. Kann 0 sein, wenn keine Umleitung erforderlich ist.

`pCallback`\
[in] Das [IDebugEventCallback2-Objekt,](../../../extensibility/debugger/reference/idebugeventcallback2.md) das Debuggerereignisse empfängt.

`ppDebugProcess`\
[out] Gibt das resultierende [IDebugProcess2-Objekt](../../../extensibility/debugger/reference/idebugprocess2.md) zurück, das den gestarteten Prozess darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Normalerweise [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] startet ein Programm mit der [LaunchSuspended-Methode](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) und fügt dann den Debugger an das angehaltene Programm an. Es gibt jedoch Umstände, unter denen das Debugmodul möglicherweise ein Programm starten muss (z. B. wenn das Debugmodul Teil [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] eines `IDebugEngineLaunch2::LaunchSuspended` Interpreters ist und das zu debuggende Programm eine interpretierte Sprache ist), in diesem Fall wird die Methode verwendet.

 Die [ResumeProcess-Methode](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) wird aufgerufen, um den Prozess zu starten, nachdem der Prozess erfolgreich in einem angehaltenen Zustand gestartet wurde.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
