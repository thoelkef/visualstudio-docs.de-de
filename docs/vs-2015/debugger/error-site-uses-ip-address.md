---
title: 'Fehler: Site verwendet IP-Adresse | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46eace1c566a2810c5914a49654f8393f425fdee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155750"
---
# <a name="error-site-uses-ip-address"></a>Fehler: Site verwendet IP-Adresse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zu diesem Fehler kommt es beim Versuch des Debuggers, sich automatisch an eine Webanwendung anzuhängen, die eine IP-Adresse verwendet. Dies passiert, wenn Sie in IIS **Identifikation der Webseite** in **Spezielle IP-Adresse verwenden** ändern.  
  
 Damit das automatische Anhängen funktioniert, muss das Projekt mit einer speziellen IP-Adresse und nicht nur mit dem Computernamen erstellt werden. Andernfalls ändert der Debugger den Computeramen in Localhost, wodurch beim Senden des DEBUG-Verbs an IIS ein Fehler auftritt.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1. Führen Sie das Anhängen stattdessen manuell aus (wählen Sie im Menü „Debuggen“ **An den Prozess anhängen** aus).  
  
     – oder –  
  
2. Ändern Sie die Einstellung **Identifikation der IIS-Website**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
