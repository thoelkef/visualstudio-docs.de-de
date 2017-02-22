---
title: "How to: Specify the ClickOnce Offline or Online Install Mode | Microsoft Docs"
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
  - "ClickOnce deployment, specifying install mode"
  - "install mode"
  - "online applications"
  - "offline applications"
  - "ClickOnce install mode"
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Specify the ClickOnce Offline or Online Install Mode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Über den `Install Mode` für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung wird festgelegt, ob diese offline oder online verfügbar ist.  Wenn Sie die Option **Anwendung ist nur online verfügbar** auswählen, muss der Benutzer auf den Veröffentlichungsort \(Webseite oder Dateifreigabe\) von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zugreifen, um die Anwendung ausführen zu können.  Wenn Sie die Option **Die Anwendung ist auch offline verfügbar** auswählen, werden durch die Anwendung Einträge im **Startmenü** und im Dialogfeld **Software** hinzugefügt. Der Benutzer kann auf diese Weise die Anwendung auch ausführen, ohne eine Verbindung herzustellen.  
  
 Der `Install Mode` kann im **Projekt\-Designer** auf der Seite **Veröffentlichen** festgelegt werden.  
  
 **Hinweis** Der `Install Mode` kann auch mit dem Webpublishing\-Assistenten festgelegt werden.  Weitere Informationen finden Sie unter [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### So stellen Sie eine ClickOnce\-Anwendung online zur Verfügung  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie im Bereich **Installationsmodus und \-einstellungen** auf das Optionsfeld **Anwendung ist nur online verfügbar**.  
  
### So stellen Sie eine ClickOnce\-Anwendung online oder offline zur Verfügung  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie im Bereich **Installationsmodus und \-einstellungen** auf das Optionsfeld **Die Anwendung ist auch offline verfügbar**.  
  
     Bei der Installation der Anwendung werden im **Startmenü** und in der Systemsteuerung im Dialogfeld **Software** Einträge hinzugefügt.  
  
## Siehe auch  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md)