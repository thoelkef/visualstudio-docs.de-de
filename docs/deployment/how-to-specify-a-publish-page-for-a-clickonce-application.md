---
title: "How to: Specify a Publish Page for a ClickOnce Application | Microsoft Docs"
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
  - "deploying applications [ClickOnce], specifying publish page"
  - "Publish Page property"
  - "publishing, ClickOnce"
  - "ClickOnce deployment, specifying publish page"
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Specify a Publish Page for a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung im Web veröffentlichen, wird eine Standardwebseite \(Publish.htm\) generiert und gemeinsam mit der Anwendung veröffentlicht.  Diese Seite enthält den Namen der Anwendung, einen Link zur Installation der Anwendung und\/oder erforderliche Komponenten sowie einen Link zu einem Hilfethema für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Mit der **Publish Page**\-Eigenschaft des Projekts können Sie einen Namen für die Webseite für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung angeben.  
  
 Nach dem Einrichten der Veröffentlichungsseite wird diese bei der nächsten Veröffentlichung an den Veröffentlichungsort kopiert. Sie wird bei einer erneuten Veröffentlichung nicht überschrieben.  Sie können das Layout der Seite anpassen, ohne dass die von Ihnen vorgenommenen Änderungen verloren gehen.  Weitere Informationen finden Sie unter [Gewusst wie: Anpassen der ClickOnce\-Standardwebseite](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 Sie können die **Publish Page**\-Eigenschaft im Dialogfeld **Veröffentlichungsoptionen** festlegen, auf das im **Projekt\-Designer** im Bereich **Veröffentlichen** zugegriffen werden kann.  
  
### So geben Sie für eine ClickOnce\-Anwendung eine benutzerdefinierte Webseite an  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Wählen Sie den Bereich **Veröffentlichen** aus.  
  
3.  Klicken Sie auf die Schaltfläche **Optionen**, um das Dialogfeld **Veröffentlichungsoptionen** zu öffnen.  
  
4.  Klicken Sie auf **Bereitstellung**.  
  
5.  Stellen Sie im Dialogfeld **Veröffentlichungsoptionen** sicher, dass das Kontrollkästchen **Nach dem Veröffentlichen Bereitstellungswebseite öffnen** aktiviert ist \(Dies sollte in der Standardeinstellung der Fall sein\).  
  
6.  Geben Sie im Feld **Bereitstellungswebseite** einen Namen für die Webseite ein, und klicken Sie anschließend auf **OK**.  
  
### So verhindern Sie, dass die Veröffentlichungsseite bei jeder Veröffentlichung aufgerufen wird  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Wählen Sie den Bereich **Veröffentlichen** aus.  
  
3.  Klicken Sie auf die Schaltfläche **Optionen**, um das Dialogfeld **Veröffentlichungsoptionen** zu öffnen.  
  
4.  Klicken Sie auf **Bereitstellung**.  
  
5.  Deaktivieren Sie im Dialogfeld **Veröffentlichungsoptionen** das Kontrollkästchen **Nach dem Veröffentlichen Bereitstellungswebseite öffnen**.  
  
## Siehe auch  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Gewusst wie: Anpassen der ClickOnce\-Standardwebseite](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)