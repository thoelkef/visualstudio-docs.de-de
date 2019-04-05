---
title: Server Probleme und Clientkonfiguration in ClickOnce-Bereitstellungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 008e7991c8f88fb1c5a8b2eb99659ebe9134df26
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958326"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Probleme mit der Server- und Clientkonfiguration in ClickOnce-Bereitstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Internetinformationsdienste (Internet Information Services, IIS) unter Windows Server verwenden und die Bereitstellung enthält einen Dateityp aus, dem Windows nicht erkannt wird, wie z. B. Microsoft Word-Datei, verweigert IIS die Datei zu übertragen, und die Bereitstellung nicht erfolgreich.  
  
 Darüber hinaus einige Webserver und Anwendungssoftware, z. B. Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], enthalten eine Liste von Dateien und Dateitypen, die nicht heruntergeladen werden können. Z. B. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] wird verhindert, dass das Herunterladen von Dateien für alle "Web.config". Diese Dateien möglicherweise vertraulichen Informationen wie Benutzernamen und Kennwörter enthalten.  
  
 Obwohl diese Einschränkung für das Herunterladen von Core unproblematisch [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Dateien wie Manifeste und Assemblys, diese Einschränkung kann verhindern, dass Sie Download von Datendateien, die Bestandteil Ihrer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung. In [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], Sie können diesen Fehler beheben, durch das Entfernen des Handlers, der verhindert, dass Download dieser Dateien aus der IIS-Konfigurations-Manager. Finden Sie unter der IIS-Server-Dokumentation für zusätzliche Details.  
  
 Einige Webserver können es sich um Dateien mit Erweiterungen wie z. B. dll-Datei, config und MDF blockieren. Windows-basierten Anwendungen beinhalten in der Regel einige dieser Erweiterungen. Wenn ein Benutzer versucht, Sie führen eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung, die eine blockierte Datei auf einem Webserver zugreift, ein Fehler ausgegeben. Anstatt alle Dateierweiterungen, Blockierung [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] jeder Datei der Anwendung mit der Dateierweiterung ".deploy" veröffentlicht, in der Standardeinstellung. Aus diesem Grund muss der Administrator nur so konfigurieren Sie den Webserver so Entsperren die folgenden drei Erweiterungen:  
  
- APPLICATION  
  
- MANIFEST  
  
- DEPLOY  
  
  Allerdings können Sie diese Option deaktivieren, indem Sie deaktivieren die **Dateierweiterung ".deploy" verwenden** option die [Publish Options Dialog Box](http://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), in diesem Fall Sie den Webserver für alle Erweiterungen zulassen konfigurieren müssen in der Anwendung verwendet.  
  
  Sie müssen konfigurieren ". manifest".application und ".deploy", z. B. Wenn Sie IIS verwenden, in denen Sie nicht installiert haben, die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], oder wenn Sie einen anderen Webserver (z. B. Apache) verwenden.  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce und Secure Sockets Layer (SSL)  
 Ein [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung wird über SSL, außer wenn eine Eingabeaufforderung zu dem SSL-Zertifikat von Internet Explorer löst problemlos funktionieren. Die Eingabeaufforderung kann ausgelöst werden, wenn vorhanden ist, dass ein Problem mit dem Zertifikat, z. B. wenn die Websitenamen nicht übereinstimmen oder das Zertifikat abgelaufen ist. Zu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] über eine SSL-Verbindung funktioniert, stellen Sie sicher, dass das Zertifikat auf dem neuesten Stand ist und dass die Daten des Zertifikats die Daten des Standorts übereinstimmt.  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce und Proxy-Authentifizierung  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bietet Unterstützung für die integrierte Windows-Proxy-Authentifizierung, die ab .NET Framework 3.5. Es sind keine bestimmten "Machine.config"-Direktiven erforderlich. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bietet keine Unterstützung für andere Authentifizierungsprotokolle wie Standard- oder Digestauthentifizierung.  
  
 Sie können auch einen Hotfix für .NET Framework 2.0 zum Aktivieren dieser Funktion anwenden. Weitere Informationen finden Sie unter http://go.microsoft.com/fwlink/?LinkId=158730.  
  
 Weitere Informationen finden Sie unter [ \<DefaultProxy >-Element (Netzwerkeinstellungen)](http://msdn.microsoft.com/library/9d663c4b-07b4-4f6f-9b12-efbd3630354f).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce und Web-Browser-Kompatibilität  
 Derzeit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Installationen nur gestartet, wenn die URL für das Bereitstellungsmanifest mit Internet Explorer geöffnet wird. Eine Bereitstellung, deren URL durch eine andere Anwendung, z. B. Microsoft Office Outlook, gestartet wird, wird erfolgreich gestartet werden, nur, wenn Internet Explorer als Standardbrowser festgelegt ist.  
  
> [!NOTE]
>  Mozilla Firefox wird unterstützt, wenn der Bereitstellungsanbieter nicht leer ist oder die Erweiterung von Microsoft .NET Framework-Assistent ist installiert. Diese Erweiterung wird mit .NET Framework 3.5 SP1 verpackt. Die NPWPF-Plug-in wird bei Bedarf zur XBAP-Unterstützung aktiviert.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>Aktivieren von ClickOnce-Anwendungen über die Skriptprogrammierung Browser  
 Wenn Sie eine benutzerdefinierte Webseite entwickelt haben, die startet eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung mithilfe von Active Scripting, vorkommen, dass die Anwendung nicht auf einigen Computern zu starten. Internet Explorer enthält eine Einstellung namens **automatisch aufgefordert, für den Download der Datei**, die dieses Verhalten wirkt sich auf. Diese Einstellung ist verfügbar, auf die **Sicherheit** Registerkarte die **Optionen** Menü, das dieses Verhalten wirkt sich auf. Es heißt **automatisch aufgefordert, für den Download der Datei**, und es wird aufgeführt, unter der **Downloads** Kategorie. Die Eigenschaft wird festgelegt, um **aktivieren** standardmäßig für die Webseiten im Intranet und **deaktivieren** standardmäßig für Internet-Webseiten. Wenn diese Einstellung festgelegt wurde, um **deaktivieren**, jeder Versuch, aktivieren Sie eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung programmgesteuert (z. B. durch die URL zum Zuweisen der `document.location` Eigenschaft) blockiert werden. Unter diesen Umständen können Benutzer Anwendungen nur über eine vom Benutzer initiierte-Download, z. B. durch Klicken auf einen Link aus, legen Sie auf die URL der Anwendung starten.  
  
## <a name="additional-server-configuration-issues"></a>Weitere Probleme der Serverkonfiguration  
  
##### <a name="administrator-permissions-required"></a>Administratorberechtigungen erforderlich  
 Wenn Sie mit HTTP veröffentlichen, müssen über Administratorberechtigungen auf dem Zielserver verfügen. IIS sind diese Berechtigungen benötigt. Wenn Sie nicht über HTTP veröffentlichen, müssen Sie nur für den Zielpfad Schreibberechtigung.  
  
##### <a name="server-authentication-issues"></a>Probleme mit Server-Authentifizierung  
 Wenn Sie mit einem Remoteserver, die "Anonymer Zugriff veröffentlichen" deaktiviert wurde, erhalten Sie die folgende Warnung:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  NTLM (NT-Abfrage / Rückmeldung)-Authentifizierung funktioniert, wenn die Website zur Eingabe von Anmeldeinformationen als die standardmäßigen Anmeldeinformationen fordert, und klicken Sie im Dialogfeld "Sicherheit", die Sie auf möglich **OK** Wenn Sie aufgefordert werden, wenn die angegebene gespeichert werden soll Anmeldeinformationen für zukünftige Sitzungen. Diese problemumgehung funktioniert jedoch nicht für die Standardauthentifizierung.  
  
## <a name="using-third-party-web-servers"></a>Mithilfe von Drittanbieter-Webservern  
 Bei der Bereitstellung einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung von einem Webserver als IIS können Sie ein Problem auftreten, wenn der Server, den falschen Inhaltstyp für Schlüssel zurückgibt [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Dateien, z. B. das Bereitstellungsmanifest und Anwendungsmanifest. Um dieses Problem zu beheben, finden Sie in Ihrem Webserver-Hilfe, die Dokumentation über das Hinzufügen von neuer Inhaltstypen an den Server, und stellen Sie sicher, dass alle Datei Namen Erweiterung Zuordnungen in der folgenden Tabelle aufgeführt sind.  
  
|Dateinamenerweiterung|Inhaltstyp|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce und zugeordnete Laufwerke  
 Wenn Sie Visual Studio zum Veröffentlichen einer ClickOnce-Anwendung verwenden, können nicht Sie ein zugeordnetes Laufwerk als Speicherort der Installation angeben. Allerdings können Sie die ClickOnce-Anwendung von einem zugeordneten Laufwerk zu installieren, mit dem Manifest-Generator und der Editor (Mage.exe und MageUI.exe) ändern. Weitere Informationen finden Sie unter [Mage.exe (Tool zum Generieren und Bearbeiten von Manifesten)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) und [MageUI.exe (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>FTP-Protokoll für die Installation von Anwendungen wird nicht unterstützt.  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] unterstützt das Installieren von Anwendungen von HTTP 1.1-Webserver oder Dateiserver. FTP, File Transfer Protocol, wird nicht unterstützt, für die Installation von Anwendungen. Sie können FTP verwenden, um nur Anwendungen zu veröffentlichen. In der folgende Tabelle werden diese Unterschiede zusammengefasst:  
  
|URL-Typ|Beschreibung|  
|--------------|-----------------|  
|ftp://|Sie können Veröffentlichen einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung mit diesem Protokoll.|  
|http://|Installation kann ein [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung mit diesem Protokoll.|  
|https://|Installation kann ein [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung mit diesem Protokoll.|  
|file://|Installation kann ein [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung mit diesem Protokoll.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows-Firewall  
 Windows XP SP2 aktiviert standardmäßig die Windows-Firewall. Wenn Sie Ihre Anwendung auf einem Computer, die Windows XP installiert ist entwickeln, können Sie weiterhin auf veröffentlichen, und führen [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen vom lokalen Server, auf denen IIS ausgeführt wird. Allerdings können nicht Sie den Server zugreifen, der IIS auf einem anderen Computer ausgeführt wird, es sei denn, Sie die Windows-Firewall zu öffnen. Informationen zum Verwalten der Windows-Firewall finden Sie in der Windows-Hilfe.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: Aktivieren Sie FrontPage-Servererweiterungen  
 FrontPage-Servererweiterungen von Microsoft ist erforderlich, für die Veröffentlichung von Anwendungen auf einem Windows-Webserver, der HTTP verwendet.  
  
 Standardmäßig verfügt Windows Server nicht über FrontPage-Servererweiterungen installiert. Wenn Sie verwenden möchten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] um an einen Webserver für Windows Server zu veröffentlichen, die mit FrontPage-Servererweiterungen HTTP verwendet, müssen Sie zunächst die FrontPage-Servererweiterungen installieren. Sie können die Installation ausführen, indem mithilfe des Verwaltungstools für die Serververwaltung in Windows Server.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server: Gesperrte Inhaltstypen  
 IIS auf [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] Sperren nach-unten-alle Dateitypen mit Ausnahme bestimmter bekannten Inhaltstypen (z. B. htm, HTML, txt usw.). So aktivieren Sie die Bereitstellung von [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen, die diesen Server verwenden, müssen Sie zum Ändern der IIS-Einstellungen, um zuzulassen, Herunterladen von Dateien des Typs Application Manifest und auf andere benutzerdefinierte Dateitypen, die von Ihrer Anwendung verwendet.  
  
 Wenn Sie die Bereitstellung mit einem IIS-Server, führen Sie inetmgr.exe und fügen Sie neue Dateitypen für die Standardwebseite hinzu:  
  
- Für die Application- und Manifest-Erweiterungen muss der MIME-Typ "Application/X-ms-Anwendung." Für andere Dateitypen muss der MIME-Typ "Application/Octet-Stream".  
  
- Bei der Erstellung eines MIME-Typs mit der Erweiterung "*" und den MIME-Typ "Application/Octet-Stream", können sie Dateien mit entsperrt Dateityp heruntergeladen werden. (Allerdings blockierte Typen wie z. B. aspx- und ASMX nicht heruntergeladen werden können.)  
  
  Spezifische Anweisungen zum Konfigurieren von MIME-Typen für Windows Server, finden Sie in Microsoft Knowledge Base-Artikel KB326965, "IIS 6.0 wird nicht dienen unbekannte MIME-Typen" am [ http://support.microsoft.com/default.aspx?scid=kb; En-us; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>Content-Type-Zuordnungen  
 Wenn Sie über HTTP veröffentlichen zu können, muss der Inhaltstyp (auch bekannt als MIME-Typ) für die Application-Datei "Application/X-ms-Anwendung." Wenn man [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] auf dem Server installiert, dies wird für Sie automatisch festgelegt. Wenn dies nicht installiert ist, müssen Sie eine MIME-Typ-Verknüpfung erstellen die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungsstammverzeichnis (oder den gesamten Server).  
  
 Wenn Sie die Bereitstellung mit einem IIS-Server, führen Sie inetmgr.exe und fügen Sie neuen Inhaltstyp "Application/X-ms-Application" für die Erweiterung .application hinzu.  
  
## <a name="http-compression-issues"></a>Probleme bei der HTTP-Komprimierung  
 Mit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], können Sie ausführen, Downloads, die HTTP-Komprimierung zu verwenden, eine Web-Server-Technologie, die den GZIP-Algorithmus verwendet, um einen Datenstrom zu komprimieren, bevor Sie den Datenstrom an den Client gesendet. Der Client – in diesem Fall [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]– dekomprimiert den Stream vor dem Lesen der Dateien.  
  
 Wenn Sie IIS verwenden, können Sie ganz einfach, HTTP-Komprimierung aktivieren. Wenn Sie HTTP-Komprimierung aktivieren, es ist jedoch nur aktiviert für bestimmte Dateitypen – nämlich, HTML- und Text-Dateien. Um die Komprimierung für Assemblys (DLL) zu aktivieren, müssen XML (XML), Bereitstellungsmanifeste (.application) und Anwendungsmanifeste (. manifest) Sie diese Dateitypen zur Liste der Typen für die IIS komprimieren hinzufügen. Bis Sie die Dateitypen zu Ihrer Bereitstellung hinzufügen, werden nur Text und HTML-Dateien komprimiert.  
  
 Ausführliche Anweisungen für IIS finden Sie unter [wie zusätzliche Dokumenttypen für HTTP-Komprimierung angegeben](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)   
 [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md)
