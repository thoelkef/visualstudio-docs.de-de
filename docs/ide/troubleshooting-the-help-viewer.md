---
title: "Problembehandlung bei Help Viewer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Help Viewer 2.0, Problembehandlung"
  - "Problembehandlung [Help Viewer 2.0]"
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Problembehandlung bei Help Viewer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema werden Probleme behandelt, die bei der Verwendung des Help Viewers auftreten können.  
  
## Audio funktioniert nicht.  
 Der Help Viewer enthält keinen Audioplayer.  Wenn Sie Inhalte herunterladen, die Audiodaten enthalten, und die Auswahl von **Wiedergeben** ohne Wirkung bleibt, installieren Sie einen Audioplayer.  
  
## Suche funktioniert nicht in Windows Server 2008, Windows Server 2008 mit SP1 oder Windows Server 2008 R2.  
 Für die Such\- und Filterfunktionen in Help Viewer muss der Dienst Windows Search installiert und verfügbar sein.  Standardmäßig ist dieser Dienst in Windows Server 2008, Windows Server 2008 mit Service Pack 1 \(SP1\) und Windows Server 2008 R2 deaktiviert.  
  
#### So aktivieren Sie den Windows Search\-Dienst  
  
1.  Starten Sie den Server\-Manager.  
  
2.  Wählen Sie im linken Navigationsbereich **Rollen** aus.  
  
3.  Wählen Sie im Bereich "Rollenübersicht" die Option **Rolle hinzufügen** aus.  
  
4.  Wählen Sie die Rolle "Dateidienste" aus, und klicken Sie dann auf die Schaltfläche **Weiter**.  
  
5.  Wählen Sie den Windows Search\-Rollendienst aus.  
  
## Zusätzliche Ressourcen  
 Mithilfe der folgenden Ressourcen können Sie weitere Informationen abrufen und Feedback zum Help Viewer bereitstellen:  
  
-   Informationen zu Feedback finden Sie unter [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) auf der Microsoft\-Website, oder Sie senden eine E\-Mail an [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).  
  
-   Weitere Informationen finden Sie im Forum des [Entwicklerdokumentations\- und \-hilfesystems](http://go.microsoft.com/fwlink/?LinkId=232741) und im Blog [The Help Guy](http://go.microsoft.com/fwlink/?LinkId=232743).  
  
## Siehe auch  
 [Help Viewer 2.1\-Administratorhandbuch](http://go.microsoft.com/fwlink/?LinkId=243985)