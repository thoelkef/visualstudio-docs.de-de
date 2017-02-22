---
title: "How to: Specify the Location Where End Users Will Install From | Microsoft Docs"
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
  - "deploying applications [ClickOnce], specifying an installation URL"
  - "URLs, specifying an installation URL"
  - "installation, specifying installation an URL"
  - "Installation URL property"
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Specify the Location Where End Users Will Install From
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung veröffentlichen, ist der Speicherort zum Herunterladen und Installieren der Anwendung durch die Benutzer nicht unbedingt der Speicherort, an dem Sie die Anwendung ursprünglich veröffentlichen.  In manchen Unternehmen veröffentlicht ein Entwickler eine Anwendung z. B. auf einem Stagingserver, und ein Administrator verschiebt diese anschließend auf einen Webserver.  
  
 In diesem Fall können Sie die `Installation URL`\-Eigenschaft verwenden, um einen Webserver anzugeben, von dem aus Benutzer die Anwendung herunterladen können.  Dies ist notwendig, damit dem Anwendungsmanifest der Speicherort für Updates bekannt ist.  
  
 Die `Installation URL`\-Eigenschaft kann im **Projekt\-Designer** auf der Seite **Veröffentlichen** festgelegt werden.  
  
 **Hinweis** Die `Installation URL`\-Eigenschaft kann auch mit dem **Webpublishing \-Assistenten** festgelegt werden.  Weitere Informationen finden Sie unter [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### So geben Sie eine Installations\-URL an  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Geben Sie im Feld URL für Installation als Installationspfad eine voll qualifizierte URL im Format http:\/\/www.microsoft.com\/Anwendungsname ein, oder verwenden Sie einen UNC\-Pfad im Format \\\\Server\\Anwendungsname.  
  
## Siehe auch  
 [How to: Specify Where Visual Studio Copies the Files](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)