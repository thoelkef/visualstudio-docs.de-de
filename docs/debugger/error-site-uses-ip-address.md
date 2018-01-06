---
title: 'Fehler: Site verwendet IP-Adresse | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, Web application errors
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e6073fd88221e307b46a90173526876f2e2186d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="error-site-uses-ip-address"></a>Fehler: Site verwendet IP-Adresse
Zu diesem Fehler kommt es beim Versuch des Debuggers, sich automatisch an eine Webanwendung anzuhängen, die eine IP-Adresse verwendet. Dies tritt auf, wenn Sie ändern **Websiteidentifikation** auf **spezifische IP-Adresse** in IIS.  
  
 Damit das automatische Anhängen funktioniert, muss das Projekt mit einer speziellen IP-Adresse und nicht nur mit dem Computernamen erstellt werden. Andernfalls ändert der Debugger den Computeramen in Localhost, wodurch beim Senden des DEBUG-Verbs an IIS ein Fehler auftritt.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Anhängen stattdessen manuell (Wählen Sie im Menü Debuggen **an den Prozess anhängen**).  
  
     – oder –  
  
2.  Ändern der **Identifikation der IIS-Website** Einstellung.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)