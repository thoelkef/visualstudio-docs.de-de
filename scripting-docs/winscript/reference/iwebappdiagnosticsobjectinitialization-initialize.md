---
title: "IWebAppDiagnosticsObjectInitialization::Initialize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsObjectInitialization::Initialize"
ms.assetid: 7ccfac28-9f65-4e1c-a0fb-a8a6c7f75b63
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IWebAppDiagnosticsObjectInitialization::Initialize
Initialisiert die Objekte, die mit [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) erstellt werden.  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsObjectInitialization\-Schnittstelle](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md) wird in activdbg100.h. gefunden.  
  
## Syntax  
  
```cpp  
HRESULT Initialize(  
        [in, annotation("__in")] HANDLE_PTR hPassedHandle,  
        [in, annotation("__in")] IUnknown* pDebugApplication  
        );  
```  
  
#### Parameter  
 `hPassedHandle`  
 Das Handle, das der [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)\-Methode im `hPassToObject`\-Parameter übergeben wurde.  
  
 `pDebugApplication`  
 Die PDM\-Anwendung, mit der das Objekt erstellt wurde.