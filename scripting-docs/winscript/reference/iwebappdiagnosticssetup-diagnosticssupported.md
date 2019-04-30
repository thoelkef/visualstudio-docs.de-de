---
title: IWebAppDiagnosticsSetup::DiagnosticsSupported | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 1d4214dea16c1e8a96ece7428f9ea73640025a9c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443675"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Bestimmt, ob die Diagnose für diese Anwendung unterstützt werden. Wenn [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) für das Objekt, das Implementieren dieser Schnittstelle mit einem Wert ungleich NULL aufgerufen wurde [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) gibt `true`. Wenn nicht der Fall, gibt `false` und Aufrufe von [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) fehl.  
  
> [!IMPORTANT]
> [IWebAppDiagnosticsSetup-Schnittstelle](../../winscript/reference/iwebappdiagnosticssetup-interface.md) wird implementiert von PDM V11. 0 und höher. Im activdbg100 wurde gefunden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 Wenn [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) für das Objekt, das Implementieren dieser Schnittstelle mit einem Wert ungleich NULL aufgerufen wurde [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) gibt `true`. Wenn nicht der Fall, gibt `false`, und Aufrufe von [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) fehl.