---
title: Vorbedingungen für die Anwendungsbereitstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 58f9de8e5b2a5f0f774bbf6f23df544bb24b2846
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081321"
---
# <a name="application-deployment-prerequisites"></a>Vorbedingungen für die anwendungsbereitstellung

Damit Ihre Anwendung erfolgreich installiert und ausgeführt, müssen Sie zunächst installieren Sie alle Komponenten, von denen Ihre Anwendung abhängig ist, auf dem Zielcomputer ist. Z. B. die meisten Anwendungen, die mit erstellt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hängen die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Die richtige Version der common Language Runtime muss in diesem Fall auf dem Zielcomputer vorhanden sein, bevor die Anwendung installiert wird.  
  
 Sie können auswählen, wenn diese Voraussetzungen sind die **Prerequisites Dialog Box** herunter, und Installieren von .NET Framework und alle anderen Redistributable-Komponente als Teil der Installation. Diese Vorgehensweise heißt *bootstrapping*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert ein ausführbares Windows-Programm, mit dem Namen *Setup.exe*, auch bekannt als eine *Bootstrapper*. Der Bootstrapper installiert diese erforderlichen Komponenten, bevor die Anwendung ausgeführt wird. Weitere Informationen zum Auswählen der erforderlichen Komponenten finden Sie unter [erforderliche](../ide/reference/prerequisites-dialog-box.md).  
  
 Jede erforderliche Komponente ist ein Bootstrapperpaket. Eine Bootstrapper-Paket ist eine Gruppe von Verzeichnissen und Dateien, die mit dem Manifesten-Dateien, die beschreiben, wie die erforderlichen Komponenten installiert werden. Wenn Ihre Anwendung erforderlichen Komponenten nicht aufgeführt sind die **erforderliche Dialogfeld**, können Sie benutzerdefinierte Bootstrapperpakete erstellen und sie zu Visual Studio hinzufügen. Dann können Sie die Voraussetzungen in der **Prerequisites Dialog Box**. Weitere Informationen finden Sie unter [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md).  
  
 Standardmäßig ist Bootstrapping für die ClickOnce-Bereitstellung aktiviert. Der für die ClickOnce-Bereitstellung generierte Bootstrapper ist signiert. Sie können bootstrapping für eine Komponente deaktivieren, aber nur, wenn Sie sicher sind, ist die richtige Version der Komponente bereits auf allen Zielcomputern installiert.  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>Bootstrapping und ClickOnce-Bereitstellung  
 Vor der Installation einer Anwendung auf einem Clientcomputer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] überprüft den Client, um sicherzustellen, dass es sich um die Anforderungen, die im Anwendungsmanifest angegeben hat. Dazu gehören die folgenden Anforderungen:  
  
-   Die mindestens erforderliche Version von Common Language Runtime, die als Assemblyabhängigkeit im Anwendungsmanifest angegeben ist.  
  
-   Die für die Anwendung mindestens erforderliche Version des Windows-Betriebssystems, wie im Anwendungsmanifest mit dem `<osVersionInfo>`-Element angegeben. (Finden Sie unter [ \<Dependency >-Element](../deployment/dependency-element-clickonce-application.md).)  
  
