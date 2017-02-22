---
title: "Beim Kontaktieren des Remotecomputers ist ein DCOM-Fehler aufgetreten. Zugriff verweigert. | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.remote.dcom_access_denied"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "DCOM, Zugriffsfehler"
  - "Kein Zugriff auf Remote-DCOM (Fehler)"
  - "Remotedebuggen, DCOM-Fehler"
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Beim Kontaktieren des Remotecomputers ist ein DCOM-Fehler aufgetreten. Zugriff verweigert.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Remotedebugging verwendet DCOM für die Kommunikation zwischen dem lokalen und dem Remotecomputer, wenn eine der folgenden Situationen vorliegt:  
  
-   Der Debugger ist auf **Systemeigenen Kompatibilitätsmodus verwenden** festgelegt, oder auf der Seite **Extras \/ Optionen \/ Debugging** ist **Verwalteter Kompatibilitätsmodus** aktiviert.  
  
-   Sie debuggen verwalteten C\+\+\-Code \(C\+\+\/CLI\).  
  
-   In Visual Studio 2013 ist auf der Seite **Extras \/ Optionen \/ Debugging** die Option **Systemeigenes Bearbeiten und Fortfahren aktivieren** aktiviert.  
  
-   Einige Debuggingszenarien von Drittanbietern  
  
 Dieser Fehler tritt auf, wenn der Visual Studio\-Prozess sich nicht über DCOM beim Remotedebuggerprozess authentifizieren kann \(oder die angegebenen Anmeldeinformationen für unzureichend angesehen wurden\). Das Problem kann mit einer oder zwei der folgenden Methoden möglicherweise umgangen werden:  
  
-   Deaktivieren Sie **Systemeigenen Kompatibilitätsmodus verwenden** und **Verwalteter Kompatibilitätsmodus**.  
  
-   Deaktivieren Sie in Visual Studio 2013 die Option **Systemeigenes Bearbeiten und Fortfahren aktivieren**.  
  
-   Starten Sie beide Computer neu.  
  
-   Wenn für das Remotedebugging die Eingabe von Anmeldeinformationen erforderlich ist, aktivieren Sie die Option zum Speichern der Anmeldeinformationen.  
  
## Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remotedebugging](../debugger/remote-debugging.md)