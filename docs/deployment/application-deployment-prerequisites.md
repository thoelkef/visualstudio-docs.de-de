---
title: "Vorbedingungen f&#252;r die Anwendungsbereitstellung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce-Bereitstellung, Abhängigkeiten"
  - "ClickOnce-Bereitstellung, Plattformerkennung"
  - "ClickOnce-Bereitstellung, Voraussetzungen"
  - "Abhängigkeiten, ClickOnce"
  - "Voraussetzungen, ClickOnce"
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
caps.latest.revision: 51
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 51
---
# Vorbedingungen f&#252;r die Anwendungsbereitstellung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Damit die Anwendung erfolgreich installiert und ausgeführt werden kann, müssen Sie zuerst sicherstellen, dass alle für die Anwendung erforderlichen Komponenten bereits auf dem Zielcomputer installiert sind. Beispielsweise hängen die meisten Anwendungen, die mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt werden, von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ab. Die richtige Version von Common Language Runtime muss auf dem Zielcomputer verfügbar sein, bevor die Anwendung installiert wird.  
  
 Sie können diese erforderlichen Komponenten im Dialogfeld **Erforderliche Komponenten** auswählen und .NET Framework sowie andere verteilbare Komponenten im Rahmen der Installation installieren. Dieses Vorgehen wird als *Bootstrapping* bezeichnet. Anschließend generiert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ein ausführbares Windows\-Programm mit dem Namen "Setup.exe", das auch *Bootstrapper* genannt wird. Der Bootstrapper installiert diese erforderlichen Komponenten, bevor die Anwendung ausgeführt wird. Weitere Informationen zum Auswählen der erforderlichen Komponenten finden Sie unter [Dialogfeld "Erforderliche Komponenten"](../ide/reference/prerequisites-dialog-box.md).  
  
 Jede erforderliche Komponente ist ein Bootstrapperpaket. Bei einem Bootstrapperpaket handelt es sich um eine Gruppe von Verzeichnissen und Dateien, die Manifestdateien enthalten, mit denen beschrieben wird, wie die erforderliche Komponente installiert werden muss. Wenn die erforderlichen Komponenten für die Anwendung nicht im Dialogfeld **Erforderliche Komponenten** aufgeführt sind, können Sie benutzerdefinierte Bootstrapperpakete erstellen und Visual Studio hinzufügen. Dann können Sie die erforderlichen Komponenten im Dialogfeld **Erforderliche Komponenten** auswählen. Weitere Informationen finden Sie unter [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md).  
  
 Standardmäßig ist Bootstrapping für die ClickOnce\-Bereitstellung aktiviert. Der für die ClickOnce\-Bereitstellung generierte Bootstrapper ist signiert. Sie können Bootstrapping für eine Komponente deaktivieren, Sie sollten dies aber nur tun, wenn Sie sicher sind, dass die richtige Version der Komponente bereits auf allen Zielcomputern installiert ist.  
  
## Bootstrapping und ClickOnce\-Bereitstellung  
 Vor der Installation einer Anwendung auf einem Clientcomputer untersucht [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] den Client, um sicherzustellen, dass bestimmte im Anwendungsmanifest angegebene Anforderungen erfüllt werden. Hierzu gehört Folgendes:  
  
-   Die mindestens erforderliche Version von Common Language Runtime, die als Assemblyabhängigkeit im Anwendungsmanifest angegeben ist.  
  
-   Die für die Anwendung mindestens erforderliche Version des Windows\-Betriebssystems, wie im Anwendungsmanifest mit dem `<osVersionInfo>`\-Element angegeben. \(Siehe [\<dependency\> Element](../deployment/dependency-element-clickonce-application.md)\)  
  
