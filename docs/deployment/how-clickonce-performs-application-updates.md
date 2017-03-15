---
title: "How ClickOnce Performs Application Updates | Microsoft Docs"
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
  - "updates, ClickOnce"
  - "ClickOnce deployment, updates"
  - "deploying applications [ClickOnce], application updates"
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# How ClickOnce Performs Application Updates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce entscheidet anhand der Dateiversionsinformationen, die im Bereitstellungsmanifest einer Anwendung angegeben sind, ob die Dateien der Anwendung aktualisiert werden.  Nach Beginn eines Updates verwendet ClickOnce eine als *Patchen von Dateien* bezeichnete Methode, um das redundante Herunterladen von Dateien zu verhindern.  
  
## Patchen von Dateien  
 Bei der Aktualisierung einer Anwendung lädt ClickOnce nicht alle Dateien für die neue Version der Anwendung herunter, sofern die Dateien sich nicht geändert haben.  Stattdessen werden die Hashsignaturen der Dateien, die im Anwendungsmanifest für die aktuelle Anwendung angegeben sind, mit den Signaturen im Manifest für die neue Version verglichen.  Wenn eine Datei verschiedene Signaturen aufweist, lädt ClickOnce die neue Version herunter.  Wenn die Signaturen sich entsprechen, wurde die Datei für die nächste Version nicht geändert.  In diesem Fall kopiert ClickOnce die vorhandene Datei und verwendet sie in der neuen Version der Anwendung.  Dieser Ansatz verhindert, dass ClickOnce auch dann die gesamte Anwendung erneut herunterladen muss, wenn sich nur eine oder zwei Dateien geändert haben.  
  
 Das Patchen von Dateien funktioniert auch für Assemblys, die bei Bedarf mit der <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A>\-Methode und der <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A>\-Methode heruntergeladen werden.  
  
 Wenn Sie Ihre Anwendung mit Visual Studio kompilieren, werden immer dann, wenn Sie das gesamte Projekt neu erstellen, neue Hashsignaturen für alle Dateien generiert.  In diesem Fall werden alle Assemblys auf den Client heruntergeladen, auch wenn sich möglicherweise nur wenige Assemblys geändert haben.  
  
 Das Patchen von Dateien funktioniert nicht für Dateien, die als Daten gekennzeichnet sind und im Datenverzeichnis gespeichert werden.  Sie werden immer unabhängig von der Hashsignatur der Datei heruntergeladen.  Weitere Informationen zum Datenverzeichnis finden Sie unter [Zugreifen auf lokale und Remotedaten in einer ClickOnce\-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## Siehe auch  
 [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md)