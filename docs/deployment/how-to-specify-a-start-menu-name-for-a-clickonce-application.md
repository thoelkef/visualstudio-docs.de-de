---
title: "How to: Specify a Start Menu Name for a ClickOnce Application | Microsoft Docs"
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
  - "Start menu resource name"
  - "Start menu name"
  - "ClickOnce deployment, Start menu name"
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# How to: Specify a Start Menu Name for a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung sowohl für die Online\- als auch Offlineverwendung installiert wird, wird im **Startmenü** und in der Liste **Software** ein Eintrag hinzugefügt.  Standardmäßig ist der Anzeigename derselbe wie der Name der Anwendungsassembly, aber Sie können den Anzeigenamen durch Festlegen der Option **Produktname** im Dialogfeld **Veröffentlichungsoptionen** ändern.  
  
 Der **Produktname** wird auf der Seite publish.htm angezeigt. Für eine installierte Offline\-Anwendung ist dies der Name des Eintrags im Menü **Start** und der Name, der unter **Software** angezeigt wird.  
  
 Der **Herausgebername** wird auf der Seite publish.htm oberhalb von **Produktname** angezeigt, und stellt für eine installierte Offlineanwendung auch den Namen des Ordners dar, der das Symbol der Anwendung im Menü **Start** enthält.  
  
 Sie können die Eigenschaften von **Produktname** und **Herausgebername** im **Projekt\-Designer** auf der Seite **Veröffentlichen** im Dialogfeld **Veröffentlichungsoptionen** festlegen.  
  
### So legen Sie einen im Startmenü\-Namen fest  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die Schaltfläche **Optionen**, um das Dialogfeld **Veröffentlichungsoptionen** zu öffnen.  
  
4.  Klicken Sie auf **Beschreibung**.  
  
5.  Geben Sie im Dialogfeld **Veröffentlichungsoptionen** den Namen ein, der unter **Produktname** angezeigt werden soll.  
  
6.  Optional können Sie in **Herausgebername** einen Herausgebernamen eingeben.  
  
## Siehe auch  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)