---
title: "IRemoteDebugApplication::ResumeFromBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.ResumeFromBreakPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::ResumeFromBreakPoint"
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::ResumeFromBreakPoint
Fügt eine Anwendung fort, die derzeit in einem Haltepunkt ist.  
  
## Syntax  
  
```  
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### Parameter  
 `prptFocus`  
 \[in\] für Tretenmodi, der Thread, der durch den Tretenmodus beeinflusst werden soll.  
  
 `bra`  
 \[in\] Die Aktion, nach dem Fortsetzen der Anwendung zu akzeptieren.  
  
 `era`  
 \[in\] Die Aktion, den Fall auszuführende, den die Anwendung aufgrund eines Fehlers beendet wurde.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode wird eine Anwendung fort, die derzeit in einem Haltepunkt ist.  
  
## Siehe auch  
 [IRemoteDebugApplication\-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)   
 [BREAKRESUMEACTION\-Enumeration](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION\-Enumeration](../../winscript/reference/errorresumeaction-enumeration.md)