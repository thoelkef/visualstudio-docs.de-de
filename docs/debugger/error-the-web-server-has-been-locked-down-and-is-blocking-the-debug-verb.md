---
title: "Fehler: Der Webserver wurde gesperrt und blockiert das DEBUG-Verb | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.webdbg_debug_verb_blocked"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugger, Webanwendungsfehler"
ms.assetid: 9c8c4812-17db-484d-9c1b-ffd9e3bfef5a
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Fehler: Der Webserver wurde gesperrt und blockiert das DEBUG-Verb
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Fehler beim schrittweisen Ausführen einer Webanwendung oder eines XML\-Webdiensts, da das Tool zum Sperren der IIS\-Sicherheit ausgeführt und URLScan installiert und aktiviert wurde.  Durch diesen Zustand wird IIS daran gehindert, das DEBUG\-Verb zu empfangen.  
  
 URLScan ist ein Sicherheitstool, das Websiteadministratoren in Kombination mit dem Tool zum Sperren der IIS\-Sicherheit die Möglichkeit gibt, nicht benötigte Features zu deaktivieren und die Typen der vom Server zu verarbeitenden HTTP\-Anforderungen einzugrenzen.  Durch das Abweisen spezifischer HTTP\-Anforderungen verhindert das URLScan\-Sicherheitstool, dass potenziell schädliche Anforderungen auf den Server gelangen und dort Schaden anrichten können.  
  
 Wenn Ihre Anwendung auf Windows Server 2003 unter IIS 6.0 ausgeführt wird, müssen Sie das Tool zum Sperren der IIS\-Sicherheit nicht ausführen, da IIS 6.0 diese Funktionalität bereits enthält.  
  
### So aktivieren Sie das Debuggen auf einem Webserver mit installiertem URLScan\-Tool  
  
1.  Suchen Sie die Datei **Urlscan.ini**.  Normalerweise befindet sie sich in einem Verzeichnis wie dem Folgenden:  
  
     C:\\WINNT\\System32\\Inetsrv\\urlscan  
  
2.  Erstellen Sie eine Kopie der Datei, und nennen Sie sie Urlscan.old.  
  
3.  Öffnen Sie die ursprüngliche Version der Datei **Urlscan.ini** mit dem Editor oder einem Text\-Editor Ihrer Wahl.  
  
4.  Suchen Sie in Urlscan.ini den Abschnitt \[AllowVerbs\].  Fügen Sie dem Abschnitt **\[AllowVerbs\]** den Eintrag **DEBUG** hinzu.  Wenn im Abschnitt \[AllowVerbs\] ;DEBUG enthalten ist, können Sie das Semikolon entfernen \(durch das das Verb auskommentiert wird\).  
  
5.  Suchen Sie den Abschnitt **\[DenyVerbs\]**.  Wenn **DEBUG** im Abschnitt **\[DenyVerbs\]** angezeigt wird, entfernen Sie es.  
  
6.  Speichern Sie die Datei.  
  
7.  Starten Sie den Server oder IIS neu.  
  
## Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Fehler: Der Webserver konnte die angeforderte Ressource nicht finden](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)