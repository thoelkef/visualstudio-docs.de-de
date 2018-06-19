---
title: 'Sicherheitshinweis: Anfügen an einen Prozess, der im Besitz eines nicht vertrauenswürdigen Benutzers kann gefährlich sein. Wenn die folgende Informationen verdächtig, oder Sie nicht sicher sind, nicht für diesen Prozess anfügen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 68d88e01dde07789467272db830cae45ca5d60c4
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2018
ms.locfileid: "34178007"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Sicherheitshinweis: Anfügen an einen Prozess, der im Besitz eines nicht vertrauenswürdigen Benutzers kann gefährlich sein. Wenn die folgende Informationen verdächtig, oder Sie nicht sicher sind, nicht für diesen Prozess anfügen
Diese Sicherheitswarnung wird direkt vor dem Anhängen an einen Prozess angezeigt, der nicht voll vertrauenswürdigen Code enthält oder der im Besitz eines nicht vertrauenswürdigen Benutzers ist. Ein nicht vertrauenswürdiger Prozess, der bösartigen Code enthält, kann unter Umständen den das Debuggen ausführenden Computer beschädigen. Wenn Sie Grund für den Prozess zu misstrauen, dann klicken Sie auf **"Abbrechen"** um Debuggen zu verhindern.  
  
 Um diese Warnung zu unterdrücken, wenn Debuggen eines gültigen Szenarios, schließen Sie Visual Studio, und legen Sie den Wert für diesen Registrierungsschlüssel auf 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`, und klicken Sie dann Visual Studio neu starten. Nachdem das Debuggen des Szenarios beendet ist, setzten Sie den Wert auf 0 zurück und starten Visual Studio neu.  
  
 Zu den "vertrauenswürdigen Benutzern" zählen Sie selbst und noch eine Reihe weiterer Standardbenutzern, die üblicherweise auf Computern definiert sind, auf denen .NET Framework installiert ist (z. B. `aspnet`, `localsystem`, `networkservice` und `localservice`).  
  
## <a name="uielement-list"></a>UIElement-Liste  
 name  
 Name der zu debuggenden Assembly  
  
 Benutzer  
 Aktueller Benutzer  
  
 Anfügen  
 Klicken Sie auf diese Schaltfläche, um das Debuggen durch Anfügen fortzusetzen  
  
 Nicht anfügen  
 Nicht an den Prozess anfügen  
  
## <a name="see-also"></a>Siehe auch  
 [Fügen an laufende Prozesse an](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)