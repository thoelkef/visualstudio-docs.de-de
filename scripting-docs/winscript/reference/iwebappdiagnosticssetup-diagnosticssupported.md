---
title: Iwebappdiagnosticssetup::D iagnosticssupported | Microsoft-Dokumentation
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
ms.openlocfilehash: dd27e7c8759054fa2d7d67858d8d006fa9c9a152
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984581"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Bestimmt, ob die Diagnose für diese Anwendung unterstützt wird. Wenn [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) für das Objekt aufgerufen wurde, das diese Schnittstelle mit einem nicht-NULL-Wert implementiert, gibt [diagnosticssupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) `true`zurück. Wenn dies nicht der Fall ist, wird `false` zurückgegeben, und Aufrufe von [iwebappdiagnosticssetup:: anateobjectwithsiteatwebapp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) schlagen fehl.  
  
> [!IMPORTANT]
> Die [iwebappdiagnosticssetup-Schnittstelle](../../winscript/reference/iwebappdiagnosticssetup-interface.md) wird von PDM v 11.0 und höher implementiert. Gefunden in "activdbg100.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 Wenn [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) für das Objekt aufgerufen wurde, das diese Schnittstelle mit einem nicht-NULL-Wert implementiert, gibt [diagnosticssupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) `true`zurück. Wenn dies nicht der Fall ist, wird `false`zurückgegeben, und der Aufruf von [iwebappdiagnosticssetup:: deateobjectwithsiteatwebapp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) schlägt fehl.