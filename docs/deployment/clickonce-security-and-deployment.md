---
title: ClickOnce-Sicherheit und-Bereitstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dd089b57fb50d20c8805c932b0043bb8c0dba82e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926448"
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce-Sicherheit und Bereitstellung
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist eine bereitstellungstechnologie, mit dem Sie selbst aktualisierende Windows-basierte Anwendungen erstellen, die installiert und mit minimalem Benutzereingriff ausgeführt werden können. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bietet vollständige Unterstützung für das Veröffentlichen und Aktualisieren von Anwendungen mit ClickOnce-Technologie bereitgestellt werden, wenn Sie Ihre Projekte mit Visual Basic und Visual c# entwickelt haben. Informationen zum Bereitstellen von Visual C++-Anwendungen finden Sie unter [ClickOnce-Bereitstellung für Visual C++-Anwendungen](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung löst drei grundlegende Probleme:  
  
- **Probleme beim Aktualisieren von Anwendungen.** Mit Microsoft Windows Installer-Bereitstellung Wenn eine Anwendung aktualisiert wird, der Benutzer kann Installieren eines Updates, die eine Msp-Datei, und klicken Sie auf das installierte Produkt anwenden; mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung, Sie können angeben, Updates automatisch. Nur die Teile der Anwendung, die geändert wurden, werden heruntergeladen, und klicken Sie dann die vollständige aktualisierte Anwendung neu installiert wird über einen neuen Ordner für die Seite-an-Seite.  
  
- **Auswirkungen auf dem Computer des Benutzers.** Mit Windows Installer-Bereitstellung nutzen die Anwendungen häufig auf freigegebene Komponenten, mit einem möglichen Konflikte bei der versionsverwaltung; mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung, jede Anwendung ist in sich geschlossen und verursacht keine Konflikte mit anderen Anwendungen.  
  
- **Die Sicherheitsberechtigungen.** Windows Installer-Bereitstellung sind Administratorrechte erforderlich und kann nur Benutzer mit beschränkten Rechten installiert werden. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung können Benutzer ohne Administratorrechte installieren und nur die Codezugriffssicherheits-Berechtigungen erforderlich, dass die Anwendung gewährt.  
  
  In der Vergangenheit verursacht diese Probleme manchmal Entwickler zum Erstellen von Web-Anwendungen anstelle von Windows-basierte Anwendungen, Einbußen bei der eine umfangreiche Benutzeroberfläche für die einfache Installation entscheiden. Mithilfe von Anwendungen, die mit bereitgestellt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], können Sie das beste aus beiden Technologien haben.  
  