-   Die Mindestversion aller Assemblys, die im globalen Assemblycache (GAC), gemäß der Assembly Abhängigkeit Deklarationen im Assemblymanifest vorinstalliert werden müssen.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kann fehlende erforderliche Komponenten bestimmen, und Sie können erforderliche Komponenten mit einem Bootstrapper installieren. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren der erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
> [!NOTE]
>  So ändern Sie die Werte in den Manifesten, die mit Tools wie z. B. generierten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und *MageUI.exe*, müssen Sie das Anwendungsmanifest in einem Text-Editor bearbeiten, und klicken Sie dann erneut sowohl den Anwendungs- und Bereitstellungsmanifeste zu signieren. Weitere Informationen finden Sie unter [Vorgehensweise: Signieren Sie Anwendungs- und Bereitstellungsmanifeste erneut](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
 Wenn Sie Visual Studio und ClickOnce für die Bereitstellung der Anwendung verwenden, hängen die standardmäßig ausgewählten Bootstrapperpakete von der .NET Framework-Version in der Projektmappe ab. Aber wenn Sie .NET Framework-Zielversion ändern, müssen Sie aktualisieren die Optionen in der **Prerequisites Dialog Box** manuell.  
  
|.NET Framework-Zielversion|Ausgewählte Bootstrapperpakete|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  
  
 Mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung der *Publish.htm* Seite von generiert die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Veröffentlichungs-Assistenten verweist auf einen Link, der nur die Anwendung installiert wird, oder auf einen Link zum Installieren der Anwendung und der Bootstrap Komponenten.  
  
 Wenn Sie den Bootstrapper generieren, mit der ClickOnce-Webpublishing-Assistenten oder die Seite "Veröffentlichen" in Visual Studio die *Setup.exe* automatisch angemeldet wird. Wenn Sie jedoch das Zertifikat des Kunden zum Signieren des Bootstrappers verwenden möchten, können Sie die Datei später signieren.  
  
## <a name="bootstrapping-and-msbuild"></a>Bootstrapping und MSBuild  
 Wenn Sie nicht verwenden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], aber stattdessen Ihre Anwendungen in der Befehlszeile zu kompilieren, können Sie erstellen die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bootstrappinganwendung mit einer Aufgabe Microsoft Build Engine (MSBuild). Weitere Informationen finden Sie unter [GenerateBootstrapper-Aufgabe](../msbuild/generatebootstrapper-task.md).  
  
 Als Alternative zum Bootstrapping können Sie Komponenten mit einem elektronischen Softwareverteilungssystem wie Microsoft Systems Management Server (SMS) vorab bereitstellen.  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>Befehlszeilenargumente Bootstrapper (Setup.exe)  
 Die *Setup.exe* vom [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und die MSBuild-Aufgaben unterstützen den folgenden Satz von Befehlszeilenargumenten. Alle anderen Argumente werden an das Installationsprogramm der Anwendung weitergeleitet.  
  
 Wenn Sie Bootstrapperoptionen ändern, müssen Sie den nicht signierten Bootstrapper ändern, und klicken Sie dann die Bootstrapperdatei später signieren.  
  
|Befehlszeilenargument|Beschreibung|  
|---------------------------|-----------------|  
|**-?, -h, -Hilfe**|Zeigt das Dialogfeld der Hilfe an.|  
|**-Url - Componentsurl**|Zeigt die gespeicherte URL und Komponenten-URLs für diese Installation an.|  
|**-Url =** `location`|Legt die URL fest, in denen *Setup.exe* sucht die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.|  
|**-Componentsurl =** `location`|Legt die URL fest, in denen *Setup.exe* sucht die Abhängigkeiten, wie z. B. die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].|  
|**-Homesite =** `true`**&#124;** `false`|Wenn `true`, lädt die Abhängigkeiten vom bevorzugten Speicherort auf der Website des Anbieters herunter. Diese Einstellung überschreibt die **- Componentsurl** festlegen. Wenn `false`, die Abhängigkeiten aus dem vom angegebenen URL heruntergeladen **- Componentsurl**.|  
  
## <a name="operating-system-support"></a>Unterstützte Betriebssysteme  
 Visual Studio-Bootstrappers wird auf Windows Server 2008 Server Core oder Windows Server 2008 R2 Server Core nicht unterstützt, wie eine wartungsarme serverumgebung mit eingeschränkter Funktionalität bieten. Die Server Core-Installationsoption unterstützt beispielsweise nur das .NET Framework 3.5 Server Core-Profil, in dem Visual Studio-Funktionen nicht ausgeführt werden kann, die das vollständige .NET Framework abhängig.  
  
## <a name="see-also"></a>Siehe auch  
 [Wählen Sie eine Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [ClickOnce security and deployment (ClickOnce-Sicherheit und -Bereitstellung)](../deployment/clickonce-security-and-deployment.md)