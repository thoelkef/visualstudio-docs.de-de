---
title: "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp"
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Diese Methode erstellt die Klasse gemeinsam mit der ID Sie in mit `rclsid` mithilfe `dwClsContext` übergeben.  Dies ist vergleichbar, die [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) bearbeitet, außer dass im `CreateObjectWithSiteAtWebApp` wird das Objekt asynchron im UI\-Thread der Webanwendung erstellt.  Das Objekt, das durch die Klassen\-ID angegeben wird, sollte [IWebAppDiagnosticsObjectInitialization\-Schnittstelle](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md) implementieren.  Nachdem das Objekt erstellt wurde, wird [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) mit einem Verweis auf die Anwendung PDM Debug\- und dem `hPassToObject`\-Parameter von `CreateObjectWithSiteAtWebApp` bezeichnet.  Sie können diese Methode verwenden, um in die Anwendung ein Handle für führen zu einer anonymen Pipe, deren Sie mit [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450) kopiert haben.  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup\-Schnittstelle](../../winscript/reference/iwebappdiagnosticssetup-interface.md) wird durch PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Syntax  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(  
        [in] REFCLSID rclsid,   
        [in] DWORD dwClsContext,   
        [in] REFIID riid,   
        [in] DWORD_PTR hPassToObject  
        );  
  
```  
  
#### Parameter  
 `rclsid`  
 Die Klassen\-ID der Klasse zu erstellen.  
  
 `dwClsContext`  
 Der Kontext, in dem der Code ausgeführt wird.  In den meisten Fällen ist es CLSCTX\_INPROC\_SERVER.  
  
 `riid`  
 Wird nicht verwendet.  
  
 `hPassToObject`  
 Ein Wert, der dem Objekt einmal übergeben wird, wird im UI\-Thread erstellt, wenn das Objekt [IWebAppDiagnosticsObjectInitialization\-Schnittstelle](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md) implementiert.