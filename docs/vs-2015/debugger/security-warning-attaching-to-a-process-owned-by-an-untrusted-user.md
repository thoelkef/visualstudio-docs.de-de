---
title: 'Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn Sie die folgende Informationen verdächtig wirken oder Sie nicht sicher sind, nicht für diesen Prozess anfügen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b856ac3a61d8af72d78546948bbe4ab780e9512e
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "47590447"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Sicherheitswarnung: Das Anfügen an einen Prozess, der einem nicht vertrauenswürdigen Benutzer gehört, kann gefährlich sein. Wenn die folgenden Informationen verdächtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, fügen Sie an den Prozess nichts an
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Sicherheitswarnung: Anfügen an einen Prozess von einem nicht vertrauenswürdigen Benutzer gehört, kann riskant sein. Wenn Sie die folgende Informationen verdächtig wirken oder Sie nicht sicher sind, nicht für diesen Prozess anfügen](https://docs.microsoft.com/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process).  
  
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



