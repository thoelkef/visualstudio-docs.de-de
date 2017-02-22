---
title: "Sicherheitswarnung: Das Anf&#252;gen an einen Prozess, der einem nicht vertrauensw&#252;rdigen Benutzer geh&#246;rt, kann gef&#228;hrlich sein. Wenn die folgenden Informationen verd&#228;chtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, f&#252;gen Sie an den Prozess nichts an. | Microsoft Docs"
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
  - "vs.debug.attachsecuritywarning"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Sicherheitswarnung: Das Anf&#252;gen an einen Prozess, der einem nicht vertrauensw&#252;rdigen Benutzer geh&#246;rt, kann gef&#228;hrlich sein. Wenn die folgenden Informationen verd&#228;chtig wirken oder Sie sich hinsichtlich der Vorgehensweise nicht sicher sind, f&#252;gen Sie an den Prozess nichts an.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Sicherheitswarnung wird direkt vor dem Anhängen an einen Prozess angezeigt, der nicht voll vertrauenswürdigen Code enthält oder der im Besitz eines nicht vertrauenswürdigen Benutzers ist.  Ein nicht vertrauenswürdiger Prozess, der bösartigen Code enthält, kann unter Umständen den das Debuggen ausführenden Computer beschädigen.  Wenn Sie Grund dazu haben, dem Prozess zu misstrauen, sollten Sie das Debuggen durch Klicken auf **Abbrechen** verhindern.  
  
 Um diese Warnung bei Debuggen eines rechtmäßigen Szenarios zu unterdrücken, führen Sie Visual Studio aus, und legen Sie den Wert dieses Registrierungsschlüssels auf 1 fest: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`. Starten Sie dann Visual Studio neu.  Nachdem das Debuggen des Szenarios beendet ist, setzten Sie den Wert auf 0 zurück und starten Visual Studio neu.  
  
 Zu den "vertrauenswürdigen Benutzern" zählen Sie selbst und noch eine Reihe weiterer Standardbenutzern, die üblicherweise auf Computern definiert sind, auf denen .NET Framework installiert ist \(z. B. `aspnet`, `localsystem`, `networkservice` und `localservice`\).  
  
## UIElement-Liste  
 Name  
 Name der zu debuggenden Assembly  
  
 Benutzer  
 Aktueller Benutzer  
  
 Anfügen  
 Klicken Sie auf diese Schaltfläche, um das Debuggen durch Anfügen fortzusetzen  
  
 Nicht anfügen  
 Nicht an den Prozess anfügen  
  
## Siehe auch  
 [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)