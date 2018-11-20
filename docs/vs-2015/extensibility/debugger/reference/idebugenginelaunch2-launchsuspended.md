---
title: IDebugEngineLaunch2::LaunchSuspended | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4ec15be6da5d20fc743c1a2655eb2d67d8247ccc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768369"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode startet einen Prozess mithilfe der Debug-Engine (DE).  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parameter  
 `pszMachine`  
 [in] Der Name des Computers in der zum Starten des Prozesses. Verwenden Sie einen null-Wert, um den lokalen Computer anzugeben.  
  
 `pPort`  
 [in] Die [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Schnittstelle, die den Port, der das Programm, im ausgeführt wird darstellt.  
  
 `pszExe`  
 [in] Der Name des zu startenden ausführbaren Datei an.  
  
 `pszArgs`  
 [in] Die Argumente, die an die ausführbare Datei übergeben werden sollen. Möglicherweise ein null-Wert ab, wenn keine Argumente vorhanden sind.  
  
 `pszDir`  
 [in] Der Name des Arbeitsverzeichnisses durch die ausführbare Datei. Möglicherweise ein null-Wert ab, wenn kein Arbeitsverzeichnis erforderlich ist.  
  
 `bstrEnv`  
 [in] Umgebungsblock mit NULL endende Zeichenfolgen, gefolgt von einer weiteren NULL-Terminator.  
  
 `pszOptions`  
 [in] Die Optionen für die ausführbare Datei.  
  
 `dwLaunchFlags`  
 [in] Gibt an, die [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) für eine Sitzung.  
  
 `hStdInput`  
 [in] Handle für einen anderen Eingabedatenstrom. 0 kann sein, wenn die Umleitung nicht erforderlich ist.  
  
 `hStdOutput`  
 [in] Handle für einen anderen Ausgabestream. 0 kann sein, wenn die Umleitung nicht erforderlich ist.  
  
 `hStdError`  
 [in] Handle für einen anderen Fehlerausgabestream. 0 kann sein, wenn die Umleitung nicht erforderlich ist.  
  
 `pCallback`  
 [in] Die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Objekt, das Debugger-Ereignisse empfängt.  
  
 `ppDebugProcess`  
 [out] Gibt die resultierende [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) -Objekt, das den gestarteten Prozess darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 In der Regel [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] gestartet wird, einem Programm mithilfe der [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) Methode und fügt dann den Debugger an die Anwendung angehalten. Es gibt jedoch Situationen, in dem die Debug-Engine möglicherweise starten ein Programm (z. B., wenn die Debug-Engine ist Teil eines Interpreters und das derzeit debuggte Programm ist eine interpretierte Sprache), in diesem Fall [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] verwendet die `IDebugEngineLaunch2::LaunchSuspended` Methode .  
  
 Die [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) aufgerufen, um den Prozess zu starten, nachdem der Prozess in einem angehaltenen Zustand erfolgreich gestartet wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)

