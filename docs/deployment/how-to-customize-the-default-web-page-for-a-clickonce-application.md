---
title: "Gewusst wie: Anpassen der Standardwebseite f&#252;r eine ClickOnce-Anwendung | Microsoft Docs"
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
  - "Publish.htm (Webseite)"
  - "Standardwebseite für ClickOnce-Bereitstellung"
  - "Bereitstellen von Anwendungen [ClickOnce], Veröffentlichung"
  - "Veröffentlichen, ClickOnce"
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# Gewusst wie: Anpassen der Standardwebseite f&#252;r eine ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie eine ClickOnce\-Anwendung im Web veröffentlichen, wird auch eine Webseite automatisch generiert und veröffentlicht.  Die Standardseite enthält den Namen der Anwendung, Links zum Installieren der Anwendung und erforderlicher Komponenten, sowie Links zum Zugriff auf die Hilfe von MSDN.  
  
> [!NOTE]
>  Abhängig vom Computer, auf dem die Seite angezeigt wird, und den Komponenten, die Sie hinzugefügt haben, können die auf der Seite verfügbaren Links variieren.  
  
 Der Standardname der Webseite lautet Publish.htm. Sie können diesen Namen im **Projekt\-Designer** ändern.  Weitere Informationen finden Sie unter [How to: Specify a Publish Page for a ClickOnce Application](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 Die Webseite Publish.htm wird nur veröffentlicht, wenn eine neuere Version erkannt wird.  
  
> [!NOTE]
>  Änderungen an den Einstellungen zum **Veröffentlichen** haben keinen Einfluss auf die Seite Publish.htm. Es gibt jedoch eine Ausnahme: Wenn Sie nach der ersten Veröffentlichung erforderliche Komponenten hinzufügen oder entfernen, ist die Liste der erforderlichen Komponenten nicht mehr korrekt.  Sie müssen den Linktext der erforderlichen Komponenten den Änderungen entsprechend bearbeiten.  
  
### So passen Sie die Veröffentlichungswebseite an  
  
1.  Veröffentlichen Sie die ClickOnce\-Anwendung an einem Webspeicherort.  Weitere Informationen finden Sie unter [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  Öffnen Sie auf dem Webserver die Datei Publish.htm mit Visual Web Designer oder einem anderen HTML\-Editor.  
  
3.  Passen Sie die Seite wie gewünscht an, und speichern Sie sie.  
  
4.  Dies ist optional.  Deaktivieren Sie im Dialogfeld "Veröffentlichungsoptionen" die Option zum automatischen Generieren der Bereitstellungswebseite nach jeder Veröffentlichung, um zu verhindern, dass Visual Studio die benutzerdefinierte Veröffentlichungswebseite überschreibt.  
  
## Siehe auch  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Install Prerequisites with a ClickOnce Application](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [How to: Specify a Publish Page for a ClickOnce Application](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)