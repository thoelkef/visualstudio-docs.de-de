---
title: "Vorbedingungen für die Anwendungsbereitstellung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
caps.latest.revision: "51"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: c323e3800e98e2451a371f3ff84b3351d760a94c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="application-deployment-prerequisites"></a>Vorbedingungen für die Anwendungsbereitstellung
Damit die Anwendung erfolgreich installiert und ausgeführt werden kann, müssen Sie zuerst sicherstellen, dass alle für die Anwendung erforderlichen Komponenten bereits auf dem Zielcomputer installiert sind. Beispielsweise hängen die meisten Anwendungen, die mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt werden, von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ab. Die richtige Version von Common Language Runtime muss auf dem Zielcomputer verfügbar sein, bevor die Anwendung installiert wird.  
  
 Sie können diese erforderlichen Komponenten im Auswählen der **Voraussetzungen (Dialogfeld)** und installieren Sie .NET Framework sowie andere verteilbare Komponenten im Rahmen der Installation. Dieses Vorgehen wird als bezeichnet *bootstrapping*. Als Nächstes [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert ein ausführbares Windows-Programm, mit dem Namen Setup.exe, auch bekannt als ein *Bootstrapper*. Der Bootstrapper installiert diese erforderlichen Komponenten, bevor die Anwendung ausgeführt wird. Weitere Informationen zum Auswählen der erforderlichen Komponenten finden Sie unter [Dialogfeld erforderliche](../ide/reference/prerequisites-dialog-box.md).  
  
 Jede erforderliche Komponente ist ein Bootstrapperpaket. Bei einem Bootstrapperpaket handelt es sich um eine Gruppe von Verzeichnissen und Dateien, die Manifestdateien enthalten, mit denen beschrieben wird, wie die erforderliche Komponente installiert werden muss. Wenn Ihre Anwendung erforderlichen Komponenten nicht aufgeführt sind die **erforderliche Dialogfeld**, können Sie benutzerdefinierte Bootstrapperpakete erstellen und sie zu Visual Studio hinzufügen. Dann Sie die erforderlichen Komponenten im wählen die **Dialogfeld erforderliche**. Weitere Informationen finden Sie unter [Bootstrapperpakete erstellen](../deployment/creating-bootstrapper-packages.md).  
  
 Standardmäßig ist Bootstrapping für die ClickOnce-Bereitstellung aktiviert. Der für die ClickOnce-Bereitstellung generierte Bootstrapper ist signiert. Sie können Bootstrapping für eine Komponente deaktivieren, Sie sollten dies aber nur tun, wenn Sie sicher sind, dass die richtige Version der Komponente bereits auf allen Zielcomputern installiert ist.  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>Bootstrapping und ClickOnce-Bereitstellung  
 Vor der Installation einer Anwendung auf einem Clientcomputer untersucht [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] den Client, um sicherzustellen, dass bestimmte im Anwendungsmanifest angegebene Anforderungen erfüllt werden. Hierzu gehört Folgendes:  
  
-   Die mindestens erforderliche Version von Common Language Runtime, die als Assemblyabhängigkeit im Anwendungsmanifest angegeben ist.  
  
-   Die für die Anwendung mindestens erforderliche Version des Windows-Betriebssystems, wie im Anwendungsmanifest mit dem `<osVersionInfo>`-Element angegeben. (Siehe [ \<Dependency >-Element](../deployment/dependency-element-clickonce-application.md))  
  
-   Die Mindestversion aller Assemblys, die im globalen Assemblycache (GAC) vorinstalliert sein müssen, wie von Deklarationen der Assemblyabhängigkeiten im Assemblymanifest angegeben.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kann fehlende erforderliche Komponenten bestimmen, und Sie können erforderliche Komponenten mit einem Bootstrapper installieren. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren der erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
> [!NOTE]
>  Um die Werte in den Manifesten zu ändern, die von Tools wie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und "MageUI.exe" generiert wurden, müssen Sie das Anwendungsmanifest in einem Text-Editor bearbeiten. Signieren Sie anschließend die Anwendungs- und Bereitstellungsmanifeste erneut. Weitere Informationen finden Sie unter [wie: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifeste](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
 Wenn Sie Visual Studio und ClickOnce für die Bereitstellung der Anwendung verwenden, hängen die standardmäßig ausgewählten Bootstrapperpakete von der .NET Framework-Version in der Projektmappe ab. Jedoch wenn Sie .NET Framework-Zielversion ändern, Sie müssen die Optionen aktualisieren in der **Dialogfeld erforderliche** manuell.  
  
|.NET Framework-Zielversion|Ausgewählte Bootstrapperpakete|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  
  
 Bei der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Bereitstellung verweist die Seite "Publish.htm", die vom [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Webpublishing-Assistenten generiert wird, auf einen Link, mit dem nur die Anwendung installiert wird, oder auf einen Link, mit dem die Anwendung und die Bootstrappingkomponenten installiert werden.  
  
 Wenn Sie den Bootstrapper mit dem ClickOnce-Webpublishing-Assistenten oder der Seite "Veröffentlichen" in Visual Studio generieren, wird "Setup.exe" automatisch signiert. Wenn Sie jedoch das Zertifikat des Kunden zum Signieren des Bootstrappers verwenden möchten, können Sie die Datei später signieren.  
  
## <a name="bootstrapping-and-msbuild"></a>Bootstrapping und MSBuild  
 Wenn Sie nicht [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verwenden, sondern die Anwendungen über die Befehlszeile kompilieren, können Sie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Bootstrappinganwendung mit einer Microsoft Build Engine-Aufgabe (MSBuild) erstellen. Weitere Informationen finden Sie unter [GenerateBootstrapper-Aufgabe](../msbuild/generatebootstrapper-task.md).  
  
 Als Alternative zum Bootstrapping können Sie Komponenten mit einem elektronischen Softwareverteilungssystem wie Microsoft Systems Management Server (SMS) vorab bereitstellen.  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>Bootstrapper-Befehlszeilenargumente ("Setup.exe")  
 Die von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generierte "Setup.exe" und die MSBuild-Aufgaben unterstützen den folgenden kleinen Satz von Befehlszeilenargumenten. Alle Argumente, die darüber hinaus in der Bootstrappinganwendung bereitgestellt werden, werden an das Installationsprogramm der Anwendung weitergeleitet.  
  
 Wenn Sie Bootstrapperoptionen ändern, müssen Sie den nicht signierten Bootstrapper ändern und die Bootstrapperdatei später signieren.  
  
|Befehlszeilenargument|Beschreibung|  
|---------------------------|-----------------|  
|**-?, -h, -Hilfe**|Zeigt das Dialogfeld der Hilfe an.|  
|**-Url - Komponenten-URL**|Zeigt die gespeicherte URL und Komponenten-URLs für diese Installation an.|  
|**-Url =**`location`|Legt die URL fest, bei der "Setup.exe" nach der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Anwendung sucht.|  
|**Komponenten-URL-=**`location`|Legt die URL fest, bei der "Setup.exe" nach Abhängigkeiten wie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sucht.|  
|**-Homesite =** `true` **&#124;**`false`|Wenn `true`, werden die Abhängigkeiten vom bevorzugten Speicherort auf der Website des Anbieters heruntergeladen. Dies überschreibt die **- Komponenten-URL** Einstellung. Wenn `false`, die Abhängigkeiten von der vom angegebenen URL heruntergeladen **- Komponenten-URL**.|  
  
## <a name="operating-system-support"></a>Unterstützte Betriebssysteme  
 Windows Server 2008 Server Core oder Windows Server 2008 R2 Server Core bieten eine wartungsarme Serverumgebung mit beschränktem Funktionsumfang und unterstützen den Visual Studio-Bootstrapper nicht. Die Server Core-Installationsoption unterstützt beispielsweise nur das Profil .NET Framework 3.5 Server Core. Visual Studio-Funktionen, die auf das vollständige .NET Framework angewiesen sind, können daher nicht ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce-Sicherheit und Bereitstellung](../deployment/clickonce-security-and-deployment.md)