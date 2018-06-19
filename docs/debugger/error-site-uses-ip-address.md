---
title: 'Fehler: Site verwendet IP-Adresse | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b726902c57cc95b694f2ab7e656a444ed42a0ba9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470903"
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