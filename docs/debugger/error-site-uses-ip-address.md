---
title: 'Fehler: Site verwendet IP-Adresse | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58db12ba9dbbc9526ac86262a6be5b2c0a7f765e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460545"
---
# <a name="error-site-uses-ip-address"></a>Fehler: Site verwendet IP-Adresse
Zu diesem Fehler kommt es beim Versuch des Debuggers, sich automatisch an eine Webanwendung anzuhängen, die eine IP-Adresse verwendet. Dies passiert, wenn Sie in IIS **Identifikation der Webseite** in **Spezielle IP-Adresse verwenden** ändern.

 Damit das automatische Anhängen funktioniert, muss das Projekt mit einer speziellen IP-Adresse und nicht nur mit dem Computernamen erstellt werden. Andernfalls ändert der Debugger den Computeramen in Localhost, wodurch beim Senden des DEBUG-Verbs an IIS ein Fehler auftritt.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Führen Sie das Anhängen stattdessen manuell aus (wählen Sie im Menü „Debuggen“ **An den Prozess anhängen** aus).

     – oder –

2. Ändern Sie die Einstellung **Identifikation der IIS-Website**.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)