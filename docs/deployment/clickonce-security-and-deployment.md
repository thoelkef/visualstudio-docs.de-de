---
title: "ClickOnce Security and Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Windows applications, ClickOnce deployment"
  - "deploying applications [ClickOnce]"
  - "ClickOnce deployment"
  - "publishing, ClickOnce"
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce Security and Deployment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist eine Bereitstellungstechnologie, mit der selbstaktualisierende Windows\-basierte Anwendungen erstellt werden können, für deren Installation und Ausführung sehr wenig Benutzerinteraktion erforderlich ist. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bietet vollständige Unterstützung zur Veröffentlichung und Aktualisierung von Anwendungen, die mit ClickOnce\-Technologie bereitgestellt wurden, sofern die Projekte mithilfe von Visual Basic und Visual C\# entwickelt wurden.  Informationen zum Bereitstellen von Visual C\+\+\-Anwendungen finden Sie unter [ClickOnce\-Bereitstellung für Visual C\+\+\-Anwendungen](/visual-cpp/ide/clickonce-deployment-for-visual-cpp-applications).  
  
 Die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung löst drei Hauptprobleme bei der Bereitstellung:  
  
-   **Schwierigkeiten beim Aktualisieren von Anwendungen.** Bei der Bereitstellung mit Microsoft Windows Installer kann der Benutzer bei jeder Aktualisierung ein Update \(eine MSP\-Datei\) installieren und auf das installierte Produkt anwenden. Mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] können Sie Updates automatisch bereitstellen.  Dabei werden nur die Teile der Anwendung heruntergeladen, die geändert wurden. Anschließend wird die vollständige aktualisierte Anwendung von einem neuen parallelen Ordner aus neu installiert.  
  
-   **Auswirkungen auf den Computer des Benutzers.** Bei der Bereitstellung mit Windows Installer hängen Anwendungen oft von gemeinsam genutzten Komponenten ab. Dies kann zu Versionskonflikten führen. Bei der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung ist jede Anwendung völlig unabhängig und verursacht keine Konflikte mit anderen Anwendungen.  
  
-   **Sicherheitsberechtigungen.** Bei der Bereitstellung mit Windows Installer sind Administratorberechtigungen erforderlich. Außerdem ist nur eine eingeschränkte Benutzerinstallation möglich. Bei der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung kann die Installation durch Benutzer ohne Administratorberechtigungen erfolgen. Es werden nur die Rechte für Codezugriffssicherheit gewährt, die für die Anwendung erforderlich sind.  
  
 In der Vergangenheit haben diese Probleme manchmal dazu geführt, dass Webanwendungen anstelle von Windows\-Anwendungen entwickelt wurden. Dabei gingen die umfangreichen Features für die Benutzeroberfläche zu Gunsten der einfacheren Installation verloren.  Bei Anwendungen, die mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bereitgestellt werden, können Sie die Vorzüge beider Technologien nutzen.  
  
