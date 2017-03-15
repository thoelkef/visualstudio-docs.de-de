---
title: "How to: Specify an Alternate Location for Deployment Updates | Microsoft Docs"
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
  - "ClickOnce deployment, updates"
  - "deployment update, alternative locations"
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# How to: Specify an Alternate Location for Deployment Updates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung zunächst von einer CD oder Dateifreigabe installieren, anschließend muss die Anwendung jedoch regelmäßig im Web nach Updates suchen.  Sie können im Bereitstellungsmanifest einen anderen Speicherort für Updates angeben, sodass die Anwendung nach der ersten Installation automatisch über das Web aktualisiert werden kann.  
  
> [!NOTE]
>  Dieses Feature kann nur verwendet werden, wenn die Anwendung für die lokale Installation konfiguriert ist.  Weitere Informationen finden Sie unter [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Wenn Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung über das Netzwerk installieren, bewirkt das Festlegen eines anderen Speicherorts, dass [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] diesen Speicherort sowohl für die erste Installation als auch für alle späteren Updates verwendet.  Installieren Sie die Anwendung hingegen lokal \(z. B. von einer CD\), erfolgt die erste Installation vom Originaldatenträger, während für alle späteren Updates der andere Speicherort verwendet wird.  
  
### Angeben eines anderen Speicherorts für Updates mit MageUI.exe \(einem Windows Forms\-basierten Dienstprogramm\)  
  
1.  Öffnen Sie eine .NET Framework\-Eingabeaufforderung, und geben Sie Folgendes ein:  
  
     **mageui.exe**  
  
2.  Wählen Sie im Menü **Datei** die Option **Öffnen** aus, um das Bereitstellungsmanifest der Anwendung zu öffnen.  
  
3.  Wählen Sie die Registerkarte **Bereitstellungsoptionen** aus.  
  
4.  Geben Sie im Textfeld **Startspeicherort** die URL des Verzeichnisses ein, das das Bereitstellungsmanifest für Anwendungsupdates enthalten soll.  
  
5.  Speichern Sie das Bereitstellungsmanifest.  
  
### Angeben eines anderen Speicherorts für Updates mit Mage.exe  
  
1.  Öffnen Sie eine .NET Framework\-Eingabeaufforderung.  
  
2.  Legen Sie den Updatepfad mit dem folgenden Befehl fest.  In diesem Beispiel ist **HelloWorld.exe.application** der Pfad zum Anwendungsmanifest von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], das immer die Erweiterung .application aufweist. **http:\/\/adatum.com\/Update\/Path** ist die URL, unter der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nach Anwendungsupdates sucht.  
  
     **Mage \-Update HelloWorld.exe.application \-ProviderUrl http:\/\/adatum.com\/Update\/Path**  
  
3.  Speichern Sie die Datei.  
  
    > [!NOTE]
    >  Sie müssen die Datei mit "Mage.exe" jetzt neu signieren.  Weitere Informationen finden Sie unter [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## .NET Framework-Sicherheit  
 Wenn Sie die Anwendung von einem Offlinemedium wie einer CD installieren und der Computer online ist, überprüft [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zunächst unter der vom `<deploymentProvider>`\-Tag im Bereitstellungsmanifest angegebenen URL, ob der Updatepfad eine neuere Anwendungsversion enthält.  Wenn dies der Fall ist, installiert [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] die Anwendung nicht aus dem ursprünglichen Installationsverzeichnis, sondern direkt aus diesem Pfad, und die Common Language Runtime \(CLR\) ermittelt mit `<deploymentProvider>` die Vertrauensebene der Anwendung.  Wenn der Computer offline oder `<deploymentProvider>` nicht erreichbar ist, wird [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] von der CD installiert, und die CLR gewährt Vertrauenswürdigkeit je nach dem Installationspfad. Bei einer Installation von CD bedeutet dies, dass die Anwendung als voll vertrauenswürdig eingestuft wird.  Alle nachfolgenden Updates erben diese Vertrauensebene.  
  
 Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen, die `<deploymentProvider>` verwenden, sollten die erforderlichen Berechtigungen explizit im Anwendungsmanifest deklarieren. So kann verhindert werden, dass der Anwendung auf verschiedenen Computern unterschiedliche Vertrauensebenen zugewiesen werden.  
  
## Siehe auch  
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md)