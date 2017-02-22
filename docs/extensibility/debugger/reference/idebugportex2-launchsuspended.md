---
title: "IDebugPortEx2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Startet eine ausführbare Datei.  
  
## Syntax  
  
```cpp#  
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
  
```c#  
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
  
#### Parameter  
 `pszExe`  
 \[in\]  Der Name der ausführbaren Datei ausgeführt werden soll.  Dies kann ein vollständiger Pfad oder relativ zum Arbeitsverzeichnis sein, das im `pszDir`\-Parameter angegeben wird.  
  
 `pszArgs`  
 \[in\]  Die zur ausführbaren Datei zu übergebenden Argumente.  Kann ein NULL\-Wert, wenn keine Argumente vorhanden sind.  
  
 `pszDir`  
 \[in\]  Der Name des Arbeitsverzeichnisses Verwendung durch die ausführbare Datei.  Kann ein NULL\-Wert, wenn kein Arbeitsverzeichnis erforderlich ist.  
  
 `bstrEnv`  
 \[in\]  Umgebungsblock auf NULL endende Zeichenfolge, gefolgt von einem zusätzlichen NULL\-Abschlusszeichen.  
  
 `hStdInput`  
 \[in\]  Handle für einen alternativen Eingabestream.  Kann 0, wenn Umleitungen nicht erforderlich ist.  
  
 `hStdOutput`  
 \[in\]  Handle für einen alternativen Ausgabestream.  Kann 0, wenn Umleitungen nicht erforderlich ist.  
  
 `hStdError`  
 \[in\]  Handle für einen alternativen Fehler ausgabedatenstrom.  Kann 0, wenn Umleitungen nicht erforderlich ist.  
  
 `ppPortProcess`  
 \[out\]  Gibt ein Objekt zurück, das [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) gestarteten Prozess darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode sollte vom Prozess starten, damit sie angehalten wurde und keinen Code ausführt.  Die [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)\-Methode wird aufgerufen, um den Vorgang fortzusetzen.  
  
 Ein Programm kann auch von einem Modul Debuggen gestartet werden.  Ausführlichere Informationen finden Sie unter [Starten eines Programms](../../../extensibility/debugger/launching-a-program.md).  
  
## Siehe auch  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Starten eines Programms](../../../extensibility/debugger/launching-a-program.md)