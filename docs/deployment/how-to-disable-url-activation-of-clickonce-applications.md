---
title: "How to: Disable URL Activation of ClickOnce Applications | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "disallowUrlActivation"
  - "URL activation, ClickOnce applications"
  - "ClickOnce deployment, URL activation"
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Disable URL Activation of ClickOnce Applications
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Regel wird eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Anwendung automatisch gestartet, sobald sie von einem Webserver installiert wurde.  Aus Gründen der Sicherheit könnten Sie dieses Verhalten deaktivieren und Benutzer dazu auffordern, die Anwendung stattdessen über das Menü **Start** zu öffnen.  Das folgende Verfahren beschreibt das Deaktivieren der URL\-Aktivierung.  
  
 Dieses Verfahren kann nur für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen verwendet werden, die von einem Webserver auf dem Computer des Benutzers installiert werden.  Es kann nicht für reine Onlineanwendungen verwendet werden, die nur über ihre URL gestartet werden können.  Weitere Informationen zu den Unterschieden zwischen reinen Onlineanwendungen und installierten Anwendungen finden Sie unter [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Dieses Verfahren verwendet das [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]Tool „MageUI.exe“.  Weitere Informationen zu diesem Tool finden Sie unter [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  Sie können dieses Verfahren auch mithilfe von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausführen.  
  
## Prozedur  
  
#### So deaktivieren Sie die URL\-Aktivierung für Ihre Anwendung  
  
1.  Öffnen Sie Ihr Bereitstellungsmanifest in „MageUI.exe“.  Wenn Sie noch kein Manifest erstellt haben, führen Sie die Schritte in [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) aus.  
  
2.  Wählen Sie die Registerkarte **Bereitstellungsoptionen** aus.  
  
3.  Deaktivieren Sie das Kontrollkästchen **Anwendung nach dem Installieren automatisch ausführen**.  
  
4.  Speichern und signieren Sie das Manifest.  
  
## Siehe auch  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)