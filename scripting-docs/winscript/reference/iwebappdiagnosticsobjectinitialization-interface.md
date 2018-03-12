---
title: IWebAppDiagnosticsObjectInitialization-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsObjectInitialization Interface
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 159b81a336accea4e4e8c035119d5525de71ae90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticsobjectinitialization-interface"></a>IWebAppDiagnosticsObjectInitialization-Schnittstelle
Diese Schnittstelle implementiert werden kann, auf Klassen, implementieren [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md). [IWebAppDiagnosticsSetup-Schnittstelle](../../winscript/reference/iwebappdiagnosticssetup-interface.md) wird durch das Objekt, das implementiert implementiert [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md). In den meisten Fällen ist dieses Objekt die PDM.  
  
 Nachdem das Objekt erstellt wurde, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) mit einem Verweis auf die PDM-Debug-Anwendung aufgerufen wird und die `hPassToObject` Parameter `CreateObjectWithSiteAtWebApp`.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsObjectInitialization`gefunden in activdbg100.h ist.  
  
## <a name="methods"></a>Methoden  
 Diese Schnittstelle legt die folgenden Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Initialisiert das Objekt.|