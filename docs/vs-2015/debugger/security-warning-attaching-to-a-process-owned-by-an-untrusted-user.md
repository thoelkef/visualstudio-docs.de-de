---
title: 'Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn Sie die folgende Informationen verdächtig wirken oder Sie nicht sicher sind, nicht für diesen Prozess anfügen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dac3ad5d51e2934bd2cbdf5a8fe9ad30a4a90a8b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745588"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Sicherheitswarnung wird direkt vor dem Anhängen an einen Prozess angezeigt, der nicht voll vertrauenswürdigen Code enthält oder der im Besitz eines nicht vertrauenswürdigen Benutzers ist. Ein nicht vertrauenswürdiger Prozess, der bösartigen Code enthält, kann unter Umständen den das Debuggen ausführenden Computer beschädigen. Wenn Sie Grund für den Prozess zu misstrauen, klicken Sie auf **Abbrechen** um Debuggen zu verhindern.  
  
 Um diese Warnung zu unterdrücken, beim Debuggen eines rechtmäßigen Szenarios, schließen Sie Visual Studio, und legen Sie den Wert dieses Registrierungsschlüssels auf 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`, und starten Sie Visual Studio neu. Nachdem das Debuggen des Szenarios beendet ist, setzten Sie den Wert auf 0 zurück und starten Visual Studio neu.  
  
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