## Was ist eine ClickOnce\-Anwendung?  
 Eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung ist eine Windows Presentation Foundation \(XBAP\-Format\)\-, Windows Forms \(EXE\-Format\)\-, Konsolenanwendungs \(EXE\-Format\)\- oder Office \(DLL\-Format\)\-Lösung, die unter Verwendung der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Technologie veröffentlicht wurde.  Sie können eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung auf drei Arten veröffentlichen: auf einer Webseite, in einer Dateifreigabe im Netzwerk oder auf einem Datenträger wie einer CD\-ROM.  Eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung kann auf dem Computer des Endbenutzers installiert und lokal ausgeführt werden, auch wenn der Computer offline ist, oder sie kann als nur online verfügbares Programm ausgeführt werden, ohne dass auf dem Computer des Endbenutzers Dateien installiert werden.  Weitere Informationen finden Sie unter [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen können sich selbst aktualisieren. Dabei können sie prüfen, ob neuere Versionen vorliegen, und die aktualisierten Dateien automatisch austauschen.  Der Entwickler kann das Updateverhalten festlegen. Der Netzwerkadministrator kann ebenfalls Updatestrategien steuern und ein Update z. B. als obligatorisch kennzeichnen.  Der Endbenutzer oder Administrator kann ein Update auch auf eine vorherige Version zurücksetzen.  Weitere Informationen hierzu finden Sie unter [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen isoliert sind, kann das Installieren oder Ausführen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung vorhandene Anwendungen nicht beschädigen.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen sind in sich abgeschlossen. Jede [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung wird je Benutzer bzw. je Anwendung in einen sicheren Cache installiert und dort ausgeführt.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen werden in der Sicherheitszone für das Internet oder Intranet ausgeführt.  Falls notwendig kann die Anwendung erhöhte Sicherheitsberechtigungen anfordern.  Weitere Informationen finden Sie unter [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md).  
  
## Funktionsweise der ClickOnce\-Sicherheit  
 Die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Kernsicherheit basiert auf Zertifikaten, Codezugriffssicherheitsrichtlinien und der vertrauenswürdigen ClickOnce\-Eingabeaufforderung.  
  
### Zertifikate  
 Authenticode\-Zertifikate werden zur Überprüfung der Echtheit des Herausgebers der Anwendung verwendet.  Durch die Verwendung von Authenticode zur Anwendungsbereitstellung ist ClickOnce dabei behilflich, schädliche Programme davon abzuhalten, sich als rechtmäßiges Programm mit vertrauenswürdiger Quelle auszugeben.  Optional können Zertifikate auch zur Unterzeichnung der Anwendung und der Bereitstellungsmanifeste verwendet werden. So kann bewiesen werden, dass die Dateien nicht verändert wurden.  Weitere Informationen finden Sie unter [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md).  Zertifikate können ebenfalls verwendet werden, um Clientcomputer für die Integration einer Liste vertrauenswürdiger Herausgeber zu konfigurieren.  Wurde eine Anwendung von einem vertrauenswürdigen Herausgeber veröffentlicht, kann sie ohne Benutzerinteraktion installiert werden.  Weitere Informationen finden Sie unter [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md).  
  
### Codezugriffssicherheit  
 Mit der Funktion für die Codezugriffssicherheit lässt sich der Codezugriff auf geschützte Ressourcen einschränken.  In den meisten Fällen können Sie die Zonen "Internet" oder "Lokales Intranet" auswählen, um die Berechtigungen zu beschränken.  Verwenden Sie im **Projekt**\-**Designer** die Seite **Sicherheit**, um die für die Anwendung erforderliche Zone anzufordern.  Sie können auch Anwendungen mit eingeschränkten Berechtigungen debuggen, um die Endbenutzererfahrung zu emulieren.  Weitere Informationen finden Sie unter [Codezugriffssicherheit für ClickOnce\-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md).  
  
### ClickOnce\-Eingabeaufforderung zur Vertrauenswürdigkeit  
 Fordert die Anwendung mehr Berechtigungen an als die Zone zulässt, kann der Endbenutzer zum Treffen einer Entscheidung über die Vertrauenswürdigkeit aufgefordert werden.  Der Endbenutzer kann entscheiden, ob ClickOnce\-Anwendungen, wie Windows Forms\-Anwendungen, Windows Presentation Foundation\-Anwendungen, Konsolenanwendungen, XAML\-Browseranwendungen und Office\-Lösungen vertrauenswürdig sind und ausgeführt werden dürfen.  Weitere Informationen finden Sie unter [How to: Configure the ClickOnce Trust Prompt Behavior](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## Funktionsweise der ClickOnce\-Bereitstellung  
 Der Kern der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungsarchitektur beruht auf zwei XML\-Manifestdateien: einem Anwendungsmanifest und einem Bereitstellungsmanifest.  Die Dateien werden zur Beschreibung verwendet, von wo die ClickOnce\-Anwendungen installiert werden und wie und wann sie aktualisiert werden.  
  
### Veröffentlichen von ClickOnce\-Anwendungen  
 Im Anwendungsmanifest wird die Anwendung selbst beschrieben.  Eingeschlossen sind dabei die Assemblys, die Abhängigkeiten und die Dateien, aus denen die Anwendung besteht, die erforderlichen Berechtigungen und der Speicherort, an dem Updates verfügbar sind.  Der Anwendungsentwickler erstellt das Anwendungsmanifest mit dem Webpublishing\-Assistenten in Visual Studio oder mit dem Tool zum Generieren und Bearbeiten von Manifesten \(Mage.exe\) in [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  Weitere Informationen finden Sie unter [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 Im Bereitstellungsmanifest wird beschrieben, wie die Anwendung bereitgestellt wird.  Eingeschlossen sind dabei der Speicherort des Anwendungsmanifests sowie die Version der Anwendung, die auf den Clients ausgeführt wird.  
  
### Bereitstellen von ClickOnce\-Anwendungen  
 Nach der Erstellung wird das Bereitstellungsmanifest an den Bereitstellungsspeicherort kopiert.  Hierbei kann es sich um einen Webserver, eine Dateifreigabe im Netzwerk oder einen Datenträger wie eine CD handeln.  Außerdem werden das Anwendungsmanifest und alle Anwendungsdateien an einen Bereitstellungsspeicherort kopiert, der im Bereitstellungsmanifest angegeben ist.  Dies kann derselbe Bereitstellungsspeicherort oder ein anderer Speicherort sein.  Wenn Sie den **Webpublishing\-Assistenten** in Visual Studio verwenden, werden die Kopiervorgänge automatisch ausgeführt.  
  
### Installieren von ClickOnce\-Anwendungen  
 Nach der Bereitstellung am Bereitstellungsspeicherort können Endbenutzer die Anwendung herunterladen und installieren, indem Sie auf einer Webseite oder in einem Ordner auf das Symbol doppelklicken, dass die Datei mit dem Bereitstellungsmanifest darstellt.  In den meisten Fällen wird ein einfaches Dialogfeld angezeigt, in dem der Endbenutzer die Installation bestätigen muss. Anschließend erfolgt die die Installation ohne weiteren Eingriff, und die Anwendung wird gestartet.  In Situationen, in denen für die Anwendung höhere Berechtigungen erforderlich sind oder die Anwendung nicht mit einem vertrauenswürdigen Zertifikat unterzeichnet wurde, wird der Benutzer im Dialogfeld außerdem dazu aufgefordert, die Berechtigungen zu gewähren, bevor die Installation fortfahren kann.  Obwohl ClickOnce für einzelne Benutzer installiert wird, kann die Berechtigungsausweitung erforderlich sein, wenn für erforderliche Komponenten Administratorrechte benötigt werden.  Weitere Informationen zu erweiterten Berechtigungen finden Sie unter [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md).  
  
 Zertifikate können über Vertrauenswürdigkeit auf Computer\- oder Unternehmensebene verfügen. So können vertrauenswürdige ClickOnce\-Anwendungen automatisch installiert werden.  Weitere Informationen über vertrauenswürdige Zertifikate finden Sie unter [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md).  
  
 Die Anwendung kann dem **Startmenü** des Benutzers und der Gruppe **Software** in der **Systemsteuerung** hinzugefügt werden.  Im Gegensatz zu anderen Bereitstellungstechnologien wird dem Ordner **Programme** oder der Registrierung nichts hinzugefügt, und für die Installation sind keine Administratorberechtigungen erforderlich.  
  
> [!NOTE]
>  Es kann auch festgelegt werden, dass die Anwendung nicht dem **Startmenü** und der Gruppe **Software** hinzugefügt wird. Die Anwendung verhält sich dann wie eine Webanwendung.  Weitere Informationen finden Sie unter [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### Aktualisieren von ClickOnce\-Anwendungen  
 Beim Erstellen einer aktualisierten Version der Anwendung müssen Entwickler auch ein neues Anwendungsmanifest generieren und Dateien an einen Bereitstellungsspeicherort kopieren. Hierbei handelt es sich i. d. R. um einen nebengeordneten Ordner des ursprünglichen Bereitstellungsordners der Anwendung.  Der Administrator aktualisiert das Bereitstellungsmanifest, um den Speicherort der neuen Anwendungsversion anzugeben.  
  
> [!NOTE]
>  Diese Schritte können mit dem **Webpublishing\-Assistenten** in Visual Studio ausgeführt werden.  
  
 Zusätzlich zum Bereitstellungsspeicherort enthält das Bereitstellungsmanifest einen Updatepfad \(eine Webseite oder eine Dateifreigabe im Netzwerk\), über den die Anwendung nach aktualisierten Versionen sucht.  Die Eigenschaften für die Veröffentlichung in [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] geben an, wann und wie oft die Anwendung die Updates überprüfen soll.  Das Updateverhalten kann im Bereitstellungsmanifest angegeben werden. Mit den [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-APIs kann es aber auch in der Benutzeroberfläche der Anwendung als Auswahlmöglichkeit für den Benutzer angezeigt werden.  Außerdem können die **Publish**\-Eigenschaften verwendet werden, um Updates als obligatorisch zu kennzeichnen oder die Anwendung auf eine frühere Version zurückzusetzen.  Weitere Informationen hierzu finden Sie unter [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### Drittanbieter\-Installationsprogramme  
 Sie können das ClickOnce\-Installationsprogramm so anpassen, dass Komponenten von Drittanbietern zusammen mit Ihrer Anwendung installiert werden.  Das verteilbare Paket \(EXE\- oder MSI\-Datei\) muss vorliegen und mit einem sprachunabhängigen Produktmanifest und einem sprachspezifischen Paketmanifest beschrieben werden.  Weitere Informationen finden Sie unter [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md).  
  
## ClickOnce\-Tools  
 In der folgenden Tabelle sind die Tools zur Erstellung, Bearbeitung, Unterzeichnung und erneuten Unterzeichnung der Anwendungs\- und Bereitstellungsmanifeste abgebildet.  
  
|Tool|Beschreibung|  
|----------|------------------|  
|[Seite "Sicherheit", Projekt\-Designer](../ide/reference/security-page-project-designer.md)|Unterzeichnet die Anwendungs\- und Bereitstellungsmanifeste.|  
|[Seite "Veröffentlichen", Projekt\-Designer](../ide/reference/publish-page-project-designer.md)|Erstellt und bearbeitet die Anwendungs\- und Bereitstellungsmanifeste für Visual Basic\- und Visual C\#\-Anwendungen.|  
|[Mage.exe \(Tool zum Generieren und Bearbeiten von Manifesten\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)|Erstellt die Anwendungs\- und Bereitstellungsmanifeste für Visual Basic\-, Visual C\#\- und Visual C\+\+\-Anwendungen.<br /><br /> Unterzeichnet die Anwendungs\- und Bereitstellungsmanifeste bzw. unterzeichnet sie erneut.<br /><br /> Kann von Batchskripts und der Eingabeaufforderung ausgeführt werden.|  
|[MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)|Erstellt und bearbeitet die Anwendungs\- und Bereitstellungsmanifeste.<br /><br /> Unterzeichnet die Anwendungs\- und Bereitstellungsmanifeste bzw. unterzeichnet sie erneut.|  
|[GenerateApplicationManifest Task](../msbuild/generateapplicationmanifest-task.md)|Erstellt das Anwendungsmanifest.<br /><br /> Kann in MSBuild ausgeführt werden.  Weitere Informationen hierzu finden Sie unter [MSBuild Reference](../msbuild/msbuild-reference.md).|  
|[GenerateDeploymentManifest Task](../msbuild/generatedeploymentmanifest-task.md)|Erstellt das Bereitstellungsmanifest.<br /><br /> Kann in MSBuild ausgeführt werden.  Weitere Informationen hierzu finden Sie unter [MSBuild Reference](../msbuild/msbuild-reference.md).|  
|[SignFile Task](../msbuild/signfile-task.md)|Unterzeichnet die Anwendungs\- und Bereitstellungsmanifeste.<br /><br /> Kann in MSBuild ausgeführt werden.  Weitere Informationen hierzu finden Sie unter [MSBuild Reference](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Entwickeln Sie eigene Anwendung, um die Anwendungs\- und die Bereitstellungsmanifeste zu generieren.|  
  
 In der folgenden Tabelle wird die jeweilige .NET Framework\-Version angezeigt, die für die Unterstützung von ClickOnce\-Anwendungen in diesen Browsern erforderlich ist.  
  
|Browser|.NET Framework\-Version|  
|-------------|-----------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|  
|Firefox|2.0 SP1, 3.5 SP1, 4|  
  
## Siehe auch  
 [ClickOnce Deployment on Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Deploying COM Components with ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Building ClickOnce Applications from the Command Line](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Debugging ClickOnce Applications That Use System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)