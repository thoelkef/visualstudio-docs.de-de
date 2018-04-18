---
title: Wenden Sie sich an den Remotecomputer ist ein DCOM-Fehler aufgetreten. Der Zugriff wird verweigert. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_access_denied
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a46129dd8b83cfbbdb62c6118cb2575b1b8cfc8a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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