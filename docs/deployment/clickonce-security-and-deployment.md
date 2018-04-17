---
title: ClickOnce-Sicherheit und Bereitstellung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 24ebab9776c6cb0b829e1b79cb089ef6b826f726
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce-Sicherheit und Bereitstellung
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist eine bereitstellungstechnologie, mit dem Sie selbstaktualisierung Windows-basierten Anwendungen erstellen, die installiert und mit minimaler Benutzerinteraktion ausgeführt werden können. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bietet vollständige Unterstützung für das Veröffentlichen und Aktualisieren von Anwendungen mit ClickOnce-Technologie bereitgestellt werden, wenn Sie Ihre Projekte mit Visual Basic und Visual c# entwickelt haben. Informationen zum Bereitstellen von Visual C++-Anwendungen finden Sie unter [ClickOnce-Bereitstellung für Visual C++-Anwendungen](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung überwunden werden drei wichtige Aspekte, die bei der Bereitstellung:  
  
-   **Probleme beim Aktualisieren von Anwendungen.** Mit Microsoft Windows Installer-Bereitstellung Wenn eine Anwendung aktualisiert wird, der Benutzer kann ein Update, ein MSP-Datei installiert und auf das installierte Produkt angewendet; mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung, Sie können Updates automatisch bereitstellt. Nur die Teile der Anwendung, die geändert wurden, werden heruntergeladen und über einen neuen Ordner für die Seite-an-Seite klicken Sie dann auf die vollständige, aktualisierte Anwendung neu installiert.  
  
-   **Auswirkungen auf dem Computer des Benutzers.** Mit Windows Installer-Bereitstellung basieren die Anwendungen häufig auf gemeinsam genutzte Komponenten, mit einem möglichen Versionskonflikte; mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung, jede Anwendung ist in sich geschlossen und kann nicht in Konflikt mit anderen Anwendungen.  
  
-   **Sicherheitsberechtigungen.** Windows Installer-Bereitstellung sind Administratorrechte erforderlich und kann nur Benutzer mit eingeschränkten Rechten installiert werden. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung ermöglicht Nichtadministrator-Benutzern zur Installation und gewährt nur die Code Access Security-Berechtigungen für die Anwendung erforderlich.  
  
 In der Vergangenheit liegen verursacht diese Probleme mitunter Entwickler zum Erstellen von Web-Anwendungen anstelle von Windows-basierten Anwendungen verwendet werden, müssen eine umfangreiche Benutzeroberfläche für die einfache Installation entscheiden. Mithilfe von Anwendungen bereitgestellt, mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], dass das Beste beider Technologien.  
  