## <a name="what-is-a-clickonce-application"></a>Was ist eine ClickOnce-Anwendung?  
 Ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung ist eine beliebige Windows Presentation Foundation (*.xbap*), Windows Forms (*.exe*), Konsolenanwendung (*.exe*), oder die Office-Projektmappe (*DLL*) mithilfe der veröffentlicht [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Technologie. Können Sie veröffentlichen eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung auf drei verschiedene Arten: von einer Webseite, aus einer Dateifreigabe im Netzwerk oder von Medien, wie eine CD-ROM. Ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung auf einem Computer des Endbenutzers installiert und lokal ausführen, auch wenn der Computer offline ist, oder sie kann nur online verfügbares ohne dass Dateien auf dem Computer des Endbenutzers ausgeführt werden kann. Weitere Informationen finden Sie unter [auswählen eine Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen können eigenständig aktualisiert werden; Sie können überprüfen, neuere Versionen vorliegen, und die aktualisierten Dateien automatisch ersetzen. Der Entwickler kann das Aktualisierungsverhalten festlegen. Netzwerkadministratoren kann auch steuern, aktualisieren Sie die Strategien, z. B. ein Update als obligatorisch kennzeichnen. Updates können auch auf eine frühere Version vom Endbenutzer oder von einem Administrator zurückgesetzt werden. Weitere Informationen finden Sie unter [auswählen eine Strategie für ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen sind isoliert, installieren oder Ausführen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung vorhandene Anwendungen nicht zerstören. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen sind eigenständig und enthalten; Jede [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung installiert und in einem sicheren, Benutzer-und anwendungsspezifischen Cache ausgeführt. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen, die in das Internet oder Intranet-Sicherheitszonen ausgeführt werden. Bei Bedarf kann die Anwendung erhöhte Sicherheitsberechtigungen anfordern. Weitere Informationen finden Sie unter [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md).  
  
## <a name="how-clickonce-security-works"></a>Funktionsweise der ClickOnce-Sicherheit  
 Die wichtigsten [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Sicherheit basiert auf Zertifikate, Codezugriffs-Sicherheitsrichtlinien und der ClickOnce-vertrauensaufforderung.  
  
### <a name="certificates"></a>Zertifikate  
 Authenticode-Zertifikate werden verwendet, um die Echtheit des Herausgebers der Anwendung zu überprüfen. Durch die Verwendung von Authenticode bei Bereitstellung einer Anwendung, können ClickOnce verhindern, dass ein schädliches Programm repräsentierte selbst als sicheres Programm aus einer bekannten und vertrauenswürdigen Quelle stammen. Optional Zertifikate können auch zum Signieren der Anwendung verwendet werden, und Bereitstellungsmanifesten um nachzuweisen, dass die Dateien nicht manipuliert wurden. Weitere Informationen finden Sie unter [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md). Zertifikate können auch verwendet werden, zum Konfigurieren von Clientcomputern für die eine Liste der vertrauenswürdigen Herausgeber verfügen. Wenn eine Anwendung von einem vertrauenswürdigen Herausgeber stammt, kann es ohne Eingreifen des Benutzers installiert werden. Weitere Informationen finden Sie unter [Übersicht über die Bereitstellung von vertrauenswürdigen Anwendung](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="code-access-security"></a>Codezugriffssicherheit  
 Code Access Secrity hilft dabei, den Zugriff zu begrenzen, den Code auf geschützte Ressourcen hat. In den meisten Fällen können Sie die Zonen "Internet" oder "Lokales Intranet" die Berechtigungen einschränken. Verwenden der **Sicherheit** auf der Seite die **ProjectDesigner** zum Anfordern der Zone, die für die Anwendung geeignet. Sie können auch Anwendungen mit eingeschränkten Berechtigungen zum Emulieren der endbenutzererfahrung Debuggen. Weitere Informationen finden Sie unter [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../deployment/code-access-security-for-clickonce-applications.md).  
  
### <a name="clickonce-trust-prompt"></a>ClickOnce-vertrauensaufforderung  
 Wenn eine Anwendung mehr Berechtigungen als können die Zone anfordert, kann der Endbenutzer aufgefordert werden, eine Vertrauensstellung Entscheidung zu treffen. Benutzer können entscheiden, ob es sich bei ClickOnce-Anwendungen wie z. B. Windows Forms-Anwendungen, Windows Presentation Foundation-Anwendungen, konsolenanwendungen, XAML-Browseranwendungen und Office-Projektmappen vertrauenswürdig ist und ausgeführt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren des Verhaltens der ClickOnce Vertrauenswürdigkeit auffordern](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## <a name="how-clickonce-deployment-works"></a>Funktionsweise der ClickOnce-Bereitstellung  
 Die wichtigsten [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsarchitektur basiert auf zwei XML-Manifestdateien: ein Anwendungsmanifest sowie ein Bereitstellungsmanifest. Die Dateien werden verwendet, um zu beschreiben, von dem die ClickOnce-Anwendungen installiert sind, wie sie aktualisiert werden und wann sie aktualisiert werden.  
  
### <a name="publish-clickonce-applications"></a>Veröffentlichen von ClickOnce-Anwendungen  
 Das Anwendungsmanifest beschreibt die Anwendung selbst. Dies schließt die Assemblys, die Abhängigkeiten und Dateien, aus denen die Anwendung, die erforderlichen Berechtigungen und den Speicherort, in denen Updates zur Verfügung stehen. Der Anwendungsentwickler erstellt das Anwendungsmanifest mit dem Webpublishing-Assistenten in Visual Studio oder das Manifest Generation and Editing Tool (*Mage.exe*) in der [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Weitere Informationen finden Sie unter [Vorgehensweise: veröffentlichen eine ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 Das Bereitstellungsmanifest beschreibt, wie die Anwendung bereitgestellt wird. Dies schließt den Speicherort des Anwendungsmanifests und die Version der Anwendung, die von Clients ausgeführt werden soll.  
  
### <a name="deploy-clickonce-applications"></a>Bereitstellen von ClickOnce-Anwendungen  
 Nachdem dieser erstellt wurde, wird das Bereitstellungsmanifest an den Bereitstellungsspeicherort kopiert. Dies kann eine Web-Server, Netzwerk-Dateifreigabe oder Medien wie CD sein. Das Anwendungsmanifest und alle Dateien der Anwendung werden auch an einen Bereitstellungsspeicherort kopiert, die im Bereitstellungsmanifest angegeben ist. Dies kann der Speicherort für die Bereitstellung identisch sein, oder es kann sein, einen anderen Speicherort. Bei Verwendung der **Veröffentlichungs-Assistenten** in Visual Studio werden die Kopiervorgänge automatisch ausgeführt.  
  
### <a name="install-clickonce-applications"></a>Installieren der ClickOnce-Anwendungen  
 Nachdem sie an den Bereitstellungsspeicherort bereitgestellt wurde, können Endbenutzer herunterladen und installieren Sie die Anwendung, indem Sie auf ein Symbol für die Bereitstellungsmanifestdatei auf einer Webseite oder in einem Ordner. In den meisten Fällen wird der Endbenutzer ein einfaches Dialogfeld den Benutzer auffordert, die Installation zu bestätigen, nachdem die Installation erfolgt und die Anwendung, ohne zusätzlichen Eingriff gestartet wird angezeigt. In Fällen, in denen die Anwendung erfordert, erhöhte Berechtigungen, oder wenn die Anwendung nicht von einem vertrauenswürdigen Zertifikat signiert ist, fordert Sie das Dialogfeld auch den Benutzer zum Erteilen der Berechtigung, bevor die Installation fortgesetzt werden kann. Obwohl ClickOnce-Installationen pro Benutzer sind, möglicherweise über erweiterte Berechtigungen erforderlich, wenn gibt es Voraussetzungen, die Administratorrechte erforderlich sind. Weitere Informationen zu erweiterten Berechtigungen, finden Sie unter [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md).  
  
 Zertifikate können vertrauenswürdige Ebene der Computer- oder Unternehmensebene sein, damit im Hintergrund mit einem vertrauenswürdigen Zertifikat signierte der ClickOnce-Anwendungen installieren können. Weitere Informationen zu vertrauenswürdigen Zertifikaten finden Sie unter [Übersicht über die Bereitstellung von vertrauenswürdigen Anwendung](../deployment/trusted-application-deployment-overview.md).  
  
 Kann die Anwendung des Benutzers hinzugefügt werden **starten** Menü und die **Software** Gruppe der **Systemsteuerung**. Im Gegensatz zu anderen bereitstellungstechnologien wird nichts hinzugefügt die **Programmdateien** Ordner oder die Registrierung und keine Administratorrechte für die Installation erforderlich sind  
  
> [!NOTE]
>  Es ist auch möglich, die verhindern, dass die Anwendung hinzugefügt wird die **starten** Menü und **Software** Gruppe faktisch somit Verhalten sich wie eine Webanwendung. Weitere Informationen finden Sie unter [auswählen eine Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### <a name="update-clickonce-applications"></a>Aktualisieren Sie die ClickOnce-Anwendungen  
 Wenn die Anwendungsentwickler eine aktualisierte Version der Anwendung erstellen, sie ein neues Anwendungsmanifest generieren und Dateien an einen Bereitstellungsspeicherort kopieren, in der Regel ein gleichgeordneter Ordner in den ursprünglichen Bereitstellungsordner der Anwendung. Der Administrator aktualisiert das Bereitstellungsmanifest, zeigen Sie auf den Speicherort der neuen Version der Anwendung.  
  
> [!NOTE]
>  Die **Veröffentlichungs-Assistenten** in Visual Studio zum Ausführen dieser Schritte verwendet werden.  
  
 Neben dem Bereitstellungsspeicherort enthält das Bereitstellungsmanifest auch einen Updatespeicherort (eine Webseite oder Datei-Netzwerkfreigabe), in dem sich die Anwendung nach aktualisierten Versionen sucht. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **Veröffentlichen von** Eigenschaften werden verwendet, um anzugeben, wann und wie oft die Anwendung nach Updates suchen soll. Aktualisierungsverhalten kann im Bereitstellungsmanifest angegeben werden, oder es kann angezeigt werden, als Auswahlmöglichkeit für den Benutzer in der Benutzeroberfläche der Anwendung, von der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] APIs. Darüber hinaus **veröffentlichen** Eigenschaften können verwendet werden, um Updates als obligatorisch festzulegen oder die Anwendung auf eine frühere Version zurückzusetzen. Weitere Informationen finden Sie unter [Auswählen einer Strategie der ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### <a name="third-party-installers"></a>Drittanbieter-Installer  
 Sie können Ihre ClickOnce-Installer zum Installieren von Drittanbieter-Komponenten zusammen mit Ihrer Anwendung anpassen. Sie haben das verteilbare Paket (.exe oder .msi-Datei), und beschreiben das Paket mit einer sprachneutralen Produktmanifests und ein Paketmanifest mit sprachspezifischen. Weitere Informationen finden Sie unter [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md).  
  
## <a name="clickonce-tools"></a>ClickOnce-tools  
 Die folgende Tabelle zeigt die Tools, die Sie zum Generieren, bearbeiten, Signieren und signieren Sie die Anwendungs- und Bereitstellungsmanifeste erneut verwenden können.  
  
|Tool|Beschreibung|  
|----------|-----------------|  
|[Seite „Sicherheit“, Projekt-Designer](../ide/reference/security-page-project-designer.md)|Meldet die Anwendungs- und Bereitstellungsmanifeste.|  
|[Seite „Veröffentlichen“, Projekt-Designer](../ide/reference/publish-page-project-designer.md)|Generiert und bearbeitet die Anwendungs- und Bereitstellungsmanifeste für Visual Basic und Visual C#-Anwendungen.|  
|[*Mage.exe* (Manifest Generation Tool und Bearbeiten von)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Generiert die Anwendungs- und Bereitstellungsmanifeste für Visual Basic, Visual c# und Visual C++-Anwendungen.<br /><br /> Meldet, und die Anwendungs- und Bereitstellungsmanifeste erneut signiert.<br /><br /> Können von batchskripten und der Eingabeaufforderung ausgeführt werden.|  
|[*MageUI.exe* (Manifest generieren und Bearbeiten von Manifesten, Grafischer Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|Wird generiert, und die Anwendungs- und Bereitstellungsmanifeste bearbeitet.<br /><br /> Meldet, und die Anwendungs- und Bereitstellungsmanifeste erneut signiert.|  
|[GenerateApplicationManifest-Aufgabe](../msbuild/generateapplicationmanifest-task.md)|Generiert das Anwendungsmanifest an.<br /><br /> Kann von MSBuild ausgeführt werden. Weitere Informationen finden Sie unter [MSBuild-Referenz](../msbuild/msbuild-reference.md).|  
|[GenerateDeploymentManifest-Aufgabe](../msbuild/generatedeploymentmanifest-task.md)|Generiert das Bereitstellungsmanifest.<br /><br /> Kann von MSBuild ausgeführt werden. Weitere Informationen finden Sie unter [MSBuild-Referenz](../msbuild/msbuild-reference.md).|  
|[SignFile-Aufgabe](../msbuild/signfile-task.md)|Meldet die Anwendungs- und Bereitstellungsmanifeste.<br /><br /> Kann von MSBuild ausgeführt werden. Weitere Informationen finden Sie unter [MSBuild-Referenz](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Entwickeln Sie Ihre eigene Anwendung aus, um die Anwendungs- und Bereitstellungsmanifeste zu generieren.|  
  
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