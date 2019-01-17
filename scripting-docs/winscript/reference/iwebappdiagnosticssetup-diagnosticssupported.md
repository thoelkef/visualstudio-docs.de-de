---
title: IWebAppDiagnosticsSetup::DiagnosticsSupported | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df9296ac251d93105229fc0af365f6797a413f2b
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349685"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Bestimmt, ob die Diagnose für diese Anwendung unterstützt werden. Wenn [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) für das Objekt, das Implementieren dieser Schnittstelle mit einem Wert ungleich NULL aufgerufen wurde [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) gibt `true`. Wenn nicht der Fall, gibt `false` und Aufrufe von [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) fehl.  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup-Schnittstelle](../../winscript/reference/iwebappdiagnosticssetup-interface.md) wird implementiert von PDM V11. 0 und höher. Im activdbg100 wurde gefunden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 Wenn [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) für das Objekt, das Implementieren dieser Schnittstelle mit einem Wert ungleich NULL aufgerufen wurde [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) gibt `true`. Wenn nicht der Fall, gibt `false`, und Aufrufe von [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) fehl.