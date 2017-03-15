---
title: "How to: Set the ClickOnce Publish Version | Microsoft Docs"
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
  - "ClickOnce deployment, setting publish version"
  - "publishing, ClickOnce"
  - "Publish Version property"
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Set the ClickOnce Publish Version
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die `Publish Version`\-Eigenschaft von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] legt fest, ob die veröffentlichte Anwendung als Update behandelt wird.  Bei jeder Versionserhöhung wird die Anwendung als Update veröffentlicht.  
  
 Die `Publish Version`\-Eigenschaft kann im **Projekt\-Designer** auf der Seite **Veröffentlichen** festgelegt werden.  
  
> [!NOTE]
>  Eine standardmäßig aktivierte Projektoption sorgt dafür, dass die `Publish Version`\-Eigenschaft bei jeder Veröffentlichung der Anwendung automatisch erhöht wird.  Weitere Informationen finden Sie unter [How to: Automatically Increment the ClickOnce Publish Version](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### So ändern Sie die Veröffentlichungsversion  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Erhöhen Sie im Feld **Veröffentlichungsversion** die Versionswerte von **Hauptversion**, **Nebenversion**, **Build** oder **Revision**.  
  
    > [!NOTE]
    >  Sie sollten nie eine Versionsnummer herabsetzen, da dies zu unvorhersehbarem Verhalten beim Update führen kann.  
  
## Siehe auch  
 [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md)   
 [How to: Automatically Increment the ClickOnce Publish Version](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)