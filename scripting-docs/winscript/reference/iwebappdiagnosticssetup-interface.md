---
title: IWebAppDiagnosticsSetup-Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6e273f29bee6e4d2aae26c01c477373a735624c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734000"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup-Schnittstelle
Diese Schnittstelle wird von einer PDM-Debug-Anwendung zum Erstellen von COM-Objekten im Prozess, der debuggt wird, und Aktivieren der Diagnose Web implementiert. Wenn die PDM implementiert Anwendung Debuggen ["IObjectWithSite"](http://go.microsoft.com/fwlink/?LinkId=232438), Internet Explorer ruft [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) auf, nachdem es erstellt wurde und übergibt einen Verweis auf [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). Ruft eine Anwendung WWA [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) und übergibt die WWA Schnittstelle IWebApplicationHost. Wenn [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) mit einem Wert ungleich NULL aufgerufen wurde [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) "Wahr" zurückgegeben. Wenn nicht, es "false" zurückgegeben, und die Aufrufe von [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) fehl.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup`wird von PDM V11. 0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Diese Schnittstelle legt die folgenden Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Ruft den Text-Dokumenten, die durch den angegebenen Filter ausgeblendet sind.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Bestimmt, ob das angegebene Dokument zu einem der untergeordneten Knoten dieses Knotens gehört.|