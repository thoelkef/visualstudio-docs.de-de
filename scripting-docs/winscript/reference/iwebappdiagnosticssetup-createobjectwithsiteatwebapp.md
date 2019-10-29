---
title: 'Iwebappdiagnosticssetup:: er\ateobjectwithsiteatwebapp | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 253b995c200566868ac9ccc06b259e0a152e1676
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984604"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Diese Methode erstellt die-Klasse, deren ID mit `rclsid` mithilfe der `dwClsContext`übergeben wird. Dies ähnelt der Funktionsweise von [iremotedebugapplication:: forateinstanceatapplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) , mit dem Unterschied, dass im Fall von `CreateObjectWithSiteAtWebApp` das Objekt asynchron im UI-Thread der Webanwendung erstellt wird. Das durch die Klassen-ID angegebene Objekt sollte die [iwebappdiagnosticsobjectinitialization-Schnittstelle](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)implementieren. Nachdem das Objekt erstellt wurde, wird [iwebappdiagnosticsobjectinitialization:: Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) mit einem Verweis auf die PDM-Debuganwendung und den `hPassToObject`-Parameter `CreateObjectWithSiteAtWebApp`aufgerufen. Sie können diese Methode verwenden, um ein Handle an eine anonyme Pipe zu übergeben, die Sie mithilfe von [dupliskiehandle](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle)kopiert haben.  
  
> [!IMPORTANT]
> Die [iwebappdiagnosticssetup-Schnittstelle](../../winscript/reference/iwebappdiagnosticssetup-interface.md) wird von PDM v 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Parameter  
 `rclsid`  
 Die Klassen-ID der zu erstellenden Klasse.  
  
 `dwClsContext`  
 Der Kontext, in dem der Code ausgeführt wird. In den meisten Fällen ist es CLSCTX_INPROC_SERVER.  
  
 `riid`  
 Nicht verwendet.  
  
 `hPassToObject`  
 Ein Wert, der an das Objekt übergeben wird, sobald es im UI-Thread erstellt wurde, wenn das Objekt die [iwebappdiagnosticsobjectinitialization-Schnittstelle](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)implementiert.