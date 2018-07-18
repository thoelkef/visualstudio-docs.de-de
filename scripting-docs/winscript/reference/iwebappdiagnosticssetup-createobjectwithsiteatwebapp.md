---
title: IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 1442297fcacb3a9464f9ea67489c91c8ab64ad78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733940"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Diese Methode erstellt zusammen die Klasse, deren ID, die Sie sich mit übergeben `rclsid` mithilfe der `dwClsContext`. Dies ist ähnlich wie bei [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) funktioniert, außer dass im Fall von `CreateObjectWithSiteAtWebApp` das Objekt asynchron an die Webanwendung-UI-Thread erstellt wird. Das durch die Klassen-ID angegebene Objekt implementieren sollten [IWebAppDiagnosticsObjectInitialization-Schnittstelle](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Nachdem das Objekt erstellt wurde, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) mit einem Verweis auf die PDM-Debug-Anwendung aufgerufen wird und die `hPassToObject` Parameter `CreateObjectWithSiteAtWebApp`. Verwenden Sie diese Methode in der app ein Handle auf eine anonyme Pipe übergeben, die Sie kopiert haben, mit [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450).  
  
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
 Ein Wert, der an das Objekt übergeben wird, sobald es an den UI-Thread erstellt wird, wenn das Objekt implementiert [IWebAppDiagnosticsObjectInitialization-Schnittstelle](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).