---
title: Server und Client-Konfigurationsprobleme in ClickOnce-Bereitstellungen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: "33"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 4b7153b0a20c10e7dbdb31ac943f150f72cb39d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Probleme mit der Server- und Clientkonfiguration in ClickOnce-Bereitstellungen
Wenn Sie Internetinformationsdienste (Internet Information Services, IIS) unter Windows Server verwenden und die Bereitstellung enthält einen Dateityp aus, dem Windows nicht erkannt wird, IIS lehnt z. B. Microsoft Word-Datei, um diese Datei zu übertragen, und die Bereitstellung nicht erfolgreich.  
  
 Darüber hinaus einige Webservern und Anwendungssoftware, z. B. Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], enthalten eine Liste von Dateien und Dateitypen, die nicht heruntergeladen werden können. Beispielsweise [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] verhindert das Herunterladen von Dateien für alle "Web.config". Diese Dateien enthalten möglicherweise vertrauliche Informationen wie Benutzernamen und Kennwörter.  
  
 Obwohl diese Einschränkung zum Herunterladen von Core unproblematisch [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Dateien wie Manifeste und Assemblys, diese Einschränkung kann verhindern, dass Sie Datendateien, die als Bestandteil von Herunterladen Ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. In [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], können Sie diesen Fehler beheben, durch das Entfernen des Handlers, der verhindert das Herunterladen von solche Dateien von den IIS-Konfigurations-Manager. Finden Sie in der IIS-Server-Dokumentation für zusätzliche Details.  
  
 Dateien mit Erweiterungen, z. B. dll-, .config und MDF können einige Webserver blockiert werden. Windows-basierten Anwendungen Includedateien in der Regel mit einigen dieser Erweiterungen. Wenn ein Benutzer versucht, führen Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, die auf eine blockierte Datei auf einem Webserver zugreift, einem Fehler führt. Anstatt alle Erweiterungen, Blockierung [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jeder Anwendungsdatei mit der Erweiterung ".deploy" standardmäßig veröffentlicht. Aus diesem Grund muss der Administrator nur so konfigurieren Sie den Webserver für die folgenden drei Dateierweiterungen zu entsperren:  
  
-   APPLICATION  
  
-   MANIFEST  
  
-   DEPLOY  
  
 Allerdings können Sie diese Option deaktivieren, indem Sie deaktivieren die **Dateierweiterung ".deploy" verwenden** option die [veröffentlichen Optionen (Dialogfeld)](http://msdn.microsoft.com/en-us/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), in diesem Fall Sie den Webserver für alle Dateierweiterungen aufheben konfigurieren müssen in der Anwendung verwendet.  
  
 Müssen so konfigurieren Sie Manifest und .application ".deploy", z. B. Wenn Sie IIS verwenden, in dem Sie nicht installiert haben, die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], oder wenn Sie einen anderen Webserver (z. B. Apache) verwenden.  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce und Secure Sockets Layer (SSL)  
 Ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, über SSL, außer wenn eine Eingabeaufforderung zu dem SSL-Zertifikat von Internet Explorer löst einwandfrei arbeitet. Die Aufforderung kann ausgelöst werden, wenn vorhanden ist, dass etwas mit dem Zertifikat, z. B. wenn die Websitenamen nicht übereinstimmen oder das Zertifikat abgelaufen ist. Vornehmen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] über eine SSL-Verbindung funktioniert, stellen Sie sicher, dass das Zertifikat auf dem neuesten Stand ist und dass die Zertifikatdaten Daten des Standorts übereinstimmt.  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce- und Proxy-Authentifizierung  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]bietet Unterstützung für integrierte Windows-Proxy-Authentifizierung, die in .NET Framework 3.5 ab. Es sind keine spezifischen "Machine.config" Direktiven erforderlich. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]bietet keine Unterstützung für andere Authentifizierungsprotokolle wie z. B. die Standard- oder Digestauthentifizierung.  
  
 Sie können auch einen Hotfix für .NET Framework 2.0 zum Aktivieren dieser Funktion anwenden. Weitere Informationen finden Sie unter http://go.microsoft.com/fwlink/?LinkId=158730.  
  
 Weitere Informationen finden Sie unter [ \<DefaultProxy >-Element (Netzwerkeinstellungen)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce und Web-Browserkompatibilität  
 Derzeit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Installationen nur gestartet, wenn die URL für das Bereitstellungsmanifest mit der Internet Explorer geöffnet wird. Eine Bereitstellung, deren URL durch eine andere Anwendung, z. B. Microsoft Office Outlook gestartet wird, wird erfolgreich gestartet werden, nur dann, wenn Internet Explorer als Standardbrowser festgelegt ist.  
  
> [!NOTE]
>  Mozilla Firefox wird unterstützt, wenn der Bereitstellungsanbieter nicht leer ist oder die Erweiterung von Microsoft .NET Framework-Assistent installiert ist. Diese Erweiterung wird mit .NET Framework 3.5 SP1 verpackt. Die NPWPF-Plug-in wird bei Bedarf für die XBAP-Unterstützung aktiviert.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>Aktivieren von ClickOnce-Anwendungen mithilfe von Skripts Browser  
 Wenn Sie eine benutzerdefinierte Webseite entwickelt haben, die startet eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung mithilfe von Active Scripting, vorkommen, dass die Anwendung auf einigen Computern nicht gestartet werden. Internet Explorer enthält eine Einstellung als bezeichnet **automatische aufgefordert werden, für den Download der Datei**, denen dieses Verhalten wirkt sich auf. Diese Einstellung ist verfügbar, auf die **Sicherheit** Registerkarte seine **Optionen** Menü, das dieses Verhalten wirkt sich auf. Aufgerufen wird **automatische aufgefordert werden, für den Download der Datei**, und es wird aufgeführt, unter der **Downloads** Kategorie. Die Eigenschaft wird festgelegt, um **aktivieren** standardmäßig für die Webseiten im Intranet und **deaktivieren** standardmäßig für Internet-Webseiten. Wenn diese Einstellung festgelegt wurde, um **deaktivieren**, jeder Versuch, aktivieren Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung programmgesteuert (z. B. durch die URL zum Zuweisen der `document.location` Eigenschaft) blockiert werden. Unter diesen Umständen können Benutzer Anwendungen nur über einen Download Benutzerinitiierte z. B. Starten Sie durch Klicken auf einen Link auf die URL der Anwendung festgelegt.  
  
## <a name="additional-server-configuration-issues"></a>Zusätzliche Server-Konfigurationsprobleme  
  
##### <a name="administrator-permissions-required"></a>Administratorberechtigungen erforderlich sind  
 Sie müssen über Administratorberechtigungen auf dem Zielserver verfügen, wenn Sie mit HTTP veröffentlichen. IIS ist diese Berechtigungsebene erforderlich. Wenn Sie nicht über HTTP veröffentlichen, müssen Sie nur auf den Zielpfad Schreibberechtigung.  
  
##### <a name="server-authentication-issues"></a>Server-Authentifizierungsprobleme  
 Beim Veröffentlichen auf einem Remoteserver, der "Anonymer Zugriff" deaktiviert hat, wird die folgende Warnung angezeigt:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  NTLM (NT Challenge-Response)-Authentifizierung verwendet werden, wenn die Website, Anmeldeinformationen von denen die standardmäßigen Anmeldeinformationen aufgefordert, und klicken Sie im Dialogfeld Sicherheit auf Sie möglich **OK** Wenn Sie aufgefordert werden, wenn das angegebene gespeichert werden soll Anmeldeinformationen für zukünftige Sitzungen. Diese problemumgehung funktioniert jedoch nicht für die Standardauthentifizierung.  
  
## <a name="using-third-party-web-servers"></a>Mithilfe von Drittanbieter-Webservern  
 Beim Bereitstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung von einem Webserver als IIS können Sie ein Problem auftreten, wenn der Server den falschen Inhaltstyp für Schlüssel zurückgibt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Dateien, z. B. das Bereitstellungsmanifest und Anwendungsmanifest. Um dieses Problem zu beheben, finden Sie in Ihrer Web-Server-Hilfe Dokumentation dazu, wie auf dem Server neue Inhaltstypen hinzu, und stellen Sie sicher, dass alle Datei Namen Erweiterung Zuordnungen in der folgenden Tabelle aufgeführt sind.  
  
|Dateinamenerweiterung|Inhaltstyp|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce und zugeordnete Laufwerke  
 Wenn Sie Visual Studio verwenden, um eine ClickOnce-Anwendung zu veröffentlichen, können nicht Sie ein zugeordnetes Laufwerk als Installationspfad angeben. Allerdings können Sie die ClickOnce-Anwendung so installieren Sie über ein zugeordnetes Laufwerk mit dem Manifest-Generator und -Editor (Mage.exe und MageUI.exe) ändern. Weitere Informationen finden Sie unter [Mage.exe (Manifest generieren und Bearbeiten von Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) und [MageUI.exe (Manifest generieren und Bearbeiten von Manifesten, Grafischer Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>FTP-Protokoll für die Installation von Anwendungen wird nicht unterstützt.  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]unterstützt das Installieren von Anwendungen von einem HTTP 1.1-Web-Server oder Dateiserver. FTP, File Transfer-Protokoll wird nicht unterstützt, für die Installation von Anwendungen. Sie können FTP verwenden, können Sie Anwendungen nur veröffentlichen. In der folgenden Tabelle werden diese Unterschiede zusammengefasst:  
  
|URL-Typ|Beschreibung|  
|--------------|-----------------|  
|FTP: / /|Sie können Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung mithilfe dieses Protokolls.|  
|http://|Sie können eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung mithilfe dieses Protokolls.|  
|https://|Sie können eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung mithilfe dieses Protokolls.|  
|file://|Sie können eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung mithilfe dieses Protokolls.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Unter Windows XP SP2: Windows-Firewall  
 Windows XP SP2 wird standardmäßig die Windows-Firewall aktiviert. Wenn Sie Ihre Anwendung auf einem Computer, die Windows XP installiert ist entwickeln, sind Sie dennoch veröffentlichen und ausführen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen aus dem lokalen Server, auf denen IIS ausgeführt wird. Sie können nicht jedoch auf diesem Server zugreifen, der von einem anderen Computer IIS ausgeführt wird, es sei denn, die Windows-Firewall zu öffnen. Anweisungen zum Verwalten der Windows-Firewall finden Sie in der Windows-Hilfe.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>WindowsServer: Aktivieren Sie die FrontPage-Servererweiterungen  
 Die FrontPage-Servererweiterungen von Microsoft ist erforderlich für das Veröffentlichen von Anwendungen auf einem Windows-Webserver, der HTTP verwendet.  
  
 Standardmäßig verfügt Windows Server nicht die FrontPage-Servererweiterungen installiert. Wenn Sie verwenden möchten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] um auf einem Windows Server-Webserver veröffentlichen, die HTTP mit FrontPage-Servererweiterungen verwendet, müssen Sie zunächst die FrontPage-Servererweiterungen installieren. Sie können die Installation ausführen, mit das Verwaltungstool für die Serververwaltung in Windows Server.  
  
## <a name="windows-server-locked-down-content-types"></a>WindowsServer: Gesperrtes Inhaltstypen  
 IIS auf [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] Sperren nach-unten-alle Dateitypen mit Ausnahme bestimmter bekannten Inhaltstypen (z. B. htm, HTML, ".txt" usw.). So aktivieren Sie die Bereitstellung von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen, die diesen Server verwenden, müssen Sie die IIS-Einstellungen zum Zulassen der Herunterladen von Dateien vom Typ .application, Manifest und benutzerdefinierte Datei andere Typen, von der Anwendung verwendeten ändern.  
  
 Wenn Sie die Bereitstellung mit einem IIS-Server, führen Sie inetmgr.exe, und fügen Sie neue Dateitypen für die Standardwebseite hinzu:  
  
-   Für die Erweiterungen .application und Manifest muss der MIME-Typ "Application/X-ms-Anwendung." Für andere Dateitypen muss der MIME-Typ "Application/Octet-Stream".  
  
-   Bei der Erstellung eines MIME-Typs mit der Erweiterung "*" und den MIME-Typ "Application/Octet-Stream", können sie Dateien mit entsperrt Dateityp heruntergeladen werden. (Allerdings blockiert-Datei, die Typen, z. B. aspx- und ASMX heruntergeladen werden können.)  
  
 Spezifische Anweisungen zum Konfigurieren von MIME-Typen auf Windows Server finden Sie in der Microsoft Knowledge Base-Artikel KB326965, "IIS 6.0 wird nicht dienen unbekannte MIME-Typen" am [http://support.microsoft.com/default.aspx?scid=kb;en-us;326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>Content-Type-Zuordnungen  
 Wenn Sie über HTTP zu veröffentlichen, muss der Inhaltstyp für die Application-Datei (auch bekannt als MIME-Typ) "Application/X-ms-Anwendung." Wenn Sie haben [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] auf dem Server installiert, dies wird für Sie automatisch festgelegt. Wenn dies nicht installiert ist, müssen Sie eine MIME-Typ-Verknüpfung erstellen die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung Vroot (oder den gesamten Server).  
  
 Wenn Sie die Bereitstellung mit einem IIS-Server, inetmgr.exe ausgeführt, und neue Inhaltstyp "Application/X-ms-Application" für die Erweiterung .application hinzufügen.  
  
## <a name="http-compression-issues"></a>Probleme bei der HTTP-Komprimierung  
 Mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], können Sie Downloads, die HTTP-Komprimierung verwenden, eine Web-Server-Technologie, die den GZIP-Algorithmus verwendet, um einen Datenstrom zu komprimieren, vor dem Senden des Streams an den Client ausführen. Der Client – in diesem Fall [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]– die Stream vor dem Lesen der Dateien dekomprimiert.  
  
 Wenn Sie IIS verwenden, können Sie einfach die HTTP-Komprimierung aktivieren. Wenn Sie HTTP-Komprimierung aktivieren, es ist jedoch nur aktiviert für bestimmte Dateitypen – d. h., HTML- und Text-Dateien. Um die Komprimierung für Assemblys (.dll) aktivieren, müssen XML (XML), Bereitstellungsmanifeste (.application) und Anwendungsmanifeste (. manifest) Sie diese Dateitypen zur Liste der Typen für IIS zum Komprimieren hinzufügen. Bis Sie die Dateitypen für Ihre Bereitstellung hinzufügen, werden nur Text und HTML-Dateien komprimiert werden.  
  
 Detaillierte Anweisungen für IIS finden Sie unter [wie zusätzliche Dokumenttypen für HTTP-Komprimierung angegeben](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)   
 [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md)