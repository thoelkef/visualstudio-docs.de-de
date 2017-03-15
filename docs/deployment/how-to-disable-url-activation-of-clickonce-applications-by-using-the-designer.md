---
title: "How to: Disable URL Activation of ClickOnce Applications by Using the Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "disallowURLActivation"
  - "URL activation, ClickOnce applications"
  - "ClickOnce deployment, URL activation"
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# How to: Disable URL Activation of ClickOnce Applications by Using the Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Regel wird eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung automatisch gestartet, sobald sie von einem Webserver installiert wurde.  Aus Sicherheitsgründen können Sie dieses Verhalten deaktivieren und Benutzer auffordern, die Anwendung stattdessen über das **Startmenü** zu starten.  Im folgenden Verfahren wird beschrieben, wie Sie die URL\-Aktivierung deaktivieren.  
  
 Dieses Verfahren kann nur für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen verwendet werden, die von einem Webserver auf dem Computer des Benutzers installiert wurden.  Es kann nicht für reine Onlineanwendungen eingesetzt werden, die nur über ihre URL gestartet werden können.  Weitere Informationen zu den Unterschieden zwischen reinen Onlineanwendungen und installierten Anwendungen finden Sie unter [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Diese Vorgehensweise basiert auf [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Sie können diese Aufgabe auch mithilfe von [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] durchführen.  Weitere Informationen finden Sie unter [How to: Disable URL Activation of ClickOnce Applications](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## Verfahren  
  
#### So deaktivieren Sie die URL\-Aktivierung für die Anwendung  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Projektnamen, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf der Seite **Eigenschaften** auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf **Optionen**.  
  
4.  Klicken Sie auf **Manifeste**.  
  
5.  Aktivieren Sie das Kontrollkästchen **Verhindern, dass Anwendungen über eine URL aktiviert werden**.  
  
6.  Stellen Sie die Anwendung bereit.  
  
## Siehe auch  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)