-   Die Mindestversion aller Assemblys, die im globalen Assemblycache \(GAC\) vorinstalliert sein müssen, wie von Deklarationen der Assemblyabhängigkeiten im Assemblymanifest angegeben.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kann fehlende erforderliche Komponenten bestimmen, und Sie können erforderliche Komponenten mit einem Bootstrapper installieren. Weitere Informationen finden Sie unter [How to: Install Prerequisites with a ClickOnce Application](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
> [!NOTE]
>  Um die Werte in den Manifesten zu ändern, die von Tools wie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und "MageUI.exe" generiert wurden, müssen Sie das Anwendungsmanifest in einem Text\-Editor bearbeiten. Signieren Sie anschließend die Anwendungs\- und Bereitstellungsmanifeste erneut. Weitere Informationen finden Sie unter [How to: Re\-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
 Wenn Sie Visual Studio und ClickOnce für die Bereitstellung der Anwendung verwenden, hängen die standardmäßig ausgewählten Bootstrapperpakete von der .NET Framework\-Version in der Projektmappe ab. Wenn Sie jedoch die .NET Framework\-Zielversion ändern, müssen Sie die Optionen im Dialogfeld **Erforderliche Komponenten** manuell aktualisieren.  
  
|.NET Framework\-Zielversion|Ausgewählte Bootstrapperpakete|  
|---------------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  
  
 Bei der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung verweist die Seite "Publish.htm", die vom [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Webpublishing\-Assistenten generiert wird, auf einen Link, mit dem nur die Anwendung installiert wird, oder auf einen Link, mit dem die Anwendung und die Bootstrappingkomponenten installiert werden.  
  
 Wenn Sie den Bootstrapper mit dem ClickOnce\-Webpublishing\-Assistenten oder der Seite "Veröffentlichen" in Visual Studio generieren, wird "Setup.exe" automatisch signiert. Wenn Sie jedoch das Zertifikat des Kunden zum Signieren des Bootstrappers verwenden möchten, können Sie die Datei später signieren.  
  
## Bootstrapping und MSBuild  
 Wenn Sie nicht [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verwenden, sondern die Anwendungen über die Befehlszeile kompilieren, können Sie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bootstrappinganwendung mit einer Microsoft Build Engine\-Aufgabe \(MSBuild\) erstellen. Weitere Informationen finden Sie unter [GenerateBootstrapper Task](../msbuild/generatebootstrapper-task.md).  
  
 Als Alternative zum Bootstrapping können Sie Komponenten mit einem elektronischen Softwareverteilungssystem wie Microsoft Systems Management Server \(SMS\) vorab bereitstellen.  
  
## Bootstrapper\-Befehlszeilenargumente \("Setup.exe"\)  
 Die von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generierte "Setup.exe" und die MSBuild\-Aufgaben unterstützen den folgenden kleinen Satz von Befehlszeilenargumenten. Alle Argumente, die darüber hinaus in der Bootstrappinganwendung bereitgestellt werden, werden an das Installationsprogramm der Anwendung weitergeleitet.  
  
 Wenn Sie Bootstrapperoptionen ändern, müssen Sie den nicht signierten Bootstrapper ändern und die Bootstrapperdatei später signieren.  
  
|Befehlszeilenargument|Beschreibung|  
|---------------------------|------------------|  
|**\-?, \-h, \-help**|Zeigt das Dialogfeld der Hilfe an.|  
|**\-url, \-componentsurl**|Zeigt die gespeicherte URL und Komponenten\-URLs für diese Installation an.|  
|**\-url\=** `location`|Legt die URL fest, bei der "Setup.exe" nach der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung sucht.|  
|**\-componentsurl\=** `location`|Legt die URL fest, bei der "Setup.exe" nach Abhängigkeiten wie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sucht.|  
|**\-homesite\=** `true` **&#124;**  `false`|Bei `true` werden die Abhängigkeiten vom bevorzugten Speicherort auf der Website des Anbieters heruntergeladen. Dies überschreibt die Einstellung **\-componentsurl**. Bei `false` werden die Abhängigkeiten von der mit **\-componentsurl** angegebenen URL heruntergeladen.|  
  
## Unterstützte Betriebssysteme  
 Windows Server 2008 Server Core oder Windows Server 2008 R2 Server Core bieten eine wartungsarme Serverumgebung mit beschränktem Funktionsumfang und unterstützen den Visual Studio\-Bootstrapper nicht. Die Server Core\-Installationsoption unterstützt beispielsweise nur das Profil .NET Framework 3.5 Server Core. Visual Studio\-Funktionen, die auf das vollständige .NET Framework angewiesen sind, können daher nicht ausgeführt werden.  
  
## Siehe auch  
 [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)