---
title: "How to: Change the Publish Language for a ClickOnce Application | Microsoft Docs"
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
  - "Publish language property"
  - "ClickOnce deployment, changing publish language"
  - "publishing, ClickOnce"
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Change the Publish Language for a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie eine eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung veröffentlichen, wird die bei der Installation angezeigte Benutzeroberfläche standardmäßig in der Sprache und Kultur des Entwicklungscomputers angezeigt.  Wenn Sie eine lokalisierte Anwendung veröffentlichen, müssen Sie Sprache und Kultur der lokalisierten Version angeben.  Dies wird durch die `Publish language`\-Eigenschaft für das Projekt festgelegt.  
  
 Die `Publish language`\-Eigenschaft kann im Dialogfeld **Veröffentlichungsoptionen** festgelegt werden, auf das im **Projekt\-Designer** auf der Seite **Veröffentlichen** zugegriffen werden kann.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### So ändern Sie die Sprache für die Veröffentlichung  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die Schaltfläche **Optionen**, um das Dialogfeld **Veröffentlichungsoptionen** zu öffnen.  
  
4.  Klicken Sie auf **Beschreibung**.  
  
5.  Wählen Sie im Dialogfeld **Veröffentlichungsoptionen** in der Dropdownliste **Sprache für Veröffentlichung** eine Sprache und Kultur aus, und klicken Sie anschließend auf **OK**.  
  
## Siehe auch  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)