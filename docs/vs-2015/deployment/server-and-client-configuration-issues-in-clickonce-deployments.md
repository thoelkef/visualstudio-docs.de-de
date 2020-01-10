---
title: Probleme mit der Server-und Client Konfiguration in ClickOnce-bereit Stellungen | Microsoft-Dokumentation
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
ms.openlocfilehash: 97c8c50dec18d730d92021d88361701a96b99590
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844988"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Probleme mit der Server- und Clientkonfiguration in ClickOnce-Bereitstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Internetinformationsdienste (IIS) unter Windows Server verwenden und die Bereitstellung einen Dateityp enthält, den Windows nicht erkennt (z. b. eine Microsoft Word-Datei), lehnt IIS die Übertragung dieser Datei ab, und die Bereitstellung kann nicht erfolgreich ausgeführt werden.  
  
 Darüber hinaus enthalten einige Webserver und Webanwendungs Software, z. b. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], eine Liste von Dateien und Dateitypen, die Sie nicht herunterladen können. Beispielsweise wird durch [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] verhindert, dass alle Web. config-Dateien heruntergeladen werden. Diese Dateien können vertrauliche Informationen enthalten, wie z. b. Benutzernamen und Kenn Wörter.  
  
 Obwohl diese Einschränkung keine Probleme beim Herunterladen von Kern [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Dateien (z. b. Manifeste und Assemblys) verursachen sollte, kann diese Einschränkung verhindern, dass Sie Datendateien herunterladen, die als Teil ihrer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung enthalten In [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]können Sie diesen Fehler beheben, indem Sie den Handler entfernen, der das Herunterladen solcher Dateien aus dem IIS-Konfigurations-Manager untersagt. Weitere Informationen finden Sie in der Dokumentation zum IIS-Server.  
  
 Einige Webserver blockieren möglicherweise Dateien mit Erweiterungen wie ". dll", ". config" und ". mdf". Windows-basierte Anwendungen enthalten in der Regel Dateien mit einigen dieser Erweiterungen. Wenn ein Benutzer versucht, eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung auszuführen, die auf eine blockierte Datei auf einem Webserver zugreift, führt dies zu einem Fehler. Anstatt alle Dateierweiterungen zu entsperren, veröffentlicht [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] jede Anwendungsdatei standardmäßig mit der Dateierweiterung ". bereitstellen". Daher muss der Administrator den Webserver nur so konfigurieren, dass die Blockierung der folgenden drei Dateierweiterungen blockiert wird:  
  
- APPLICATION  
  
- MANIFEST  
  
- DEPLOY  
  
  Sie können diese Option jedoch deaktivieren, indem Sie im [Dialog Feld "Veröffentlichungs Optionen](https://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592)" die Option **". Bereitstellungs Dateierweiterung verwenden** " deaktivieren. in diesem Fall müssen Sie den Webserver so konfigurieren, dass alle in der Anwendung verwendeten Dateierweiterungen entsperrt werden.  
  
  Sie müssen die. Manifest-, Application-und.-Bereitstellung konfigurieren, z. b. Wenn Sie IIS verwenden, bei dem Sie die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]nicht installiert haben, oder wenn Sie einen anderen Webserver (z. b. Apache) verwenden.  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce und Secure Sockets Layer (SSL)  
 Eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung funktioniert problemlos über SSL, außer wenn Internet Explorer eine Aufforderung zum SSL-Zertifikat auslöst. Die Eingabeaufforderung kann ausgelöst werden, wenn ein Problem mit dem Zertifikat vorliegt, z. b. wenn die Standortnamen nicht stimmen oder das Zertifikat abgelaufen ist. Stellen Sie sicher, dass das Zertifikat auf dem neuesten Stand ist und dass die Zertifikat Daten mit den Standortdaten übereinstimmen, um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] über eine SSL-Verbindung zu arbeiten.  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce und Proxy Authentifizierung  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bietet Unterstützung für die integrierte Windows-Proxy Authentifizierung ab .NET Framework 3,5. Bestimmte Machine. config-Direktiven sind nicht erforderlich. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bietet keine Unterstützung für andere Authentifizierungsprotokolle, wie z. b. Basic oder Digest.  
  
 Sie können auch einen Hotfix auf .NET Framework 2,0 anwenden, um dieses Feature zu aktivieren. Weitere Informationen finden Sie unter https://go.microsoft.com/fwlink/?LinkId=158730.  
  
 Weitere Informationen finden Sie unter [\<defaultProxy >-Element (Netzwerkeinstellungen)](https://msdn.microsoft.com/library/9d663c4b-07b4-4f6f-9b12-efbd3630354f).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce und Webbrowser Kompatibilität  
 Zurzeit werden [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Installationen nur gestartet, wenn die URL des Bereitstellungs Manifests mithilfe von Internet Explorer geöffnet wird. Eine Bereitstellung, deren URL von einer anderen Anwendung, z. b. Microsoft Office Outlook, gestartet wird, wird nur dann erfolgreich gestartet, wenn Internet Explorer als Standard Webbrowser festgelegt ist.  
  
> [!NOTE]
> Mozilla Firefox wird unterstützt, wenn der Bereitstellungs Anbieter nicht leer ist oder die Erweiterung des Microsoft .NET Framework-Assistenten installiert ist. Diese Erweiterung ist mit .NET Framework 3,5 SP1 verpackt. Bei der XBAP-Unterstützung wird das npwpf-Plug-in bei Bedarf aktiviert.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>Aktivieren von ClickOnce-Anwendungen mithilfe von Browser Skripts  
 Wenn Sie eine benutzerdefinierte Webseite entwickelt haben, die eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung mithilfe von Active Scripting startet, werden Sie möglicherweise feststellen, dass die Anwendung auf einigen Computern nicht gestartet wird. Internet Explorer enthält eine Einstellung, die als **Automatische Eingabeaufforderung für Dateidownloads**bezeichnet wird, was sich auf dieses Verhalten auswirkt. Diese Einstellung ist im Menü **Optionen** auf der Registerkarte **Sicherheit** verfügbar und wirkt sich auf dieses Verhalten aus. Sie wird als **Automatische Aufforderung zum Herunterladen von Dateien**bezeichnet und unterhalb der Kategorie **Downloads** aufgeführt. Die-Eigenschaft ist so festgelegt, dass Sie für Intranetwebseiten standardmäßig **aktiviert** und für Internet Webseiten standardmäßig **deaktiviert** wird. Wenn diese Einstellung auf **Deaktivieren**festgelegt ist, wird jeder Versuch, eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung Programm gesteuert zu aktivieren (z. b. durch Zuweisen der URL zur `document.location`-Eigenschaft) blockiert. Unter diesen Umständen können Benutzer Anwendungen nur über einen vom Benutzer initiierten Download starten, indem Sie beispielsweise auf einen Hyperlink klicken, der auf die URL der Anwendung festgelegt ist.  
  
## <a name="additional-server-configuration-issues"></a>Zusätzliche Probleme bei der Server Konfiguration  
  
##### <a name="administrator-permissions-required"></a>Administrator Berechtigungen erforderlich  
 Wenn Sie mit http veröffentlichen, müssen Sie über Administrator Berechtigungen auf dem Zielserver verfügen. IIS erfordert diese Berechtigungsstufe. Wenn Sie nicht mit http veröffentlichen, benötigen Sie nur die Schreib Berechtigung für den Zielpfad.  
  
##### <a name="server-authentication-issues"></a>Probleme mit der Server Authentifizierung  
 Wenn Sie auf einem Remote Server veröffentlichen, auf dem "Anonymer Zugriff" deaktiviert ist, erhalten Sie die folgende Warnung:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
> Sie können die NTLM-Authentifizierung (NT Challenge-Response) aktivieren, wenn die Website zur Eingabe von Anmelde Informationen verwendet, die nicht Ihren Standard Anmelde Informationen entsprechen, und Sie im Dialogfeld Sicherheit auf **OK** klicken, wenn Sie dazu aufgefordert werden, die angegebenen Anmelde Informationen für zukünftige Sitzungen zu speichern. Diese Problem Umgehung funktioniert jedoch nicht bei der Standard Authentifizierung.  
  
## <a name="using-third-party-web-servers"></a>Verwenden von Drittanbieter-Webservern  
 Wenn Sie eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung von einem anderen Webserver als IIS bereitstellen, tritt möglicherweise ein Problem auf, wenn der Server den falschen Inhaltstyp für Schlüssel [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Dateien zurückgibt, wie z. b. das Bereitstellungs Manifest und das Anwendungs Manifest. Um dieses Problem zu beheben, finden Sie in der Hilfe Dokumentation Ihres Webservers Informationen zum Hinzufügen neuer Inhaltstypen zum Server, und stellen Sie sicher, dass alle in der folgenden Tabelle aufgeführten Dateinamen-Erweiterungs Zuordnungen vorhanden sind.  
  
|Dateinamenerweiterung|Art des Inhalts|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce und zugeordnete Laufwerke  
 Wenn Sie Visual Studio verwenden, um eine ClickOnce-Anwendung zu veröffentlichen, können Sie kein zugeordnetes Laufwerk als Installations Speicherort angeben. Sie können jedoch die ClickOnce-Anwendung so ändern, dass Sie von einem zugeordneten Laufwerk aus mithilfe des Manifest-Generators und des Editors ("Mage. exe" und "MageUI. exe") installiert wird. Weitere Informationen finden Sie unter [Mage.exe (Tool zum Generieren und Bearbeiten von Manifesten)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) und [MageUI.exe (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>FTP-Protokoll wird für die Installation von Anwendungen nicht unterstützt  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] unterstützt die Installation von Anwendungen von einem beliebigen HTTP 1,1-Webserver oder-Dateiserver. FTP, die Dateiübertragungsprotokoll, wird für die Installation von Anwendungen nicht unterstützt. Sie können FTP nur zum Veröffentlichen von Anwendungen verwenden. In der folgenden Tabelle werden diese Unterschiede zusammengefasst:  
  
|URL-Typ|Beschreibung|  
|--------------|-----------------|  
|ftp://|Sie können eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung mithilfe dieses Protokolls veröffentlichen.|  
|http://|Mithilfe dieses Protokolls können Sie eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung installieren.|  
|https://|Mithilfe dieses Protokolls können Sie eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung installieren.|  
|file://|Mithilfe dieses Protokolls können Sie eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung installieren.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows Firewall  
 Standardmäßig wird die Windows-Firewall von Windows XP SP2 aktiviert. Wenn Sie Ihre Anwendung auf einem Computer entwickeln, auf dem Windows XP installiert ist, können Sie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen weiterhin auf dem lokalen Server veröffentlichen und ausführen, auf dem IIS ausgeführt wird. Sie können jedoch nicht auf den Server zugreifen, auf dem IIS von einem anderen Computer ausgeführt wird, sofern Sie nicht die Windows-Firewall öffnen. Anweisungen zur Verwaltung der Windows-Firewall finden Sie in der Windows-Hilfe.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: FrontPage-Server Erweiterungen aktivieren  
 Zum Veröffentlichen von Anwendungen auf einem Windows-Webserver, der HTTP verwendet, sind FrontPage-Servererweiterungen von Microsoft erforderlich.  
  
 Standardmäßig ist auf Windows Server keine FrontPage-Servererweiterungen installiert. Wenn Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verwenden möchten, um auf einem Windows Server-Webserver zu veröffentlichen, der HTTP mit FrontPage-Servererweiterungen verwendet, müssen Sie zuerst FrontPage-Servererweiterungen installieren. Sie können die Installation mithilfe des Verwaltungs Tools Server verwalten in Windows Server ausführen.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server: gesperrte Inhaltstypen  
 IIS auf [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] sperrt alle Dateitypen außer für bestimmte bekannte Inhaltstypen (z. b. htm, HTML, txt usw.). Um die Bereitstellung von [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen mit diesem Server zu ermöglichen, müssen Sie die IIS-Einstellungen ändern, um das Herunterladen von Dateien vom Typ ". Application", "Manifest" und anderen von der Anwendung verwendeten benutzerdefinierten Dateitypen zuzulassen.  
  
 Wenn Sie die Bereitstellung über einen IIS-Server durchführen, führen Sie inetmgr. exe aus, und fügen Sie neue Dateitypen für die Standard Webseite hinzu:  
  
- Für die Erweiterungen ". Application" und ". Manifest" sollte der MIME-Typ "application/x-ms-application" lauten. Bei anderen Dateitypen sollte der MIME-Typ "Application/Octett-Stream" lauten.  
  
- Wenn Sie einen MIME-Typ mit der Erweiterung "*" und dem MIME-Typ "Application/Octett-Stream" erstellen, können Dateien vom Typ "nicht blockierter Dateityp" heruntergeladen werden. (Blockierte Dateitypen wie ASPX und ASMX können jedoch nicht heruntergeladen werden.)  
  
  Spezifische Anweisungen zum Konfigurieren von MIME-Typen unter Windows Server finden Sie im Microsoft Knowledge Base-Artikel KB326965, "IIS 6,0 bedient keine unbekannten MIME-Typen" unter [https://support.microsoft.com/default.aspx?scid=kb; en-US; 326965](https://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>Inhaltstyp Zuordnungen  
 Beim Veröffentlichen über HTTP sollte der Inhaltstyp (auch als MIME-Typ bezeichnet) für die Anwendungsdatei "application/x-ms-application" lauten. Wenn Sie [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] auf dem Server installiert haben, wird dieser automatisch für Sie festgelegt. Wenn dies nicht installiert ist, müssen Sie eine MIME-Typzuordnung für den [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Application vroot (oder den gesamten Server) erstellen.  
  
 Wenn Sie die Bereitstellung über einen IIS-Server ausführen, führen Sie inetmgr. exe aus, und fügen Sie den neuen Inhaltstyp "application/x-ms-application" für die Erweiterung ". Application" hinzu.  
  
## <a name="http-compression-issues"></a>HTTP-Komprimierungs Probleme  
 Mit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]können Sie Downloads ausführen, die die HTTP-Komprimierung verwenden, eine Webserver Technologie, die den gzip-Algorithmus zum Komprimieren eines Datenstroms verwendet, bevor der Datenstrom an den Client gesendet wird. Der Client – in diesem Fall, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]– den Stream vor dem Lesen der Dateien dekomprimiert.  
  
 Wenn Sie IIS verwenden, können Sie die HTTP-Komprimierung problemlos aktivieren. Wenn Sie die HTTP-Komprimierung aktivieren, ist Sie jedoch nur für bestimmte Dateitypen aktiviert – HTML-und Textdateien. Um die Komprimierung für Assemblys (. dll), XML (XML), Bereitstellungs Manifeste (. Application) und Anwendungs Manifeste (. manifest) zu aktivieren, müssen Sie diese Dateitypen der Liste der Typen hinzufügen, die von IIS komprimiert werden sollen. Bis Sie die Dateitypen der Bereitstellung hinzufügen, werden nur Text-und HTML-Dateien komprimiert.  
  
 Ausführliche Anweisungen für IIS finden Sie unter [Angeben zusätzlicher Dokumenttypen für die HTTP-Komprimierung](https://support.microsoft.com/kb/234497).  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei ClickOnce](../deployment/troubleshooting-clickonce-deployments.md) -bereit Stellungen   
 [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md)
