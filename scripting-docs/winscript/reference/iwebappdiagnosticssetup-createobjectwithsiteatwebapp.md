---
title: IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs
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
ms.openlocfilehash: 26403a168268e817644637544d64d4205c398b75
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157658"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Diese Methode erstellt gemeinsam die Klasse, deren ID, die Sie sich mit übergeben `rclsid` mithilfe der `dwClsContext`. Dies ist ähnlich wie die [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) funktioniert, außer dass im Fall von `CreateObjectWithSiteAtWebApp` das Objekt asynchron auf die Webanwendung UI-Thread erstellt wird. Die Klassen-ID angegebene Objekt implementieren sollte [IWebAppDiagnosticsObjectInitialization-Schnittstelle](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Nachdem das Objekt erstellt wurde, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) aufgerufen wird und einen Verweis auf das PDM-Debug-Anwendung und die `hPassToObject` Parameter `CreateObjectWithSiteAtWebApp`. Sie können diese Methode verwenden, bei der app ein Handle zu einer anonymen Pipe übergeben, die Sie kopiert haben, mithilfe von [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450).  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup-Schnittstelle](../../winscript/reference/iwebappdiagnosticssetup-interface.md) wird implementiert von PDM V11. 0 und höher. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Parameter  
 `rclsid`  
 Die Klassen-ID der Klasse zu erstellen.  
  
 `dwClsContext`  
 Der Kontext, in dem der Code ausgeführt wird. In den meisten Fällen ist es CLSCTX_INPROC_SERVER.  
  
 `riid`  
 Nicht verwendet.  
  
 `hPassToObject`  
 Ein Wert, der auf das Objekt übergeben werden, wird nach der Erstellung der UI-Thread, wenn das Objekt implementiert [IWebAppDiagnosticsObjectInitialization-Schnittstelle](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).