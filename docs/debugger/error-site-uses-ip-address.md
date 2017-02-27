---
title: "Fehler: Site verwendet IP-Adresse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.webdbg_siteusesipaddress"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugger, Webanwendungsfehler"
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Fehler: Site verwendet IP-Adresse
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Zu diesem Fehler kommt es beim Versuch des Debuggers, sich automatisch an eine Webanwendung anzuhängen, die eine IP\-Adresse verwendet.  Dies passiert, wenn Sie in IIS **Identifikation der Webseite** in **Spezielle IP\-Adresse verwenden** ändern.  
  
 Damit das automatische Anhängen funktioniert, muss das Projekt mit einer speziellen IP\-Adresse und nicht nur mit dem Computernamen erstellt werden.  Andernfalls ändert der Debugger den Computeramen in Localhost, wodurch beim Senden des DEBUG\-Verbs an IIS ein Fehler auftritt.  
  
### So beheben Sie diesen Fehler  
  
1.  Führen Sie das Anhängen stattdessen manuell aus \(wählen Sie im Menü Debuggen **An den Prozess anhängen** aus\).  
  
     \- oder \-  
  
2.  Ändern Sie die Einstellung von **Identifikation der IIS\-Website**.  
  
## Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)