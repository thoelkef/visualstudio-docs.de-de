---
title: "How to: Enable AutoStart for CD Installations | Microsoft Docs"
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
  - "ClickOnce deployment, AutoStart"
  - "ClickOnce deployment, installation on CD or DVD"
  - "deploying applications [ClickOnce], installation on CD or DVD"
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Enable AutoStart for CD Installations
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Bereitstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung über Wechselmedien wie CD\-ROM oder DVD\-ROM können Sie `AutoStart` aktivieren, sodass die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung beim Einlegen des Datenträgers automatisch gestartet wird.  
  
 `AutoStart` kann im **Projekt\-Designer** auf der Seite **Veröffentlichen** aktiviert werden.  
  
### So aktivieren Sie AutoStart  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die Schaltfläche **Optionen**.  
  
     Das Dialogfeld **Veröffentlichungsoptionen** wird angezeigt.  
  
4.  Klicken Sie auf **Bereitstellung**.  
  
5.  Aktivieren Sie das Kontrollkästchen **Bei CD\-Installationen automatisch Setup starten, wenn CD eingelegt wird**.  
  
     Beim Veröffentlichen der Anwendung wird die Datei Autorun.inf an den Veröffentlichungsort kopiert.  
  
## Siehe auch  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)