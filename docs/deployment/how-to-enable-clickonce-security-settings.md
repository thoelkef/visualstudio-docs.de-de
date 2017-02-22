---
title: "How to: Enable ClickOnce Security Settings | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
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
  - "security [Visual Studio], ClickOnce applications"
  - "ClickOnce deployment, security settings"
  - "security settings, ClickOnce deployment"
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Enable ClickOnce Security Settings
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Codezugriffssicherheit für ClickOnce\-Anwendungen muss aktiviert werden, damit die Anwendungen veröffentlicht werden können.  Dies geschieht automatisch, wenn Sie eine Anwendung mit dem Webpublishing\-Assistenten veröffentlichen.  
  
 In einigen Fällen kann durch Aktivieren der Codezugriffssicherheit die Leistung beim Erstellen oder Debuggen der Anwendung beeinträchtigt werden. In diesem Fall können Sie die Sicherheitseinstellungen vorübergehend deaktivieren.  
  
 Die ClickOnce\-Sicherheitseinstellungen können im **Projekt\-Designer** auf der Seite **Sicherheit** aktiviert und deaktiviert werden.  
  
### So aktivieren Sie die ClickOnce\-Sicherheitseinstellungen  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Sicherheit**.  
  
3.  Aktivieren Sie das Kontrollkästchen **ClickOnce\-Sicherheitseinstellungen aktivieren**.  
  
     Sie können jetzt auf der Seite Sicherheit die Sicherheitseinstellungen für die Anwendung anpassen.  
  
    > [!NOTE]
    >  Dieses Kontrollkästchen wird automatisch aktiviert, wenn die Anwendung mit dem **Webpublishing\-Assistenten** veröffentlicht wird.  
  
### So deaktivieren Sie die ClickOnce\-Sicherheitseinstellungen  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Sicherheit**.  
  
3.  Deaktivieren Sie das Kontrollkästchen **ClickOnce\-Sicherheitseinstellungen aktivieren**.  
  
     Die Anwendung wird mit der Sicherheitseinstellung Voll vertrauenswürdig ausgeführt. Die Einstellungen auf der Seite **Sicherheit** werden ignoriert.  
  
    > [!NOTE]
    >  Bei jeder Veröffentlichung der Anwendung mit dem Webpublishing\-Assistenten wird dieses Kontrollkästchen aktiviert. Sie müssen es nach jeder erfolgreichen Veröffentlichung wieder deaktivieren.  
  
## Siehe auch  
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Codezugriffssicherheit für ClickOnce\-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)