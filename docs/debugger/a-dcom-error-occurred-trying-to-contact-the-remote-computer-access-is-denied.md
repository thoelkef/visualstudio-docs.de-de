---
title: Wenden Sie sich an den Remotecomputer ist ein DCOM-Fehler aufgetreten. Der Zugriff wird verweigert. | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe153a5252603cf967b396932a6479a8df437a08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Wenden Sie sich an den Remotecomputer ist ein DCOM-Fehler aufgetreten. Der Zugriff wird verweigert.
Remotedebugging verwendet DCOM für die Kommunikation zwischen dem lokalen und dem Remotecomputer, wenn eine der folgenden Situationen vorliegt:  
  
-   Der Debugger so eingestellt ist **systemeigenen Kompatibilitätsmodus** oder **verwalteter Kompatibilitätsmodus** eingecheckt wird die **Extras > Optionen > Debugging** Seite  
  
-   Sie debuggen verwalteten C++-Code (C++/CLI).  
  
-   In Visual Studio 2013 Wenn **native bearbeiten und Fortfahren aktivieren** eingecheckt wird die **Tools > Optionen > Debugging** Seite  
  
-   Einige Debuggingszenarien von Drittanbietern  
  
 Dieser Fehler tritt auf, wenn der Visual Studio-Prozess sich nicht über DCOM beim Remotedebuggerprozess authentifizieren kann (oder die angegebenen Anmeldeinformationen für unzureichend angesehen wurden). Das Problem kann mit einer oder zwei der folgenden Methoden möglicherweise umgangen werden:  
  
-   Deaktivieren Sie  **Systemeigenen Kompatibilitätsmodus verwenden** und **Verwalteter Kompatibilitätsmodus**.  
  
-   Deaktivieren Sie in Visual Studio 2013 die Option **Systemeigenes Bearbeiten und Fortfahren aktivieren**.  
  
-   Starten Sie beide Computer neu.  
  
-   Wenn für das Remotedebugging die Eingabe von Anmeldeinformationen erforderlich ist, aktivieren Sie die Option zum Speichern der Anmeldeinformationen.  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remotedebuggen](../debugger/remote-debugging.md)