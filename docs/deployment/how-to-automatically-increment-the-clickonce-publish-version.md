---
title: "How to: Automatically Increment the ClickOnce Publish Version | Microsoft Docs"
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
  - "deploying applications [ClickOnce], incrementing publish version automatically"
  - "Publish Version property, incrementing"
  - "ClickOnce deployment, incrementing publish version automatically"
  - "publishing, ClickOnce"
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Automatically Increment the ClickOnce Publish Version
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung veröffentlichen, führt eine Änderung der `Publish Version`\-Eigenschaft dazu, dass die Anwendung als Update veröffentlicht wird.  Die Nummer der `Revision` der `Publish Version` bei jeder Veröffentlichung der Anwendung von Visual Studio standardmäßig automatisch erhöht.  
  
 Sie können dieses Verhalten im **Projekt\-Designer** auf der Seite **Veröffentlichen** deaktivieren.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### So deaktivieren Sie die automatische Erhöhung der Veröffentlichungsversion  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Deaktivieren Sie im Abschnitt **Veröffentlichungsversion** das Kontrollkästchen **Revisionsnummer automatisch mit jeder Veröffentlichung erhöhen**.  
  
## Siehe auch  
 [How to: Set the ClickOnce Publish Version](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)