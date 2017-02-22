---
title: "Gewusst wie: Debuggen einer ClickOnce-Anwendung mit eingeschr&#228;nkten Berechtigungen | Microsoft Docs"
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
  - "Debuggen [Visual Studio], ClickOnce-Anwendungen"
  - "ClickOnce-Bereitstellung, Debuggen"
  - "ClickOnce-Anwendungen, Debuggen"
ms.assetid: 6991ea91-5253-451b-923d-22273a3d38b1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gewusst wie: Debuggen einer ClickOnce-Anwendung mit eingeschr&#228;nkten Berechtigungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Als Entwickler führen Sie wahrscheinlich Ihre Entwicklungscomputer mit der Berechtigungen „Voll vertrauenswürdig“ aus, daher werden Sie nicht die gleichen Sicherheitsausnahmen beim Debuggen einer ClickOnce\-Anwendung sehen, die der Endbenutzer möglicherweise sieht, wenn sie mit eingeschränkten Berechtigungen ausgeführt wird.  
  
 Um diese Ausnahmen zu erfassen, müssen Sie die Anwendung mit genau den Berechtigungen debuggen, die ein Endbenutzer hat. Debuggen mit eingeschränkten Berechtigungen kann im **Projekt\-Designer** auf der Seite **Sicherheit** aktiviert werden.  
  
 Wenn Sie darüber hinaus Anwendungen entwickeln, die Webdienste aufrufen, befinden sich diese Webdienste häufig auf Ihrem Entwicklungscomputer. Nach der Bereitstellung greift der Endbenutzer auf diese Webdienste von einer anderen URL aus zu. Zum Emulieren der Endbenutzererfahrung während des Debuggens können Sie eine URL angeben, und der Debugger wird die Webdienste daraufhin so behandeln, als würden Sie von dieser URL aufgerufen werden.  
  
### So aktivieren Sie das Debuggen mit eingeschränkten Berechtigungen  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen\-Explorer** im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie im **Projekt\-Designer** auf die Registerkarte **Sicherheit**.  
  
3.  Wählen Sie das Kontrollkästchen **Enable ClickOnce Security Setting** \(ClickOnce\-Sicherheitseinstellung aktivieren\) aus, und klicken Sie dann auf das Optionsfeld **Teilweise vertrauenswürdige Anwendung**.  
  
4.  Klicken Sie auf die Schaltfläche **Erweitert**.  
  
5.  Wählen Sie das Kontrollkästchen **Diese Anwendung mit dem ausgewählten Berechtigungssatz &debuggen** aus, und klicken Sie dann auf **OK**.  
  
     Wenn Sie die Anwendung debuggen, lösen alle Zugriffsversuche auf eine Berechtigung, die nicht Teil des Berechtigungssatzes ist, eine Sicherheitsausnahme aus.  
  
### So geben Sie eine URL für das Debuggen an  
  
1.  Klicken Sie bei ausgewähltem Projekt im **Projektmappen\-Explorer** im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie im **Projekt\-Designer** auf die Registerkarte **Sicherheit**.  
  
3.  Wählen Sie das Kontrollkästchen **Enable ClickOnce Security Setting** \(ClickOnce\-Sicherheitseinstellung aktivieren\) aus, und klicken Sie dann auf das Optionsfeld **Teilweise vertrauenswürdige Anwendung**.  
  
4.  Klicken Sie auf die Schaltfläche **Erweitert**.  
  
5.  Wählen Sie das Kontrollkästchen **Diese Anwendung mit dem ausgewählten Berechtigungssatz &debuggen** aus, und klicken Sie dann auf **OK**.  
  
6.  Geben Sie im Textfeld **Diese Anwendung debuggen, als ob sie von folgender URL heruntergeladen würde:** eine URL oder einen Netzwerkpfad ein.  
  
## Siehe auch  
 [Gewusst wie: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce\-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Codezugriffssicherheit für ClickOnce\-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)   
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)