## <a name="what-is-a-clickonce-application"></a>Was ist eine ClickOnce-Anwendung?  
 Ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung ist eine beliebige Windows Presentation Foundation (XBAP), Windows Forms (.exe), Konsolenanwendung (.exe) oder Office-Projektmappe (.dll) mithilfe der veröffentlicht [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Technologie. Sie veröffentlichen eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung auf drei verschiedene Arten: von einer Webseite, aus einer Dateifreigabe im Netzwerk oder von einem Medium wie einer CD-ROM. Ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung kann auf dem Computer des Endbenutzers installiert und lokal ausgeführt werden, auch wenn der Computer offline ist oder in einem nur online-Modus ohne etwas dauerhaft auf dem Computer des Endbenutzers installiert ausgeführt werden. Weitere Informationen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen können selbstaktualisierung; Sie können überprüfen, neuere Versionen verfügbar, und Ersetzen Sie alle aktualisierten Dateien automatisch. Der Entwickler kann das Updateverhalten festlegen. Ein Netzwerkadministrator kann auch steuern, Aktualisierungsstrategien, z. B. ein Update als obligatorisch kennzeichnen. Updates können auch auf eine frühere Version vom Endbenutzer oder vom Administrator rückgängig gemacht werden. Weitere Informationen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen sind isoliert, installieren oder Ausführen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung kann nicht unterbrochen werden vorhandene Anwendungen. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen sind eigenständig und enthalten; Jede [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung installiert ist, und führen Sie von einem sicheren, Benutzer Cache pro Anwendung. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen, die im Internet oder Intranet Sicherheitszonen ausgeführt werden. Bei Bedarf kann die Anwendung mit erhöhten Rechten Sicherheitsberechtigungen anfordern. Weitere Informationen finden Sie unter [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md).  
  
## <a name="how-clickonce-security-works"></a>Funktionsweise von ClickOnce-Sicherheit  
 Der Kern [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Sicherheit basiert auf Zertifikaten, Codezugriffs-Sicherheitsrichtlinien und die ClickOnce-vertrauensaufforderung.  
  
### <a name="certificates"></a>Zertifikate  
 Authenticode-Zertifikate werden verwendet, um die Echtheit des Herausgebers der Anwendung zu überprüfen. Mithilfe von Authenticode für die Bereitstellung einer Anwendung verhindert ClickOnce ein schädliches Programm nahm selbst als sicheres Programm aus einer bekannten und vertrauenswürdigen Quelle stammen. Optional können Zertifikate auch zum Signieren der Anwendung verwendet werden und die Bereitstellungsmanifeste um nachzuweisen, dass die Dateien nicht manipuliert wurden. Weitere Informationen finden Sie unter [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md). Zertifikate können auch verwendet werden, zum Konfigurieren von Clientcomputern, um eine Liste der vertrauenswürdigen Herausgeber verfügen. Wenn eine Anwendung von einem vertrauenswürdigen Herausgeber stammen, kann er ohne Eingreifen des Benutzers installiert werden. Weitere Informationen finden Sie unter [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="code-access-security"></a>Codezugriffssicherheit  
 Codezugriffssicherheit wird den Zugriff zu begrenzen, den Code auf geschützte Ressourcen hat. In den meisten Fällen können Sie die Zonen "Internet" oder "Lokales Intranet befinden, die Berechtigungen zu beschränken. Verwenden der **Sicherheit** auf der Seite der **ProjectDesigner** , die für die Anwendung entsprechende Zone anfordert. Sie können auch Debuggen von Anwendungen mit eingeschränkten Berechtigungen für den Endbenutzer zu emulieren. Weitere Informationen finden Sie unter [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../deployment/code-access-security-for-clickonce-applications.md).  
  
### <a name="clickonce-trust-prompt"></a>ClickOnce-Vertrauensaufforderung  
 Wenn die Anwendung mehr Berechtigungen fordert als die Zone zulässt, kann der Endbenutzer aufgefordert werden, um eine Vertrauensstellung Entscheidung zu treffen. Die Endbenutzer können entscheiden, ob ClickOnce-Anwendungen wie z. B. Windows Forms-Anwendungen, Windows Presentation Foundation-Anwendungen, konsolenanwendungen, XAML-Browseranwendungen und Office-Projektmappen vertrauenswürdig ist und ausgeführt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren der ClickOnce-vertrauen Verhalten der Authentifizierungeingabeaufforderung](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## <a name="how-clickonce-deployment-works"></a>Funktionsweise der ClickOnce-Bereitstellung  
 Der Kern [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsarchitektur basiert auf zwei XML-Manifestdateien: ein Anwendungsmanifest und ein Bereitstellungsmanifest. Die Dateien werden verwendet, um zu beschreiben, auf dem die ClickOnce-Anwendungen aus installiert werden, wie sie aktualisiert werden und wenn sie aktualisiert werden.  
  
### <a name="publishing-clickonce-applications"></a>Veröffentlichen von ClickOnce-Anwendungen  
 Das Anwendungsmanifest beschreibt die Anwendung selbst. Dies schließt die Assemblys, die Abhängigkeiten und Dateien, aus denen die Anwendung, die erforderlichen Berechtigungen und den Speicherort, in denen Updates zur Verfügung stehen. Der Anwendungsentwickler erstellt das Anwendungsmanifest mit dem Webpublishing-Assistenten in Visual Studio oder das Manifest Tool zum Generieren und bearbeiten (Mage.exe) in der [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Weitere Informationen finden Sie unter [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 Das Bereitstellungsmanifest beschreibt, wie die Anwendung bereitgestellt wird. Dies schließt den Speicherort des Anwendungsmanifests und der Version der Anwendung, die Clients ausgeführt werden soll.  
  
### <a name="deploying-clickonce-applications"></a>Bereitstellen von ClickOnce-Anwendungen  
 Nachdem sie erstellt wurde, wird das Bereitstellungsmanifest an den Bereitstellungsspeicherort kopiert. Dies kann ein Web-Server, Netzwerk-Dateifreigabe oder Medien wie CD sein. Das Anwendungsmanifest und alle Dateien der Anwendung werden auch in einen Speicherort für die Bereitstellung kopiert, die im Bereitstellungsmanifest angegeben ist. Dies kann der Speicherort für die Bereitstellung identisch sein, oder es kann sich auf einem anderen Speicherort. Bei Verwendung der **Veröffentlichungs-Assistenten** in Visual Studio werden die Kopiervorgänge automatisch ausgeführt.  
  
### <a name="installing-clickonce-applications"></a>Installieren der ClickOnce-Anwendungen  
 Nachdem sie an den Bereitstellungsspeicherort bereitgestellt wurde, können Endbenutzer herunterladen und installieren Sie die Anwendung, indem Sie auf ein Symbol, das die Bereitstellungsmanifestdatei auf einer Webseite oder in einem Ordner darstellt. In den meisten Fällen erhält der Endbenutzer mit einem einfachen Dialogfeld fordert den Benutzer bestätigen, nachdem die Installation wird fortgesetzt, und die Anwendung, ohne weiteren Eingriff gestartet wird. In Fällen, in denen die Anwendung erfordert, erhöhten Berechtigungen, oder wenn die Anwendung nicht von einem vertrauenswürdigen Zertifikat signiert ist, fordert das Dialogfeld auch den Benutzer auf die Berechtigung zu erteilen, bevor die Installation fortgesetzt werden kann. Obwohl ClickOnce-Installationen pro Benutzer sind, möglicherweise berechtigungserweiterung erforderlich, wenn erforderliche Komponenten, die Administratorrechte erfordern vorhanden sind. Weitere Informationen zu erweiterten Berechtigungen finden Sie unter [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md).  
  
 Zertifikate können vertrauenswürdige Ebene der Computer- oder Unternehmensebene sein, damit ClickOnce-Anwendungen, die mit einem vertrauenswürdigen Zertifikat signiert im Hintergrund installiert werden können. Weitere Informationen zu vertrauenswürdigen Zertifikaten finden Sie unter [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
 Die Anwendung kann des Benutzers hinzugefügt werden **starten** Menü und die **Software** in Gruppe der **Systemsteuerung**. Im Gegensatz zu anderen bereitstellungstechnologien ist keine Elemente hinzugefügt die **Programmdateien** Ordner oder die Registrierung und keine Administratorrechte für die Installation erforderlich sind  
  
> [!NOTE]
>  Es ist auch möglich, zu verhindern, dass die Anwendung eingefügt werden die **starten** Menü und **Software** Gruppe faktisch somit verhält sich wie eine Webanwendung. Weitere Informationen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### <a name="updating-clickonce-applications"></a>Aktualisieren von ClickOnce-Anwendungen  
 Wenn der Anwendungsentwickler eine aktualisierte Version der Anwendung erstellen, sie generieren ein neues Anwendungsmanifest und kopieren Sie Dateien auf einen Speicherort für die Bereitstellung – in der Regel einen gleichgeordneten Ordner in den ursprünglichen Bereitstellungsordner für die Anwendung. Der Administrator aktualisiert das Bereitstellungsmanifest, um auf den Speicherort der neuen Version der Anwendung zu verweisen.  
  
> [!NOTE]
>  Die **Veröffentlichungs-Assistenten** in Visual Studio zum Ausführen dieser Schritte verwendet werden.  
  
 Zusätzlich zu den Bereitstellungsspeicherort enthält das Bereitstellungsmanifest auch einen Updatespeicherort (eine Webseite oder eine Netzwerkdateifreigabe), in dem die Anwendung nach aktualisierten Versionen sucht. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **Veröffentlichen** Eigenschaften werden verwendet, um anzugeben, wann und wie oft die Anwendung nach Updates suchen soll. Updateverhalten kann im Bereitstellungsmanifest angegeben werden, oder sie können als Benutzerauswahl in der Benutzeroberfläche mithilfe von der Anwendung angezeigt werden die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] APIs. Darüber hinaus **veröffentlichen** Eigenschaften können verwendet werden, um Updates als obligatorisch festzulegen oder ein Rollback auf eine frühere Version. Weitere Informationen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### <a name="third-party-installers"></a>Drittanbieter-Installationsprogramme  
 Sie können Ihre ClickOnce-Installationsprogramms zum Installieren von Drittanbieter-Komponenten zusammen mit der Anwendung anpassen. Das redistributable Package (.exe oder .msi-Datei) muss und das Paket mit einem sprachneutrale Produktmanifest und ein Paketmanifest sprachspezifische beschreiben. Weitere Informationen finden Sie unter [Bootstrapperpakete erstellen](../deployment/creating-bootstrapper-packages.md).  
  
## <a name="clickonce-tools"></a>ClickOnce-Tools  
 In der folgenden Tabelle zeigt die Tools, die Sie verwenden können, erstellen, bearbeiten, Signieren und signieren Sie die Anwendungs- und Bereitstellungsmanifeste erneut.  
  
|Tool|Beschreibung|  
|----------|-----------------|  
|[Seite „Sicherheit“, Projekt-Designer](../ide/reference/security-page-project-designer.md)|Meldet die Anwendungs- und Bereitstellungsmanifeste.|  
|[Seite „Veröffentlichen“, Projekt-Designer](../ide/reference/publish-page-project-designer.md)|Generiert und bearbeitet die Anwendungs- und Bereitstellungsmanifeste für Visual Basic und Visual C#-Anwendungen.|  
|[Mage.exe (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Generiert die Anwendungs- und Bereitstellungsmanifeste für Visual Basic, Visual c# und Visual C++-Anwendungen.<br /><br /> Signiert und die Anwendungs- und Bereitstellungsmanifeste erneut signiert.<br /><br /> Kann von batchskripten und der Befehlszeile aus ausgeführt werden.|  
|[MageUI.exe (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|Wird generiert, und die Anwendungs- und Bereitstellungsmanifeste bearbeitet.<br /><br /> Signiert und die Anwendungs- und Bereitstellungsmanifeste erneut signiert.|  
|[GenerateApplicationManifest-Aufgabe](../msbuild/generateapplicationmanifest-task.md)|Generiert das Anwendungsmanifest.<br /><br /> Kann von MSBuild ausgeführt werden. Weitere Informationen finden Sie unter [Referenz zu MSBuild-](../msbuild/msbuild-reference.md).|  
|[GenerateDeploymentManifest-Aufgabe](../msbuild/generatedeploymentmanifest-task.md)|Generiert das Bereitstellungsmanifest.<br /><br /> Kann von MSBuild ausgeführt werden. Weitere Informationen finden Sie unter [Referenz zu MSBuild-](../msbuild/msbuild-reference.md).|  
|[SignFile-Aufgabe](../msbuild/signfile-task.md)|Meldet die Anwendungs- und Bereitstellungsmanifeste.<br /><br /> Kann von MSBuild ausgeführt werden. Weitere Informationen finden Sie unter [Referenz zu MSBuild-](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Entwickeln Sie eine eigene Anwendung, um die Anwendungs- und Bereitstellungsmanifeste zu generieren.|  
  
 Die folgende Tabelle zeigt die .NET Framework-Version erforderlich, um die ClickOnce-Anwendungen in den folgenden Browsern unterstützt.  
  
|Browser|.NET Framework-Version|  
|-------------|----------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 4 3.5 SP1|  
|Firefox|2.0 SP1, 3.5 SP1, 4|  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Bereitstellung unter Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Bereitstellen von COM-Komponenten mit ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Erstellen von ClickOnce-Anwendungen über die Befehlszeile](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Debuggen von ClickOnce-Anwendungen, die System.Deployment.Application verwenden](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)