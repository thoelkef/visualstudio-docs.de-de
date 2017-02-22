---
title: "How to: Manage Updates for a ClickOnce Application | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, managing applications"
  - "ClickOnce deployment, updates"
  - "updating data, ClickOnce"
  - "application updates"
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Manage Updates for a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen können automatisch oder programmgesteuert nach Updates suchen.  Als Entwickler können Sie außerordentlich flexibel festlegen, wann und wie nach Updates gesucht werden soll, ob Updates obligatorisch installiert werden sollen und wo die Anwendung nach Updates suchen soll.  
  
 Sie können die Anwendung so konfigurieren, dass sie automatisch vor dem Starten oder in festgelegten Intervallen nach dem Starten nach Updates suchen soll.  Darüber hinaus können Sie eine mindestens erforderliche Version angeben, sodass ein Update installiert wird, wenn die verwendete Version älter ist als die erforderliche Version.  
  
 Sie können die Anwendung so konfigurieren, dass Updates programmgesteuert auf Basis von Ereignissen wie Benutzeranforderungen gesucht werden.  Im Abschnitt "So werden Updates programmgesteuert gesucht" weiter unten in diesem Thema wird gezeigt, wie Sie Code erstellen, der mithilfe der <xref:System.Deployment.Application.ApplicationDeployment>\-Klasse Updates ereignisgesteuert sucht.  
  
 Sie können die Anwendung auch von einem Speicherort aus bereitstellen und von einem anderen aus aktualisieren.  Informationen zu dieser Vorgehensweise finden Sie unter "So legen Sie einen anderen Updatepfad fest".  
  
 Weitere Informationen finden Sie unter [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Das Updateverhalten wird im **Projekt\-Designer** auf der Seite **Veröffentlichen** im Dialogfeld **Anwendungsupdates** verwaltet.  
  
### So wird eine Überprüfung vor dem Start der Anwendung ausgeführt  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die Schaltfläche **Updates**, um das Dialogfeld **Anwendungsupdates** zu öffnen.  
  
4.  Stellen Sie sicher, dass im Dialogfeld **Anwendungsupdates** das Kontrollkästchen **Die Anwendung soll nach Updates suchen** aktiviert ist.  
  
5.  Wählen Sie im Bereich **Zeitpunkt auswählen, wann die Anwendung auf Updates überprüfen soll** die Option **Vor Start der Anwendung** aus.  Dadurch stellen Sie sicher, dass mit dem Netzwerk verbundene Benutzer die Anwendung mit den neuesten Updates ausführen.  
  
### So wird eine Überprüfung vor dem Start der Anwendung im Hintergrund ausgeführt  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die Schaltfläche **Updates**, um das Dialogfeld **Anwendungsupdates** zu öffnen.  
  
4.  Stellen Sie sicher, dass im Dialogfeld **Anwendungsupdates** das Kontrollkästchen **Die Anwendung soll nach Updates suchen** aktiviert ist.  
  
5.  Wählen Sie im Bereich **Zeitpunkt auswählen, wann die Anwendung auf Updates überprüfen soll** die Option **Nach dem Starten der Anwendung** aus.  Die Anwendung startet auf diese Weise schneller, sucht im Hintergrund nach Updates und benachrichtigt den Benutzer nur dann, wenn ein Update verfügbar ist.  Nach der Installation des Updates werden die Änderungen erst nach einem Neustart der Anwendung übernommen.  
  
6.  Wählen Sie im Bereich **Häufigkeit der Überprüfung auf Updates angeben** entweder **Bei jedem Ausführen der Anwendung überprüfen** \(was die Standardeinstellung ist\) oder **Überprüfung alle:** aus, und geben Sie eine Zahl und ein Zeitintervall ein.  
  
### So legen Sie eine mindestens erforderliche Version für die Anwendung fest  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die Schaltfläche **Updates**, um das Dialogfeld **Anwendungsupdates** zu öffnen.  
  
4.  Stellen Sie sicher, dass im Dialogfeld **Anwendungsupdates** das Kontrollkästchen **Die Anwendung soll nach Updates suchen** aktiviert ist.  
  
5.  Aktivieren Sie das Kontrollkästchen **Geben Sie die mindestens erforderliche Version für diese Anwendung an**, und geben Sie dann die Versionsziffern für **Hauptversion**, **Nebenversion**, **Build** und **Revision** für die Anwendung ein.  
  
### So legen Sie einen anderen Updatepfad fest  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die Schaltfläche **Updates**, um das Dialogfeld **Anwendungsupdates** zu öffnen.  
  
4.  Stellen Sie sicher, dass im Dialogfeld **Anwendungsupdates** das Kontrollkästchen **Die Anwendung soll nach Updates suchen** aktiviert ist.  
  
5.  Geben Sie im Feld **Updatepfad** mit einer vollqualifizierten URL den Updatepfad im Format http:\/\/Hostname\/Anwendungsname ein, oder verwenden Sie einen UNC\-Pfad im Format \\\\Server\\\\Anwendungsname. Sie können auch auf die Schaltfläche **Durchsuchen** klicken, um den Updatepfad zu suchen.  
  
### So werden Updates programmgesteuert gesucht  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
3.  Klicken Sie auf die Schaltfläche **Updates**, um das Dialogfeld **Anwendungsupdates** zu öffnen.  
  
4.  Stellen Sie sicher, dass im Dialogfeld **Anwendungsupdates** das Kontrollkästchen **Die Anwendung soll nach Updates suchen** deaktiviert ist.  \(Optional können Sie dieses Kontrollkästchen aktivieren, um programmgesteuert nach Updates zu suchen und mit der ClickOnce\-Laufzeit eine automatische Updateüberprüfung vorzunehmen.\)  
  
5.  Geben Sie im Feld **Updatepfad** mit einer vollqualifizierten URL den Updatepfad im Format http:\/\/Hostname\/Anwendungsname ein, oder verwenden Sie einen UNC\-Pfad im Format \\\\Server\\\\Anwendungsname. Sie können auch auf die Schaltfläche **Durchsuchen** klicken, um den Updatepfad zu suchen.  Im Updatepfad sucht die Anwendung nach einer aktualisierten Version.  
  
6.  Erstellen Sie eine Schaltfläche, ein Menüelement oder ein anderes Benutzeroberflächenelement auf einem Windows Form, das Benutzer für die Updateüberprüfung auswählen.  Rufen Sie vom Ereignishandler dieses Elements eine Methode auf, um nach Updates zu suchen und sie zu installieren.  Ein Beispiel für einen Visual Basic\- und Visual C\#\-Code für eine solche Methode finden Sie unter [How to: Check for Application Updates Programmatically Using the ClickOnce Deployment API](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7.  Erstellen Sie die Anwendung.  
  
## Siehe auch  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Application Updates Dialog Box](http://msdn.microsoft.com/de-de/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [How to: Check for Application Updates Programmatically Using the ClickOnce Deployment API](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)