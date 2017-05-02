---
title: "IActiveScriptProfilerCallback::Initialize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Initialize
apilocation: scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptProfilerCallback::Initialize
Wird aufgerufen, um das Profilerobjekt zu initialisieren, wenn ein Profil erstellen auf einem Skriptmodul gestartet wird.  
  
## Syntax  
  
```  
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### Parameter  
 `dwContext`  
 \[in\] Ein 4\-Byte\-Wert, der zu [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md) übergeben wird.  
  
## Rückgabewert  
 Gibt ein HRESULT zurück.  Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Wenn die Methode das Profilerobjekt nicht initialisieren kann, sollte sie ein Fehler\-HRESULT zurückgeben, um das Skriptmodul zu benachrichtigen.  In diesem Fall sollte das Skriptmodul [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) direkt aufrufen und das HRESULT im Parameter übergeben, und gibt dann das Profilerobjekt frei.  
  
## Siehe auch  
 [IActiveScriptProfilerCallback\-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)