---
title: "IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode startet einen Prozess mithilfe des Debugmoduls \(DE\).  
  
## Syntax  
  
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
  
```c#  
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
  
#### Parameter  
 `pszMachine`  
 \[in\]  Der Name des Computers, auf dem der Prozess gestartet werden soll.  Verwenden Sie einen NULL\-Wert, um den lokalen Computer anzugeben.  
  
 `pPort`  
 \[in\]  Die [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)\-Schnittstelle, die den Anschluss darstellt, den das Programm ausgeführt wird.  
  
 `pszExe`  
 \[in\]  Der Name der ausführbaren Datei ausgeführt werden soll.  
  
 `pszArgs`  
 \[in\]  Die zur ausführbaren Datei zu übergebenden Argumente.  Kann ein NULL\-Wert, wenn keine Argumente vorhanden sind.  
  
 `pszDir`  
 \[in\]  Der Name des Arbeitsverzeichnisses Verwendung durch die ausführbare Datei.  Kann ein NULL\-Wert, wenn kein Arbeitsverzeichnis erforderlich ist.  
  
 `bstrEnv`  
 \[in\]  Umgebungsblock auf NULL endende Zeichenfolge, gefolgt von einem zusätzlichen NULL\-Abschlusszeichen.  
  
 `pszOptions`  
 \[in\]  Die Optionen für die ausführbare Datei.  
  
 `dwLaunchFlags`  
 \[in\]  Gibt [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) für eine Sitzung an.  
  
 `hStdInput`  
 \[in\]  Handle für einen alternativen Eingabestream.  Kann 0, wenn Umleitungen nicht erforderlich ist.  
  
 `hStdOutput`  
 \[in\]  Handle für einen alternativen Ausgabestream.  Kann 0, wenn Umleitungen nicht erforderlich ist.  
  
 `hStdError`  
 \[in\]  Handle für einen alternativen Fehler ausgabedatenstrom.  Kann 0, wenn Umleitungen nicht erforderlich ist.  
  
 `pCallback`  
 \[in\]  Das Objekt, das [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Debuggerereignisse empfängt.  
  
 `ppDebugProcess`  
 \[out\]  Gibt das resultierende [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)\-Objekt zurück, das den aufgerufenen Prozess darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Normalerweise startet [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ein Programm mit der [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)\-Methode und fügt dann den Debugger an den angehaltenen Programm an.  Es gibt jedoch Umstände, unter denen das Debugmodul möglicherweise ein Programm starten muss \(beispielsweise, wenn das Debugmodul ist, ist Teil eines Interpreters und des Programms, das gedebuggt wird, eine interpretierte Sprache\). In diesem Fall [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] verwendet die `IDebugEngineLaunch2::LaunchSuspended`\-Methode.  
  
 Die [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)\-Methode wird aufgerufen, um den Prozess gestartet wird, nachdem der Vorgang erfolgreich in einem Ruhezustand gestartet wurde.  
  
## Siehe auch  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)