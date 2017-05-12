---
title: "IWebAppDiagnosticsSetup::DiagnosticsSupported | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup::DiagnosticsSupported"
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsSetup::DiagnosticsSupported
Bestimmt, ob Diagnoseinformationen auf diese Anwendung unterstützt wird.  Wenn [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439), die dem Objekt aufgerufen wurde, das diese Schnittstelle mit einem Wert ungleich null angibt implementiert, gibt [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)`true` zurück.  Wenn nicht, gibt es `false` zurück und ruft auf [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) schlagen fehl.  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup\-Schnittstelle](../../winscript/reference/iwebappdiagnosticssetup-interface.md) wird durch PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.  
  
## Syntax  
  
```cpp  
HRESULT DiagnosticsSupported(  
        [out, retval] VARIANT_BOOL* pRetVal  
        );  
```  
  
#### Parameter  
 `pRetVal`  
 Wenn [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439), die dem Objekt aufgerufen wurde, das diese Schnittstelle mit einem Wert ungleich null angibt implementiert, gibt [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)`true` zurück.  Wenn nicht, gibt es `false` zurück, und ruft auf [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) schlagen fehl.