---
title: "IWebAppDiagnosticsObjectInitialization-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsObjectInitialization-Schnittstelle"
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsObjectInitialization-Schnittstelle
Diese Schnittstelle kann für Klassen implementiert werden, die [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) implementieren.  [IWebAppDiagnosticsSetup\-Schnittstelle](../../winscript/reference/iwebappdiagnosticssetup-interface.md) wird durch das Objekt implementiert, das [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md) implementiert.  In den meisten Fällen ist dies das Objekt PDM.  
  
 Nachdem das Objekt erstellt wurde, wird [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) mit einem Verweis auf die Anwendung PDM Debug\- und dem `hPassToObject`\-Parameter von `CreateObjectWithSiteAtWebApp` bezeichnet.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsObjectInitialization` wird in activdbg100.h. gefunden.  
  
## Methoden  
 Diese Schnittstelle macht die folgenden Methoden verfügbar.  
  
|Methode|Description|  
|-------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Initialisiert das Objekt.|