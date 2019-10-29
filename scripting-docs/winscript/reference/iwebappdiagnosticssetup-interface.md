---
title: Iwebappdiagnosticssetup-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e9bb3905da6227b978bc27b96493500f8d6d2ff
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984543"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup-Schnittstelle
Diese Schnittstelle wird von einer PDM-Debuganwendung implementiert, um COM-Objekte in dem Prozess zu erstellen, der debuggt wird, und um die webdiagnose zu aktivieren. Wenn das PDM-debuganwendungsobjekt [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite)implementiert, ruft Internet Explorer [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) darauf auf, nachdem es erstellt wurde, und übergibt einen Verweis auf [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127(v=vs.85)). Eine WWA-Anwendung ruft [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) auf und übergibt stattdessen die WWA-Schnittstelle iwebapplicationhost. Wenn [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) mit einem nicht-NULL-Wert aufgerufen wurde, gibt [iwebappdiagnosticssetup::D iagnosticssupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) "true" zurück. Wenn dies nicht der Fall ist, wird false zurückgegeben, und Aufrufe von [iwebappdiagnosticssetup:: deateobjectwithsiteatwebapp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) schlagen fehl.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsSetup` wird von PDM v 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Diese Schnittstelle stellt die folgenden Methoden zur Verfügung.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Ruft die Textdokumente ab, die durch den angegebenen Filter ausgeblendet sind.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Bestimmt, ob das angegebene Dokument zu einem der untergeordneten Knoten dieses Knotens gehört.|