---
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f22afc50a1a2874d4853acbf9ff72cae622e790
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114890"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Startet eine ausführbare Datei an.  
  
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
  
#### <a name="parameters"></a>Parameter  
 `pszExe`  
 [in] Der Name der ausführbaren Datei gestartet werden. Dies kann ein vollständiger Pfad oder relativ zum Arbeitsverzeichnis im angegebenen der `pszDir` Parameter.  
  
 `pszArgs`  
 [in] Die Argumente, die an die ausführbare Datei übergeben werden soll. Möglicherweise ein null-Wert, wenn keine Argumente.  
  
 `pszDir`  
 [in] Der Name des Arbeitsverzeichnisses, das durch die ausführbare Datei verwendet werden soll. Möglicherweise ein null-Wert, wenn kein Arbeitsverzeichnis erforderlich ist.  
  
 `bstrEnv`  
 [in] Umgebungsblock mit Null endende Zeichenfolgen, gefolgt von einer zusätzlichen NULL-Terminator.  
  
 `hStdInput`  
 [in] Handle für einen anderen Eingabedatenstrom. Möglicherweise 0, wenn keine Umleitung erforderlich ist.  
  
 `hStdOutput`  
 [in] Handle für einen anderen Ausgabestream. Möglicherweise 0, wenn keine Umleitung erforderlich ist.  
  
 `hStdError`  
 [in] In einen Ausgabestream alternativen Fehler zu behandeln. Möglicherweise 0, wenn keine Umleitung erforderlich ist.  
  
 `ppPortProcess`  
 [out] Gibt eine [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) -Objekt, das die gestarteten Prozess darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode sollte starten Sie den Prozess so, dass die It angehalten wird und keine Ausführung von Code. Die [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) Methode wird aufgerufen, um den Vorgang fortzusetzen.  
  
 Ein Programm kann auch über ein Debugmodul gestartet werden. Weitere Informationen finden Sie unter [Programmstart](../../../extensibility/debugger/launching-a-program.md).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Starten eines Programms](../../../extensibility/debugger/launching-a-program.md)