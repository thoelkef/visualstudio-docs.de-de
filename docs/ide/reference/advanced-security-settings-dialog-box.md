---
title: "Dialogfeld &quot;Erweiterte Sicherheitseinstellungen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.err.debug_in_zone_no_hostproc"
  - "vs.err.debug_in_zone_no_hostproc:11310"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Erweiterte Sicherheitseinstellungen (Dialogfeld)"
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Dialogfeld &quot;Erweiterte Sicherheitseinstellungen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In diesem Dialogfeld können Sie Sicherheitseinstellungen für das Debuggen in einer Zone angeben.  
  
 Wählen Sie zum Aufrufen des Dialogfelds einen Projektknoten im **Projektmappen\-Explorer** aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**.  Sobald der **Projekt\-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Sicherheit**.  Wählen Sie auf der Seite **Sicherheit** die Option **ClickOnce\-Sicherheitseinstellungen aktivieren** aus, klicken Sie auf **Teilweise vertrauenswürdige Anwendung** und anschließend auf **Erweitert**.  
  
## UIElement-Liste  
 **Diese Anwendung mit dem ausgewählten Berechtigungssatz debuggen**  
 Wenn Sie dieses Kontrollkästchen aktivieren, wird während des Debugvorgangs der auf der Seite **Sicherheit** ausgewählte Berechtigungssatz verwendet.  Diese Option ist standardmäßig ausgewählt.  
  
 Damit das Debuggen in einer Sicherheitszone funktioniert, muss diese Option wie auch die Option **Visual Studio\-Hostprozess aktivieren** \(verfügbar auf der Seite **Debuggen** des **Projekt\-Designers**\) aktiviert sein.  
  
 Für WPF\-Webbrowseranwendungsprojekte ist das Kontrollkästchen **Diese Anwendung mit dem ausgewählten Berechtigungssatz debuggen** ausgewählt und deaktiviert.  
  
 **Der Anwendung Zugriff auf die Ursprungssite gewähren**  
 Wenn Sie dieses Kontrollkästchen aktivieren, kann die Anwendung auf die Website oder Serverfreigabe zugreifen, auf der sie veröffentlicht ist.  Diese Option ist standardmäßig ausgewählt.  
  
 **Diese Anwendung debuggen, als ob sie von folgender URL heruntergeladen würde**  
 Um der Anwendung den Zugriff auf die Website oder Serverfreigabe zu ermöglichen, die der auf der Seite **Veröffentlichen** angegebenen **Installations\-URL** entspricht, geben Sie diese URL hier ein.  Diese Option ist nur verfügbar, wenn **Der Anwendung Zugriff auf die Ursprungssite gewähren** ausgewählt wird.  
  
## Siehe auch  
 [Seite "Sicherheit", Projekt\-Designer](../../ide/reference/security-page-project-designer.md)