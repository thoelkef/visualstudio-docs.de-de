---
title: "Server and Client Configuration Issues in ClickOnce Deployments | Microsoft Docs"
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
  - "deploying applications, ClickOnce"
  - "troubleshooting ClickOnce deployments"
  - "ClickOnce deployment, troubleshooting"
  - "Windows applications, ClickOnce deployments"
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Server and Client Configuration Issues in ClickOnce Deployments
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie Internetinformationsdienste \(IIS\) unter Windows Server verwenden und die Bereitstellung einen Dateityp enthält, der von Windows nicht erkannt wird, z. B. eine Microsoft Word\-Datei, wird diese Datei von IIS nicht übertragen, und die Bereitstellung schlägt fehl.  
  
 Außerdem enthalten bestimmte Webserver und manche Webanwendungssoftware, z. B. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], eine Liste von Dateien und Dateitypen, die nicht heruntergeladen werden können.  Beispielsweise verhindert [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] den Download aller Web.config\-Dateien.  Diese Dateien enthalten möglicherweise vertrauliche Informationen z. B. Benutzernamen und Kennwörter.  
  
 Beim Download von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Kerndateien, z. B. Manifeste und Assemblys, ist diese Einschränkung i. d. R. unproblematisch, allerdings kann durch diese Einschränkung der Download von Datendateien verhindert werden, die Bestandteil der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung sind.  In [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] können Sie den Fehler beheben, indem Sie den Handler, der den Download dieser Dateien verhindert, aus dem IIS\-Konfigurations\-Manager entfernen.  Weitere Informationen finden Sie in der IIS\-Serverdokumentation.  
  
 Einige Webserver blockieren möglicherweise Dateien mit Erweiterungen wie .dll, .config und .mdf.  Windows\-basierte Anwendungen enthalten in der Regel Dateien mit diesen Erweiterungen.  Wenn ein Benutzer versucht, eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung auszuführen, die auf eine blockierte Datei auf einem Webserver zugreift, führt dies zu einer Fehlermeldung.  Anstatt die Blockierung aller Dateierweiterungen aufzuheben, veröffentlicht [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] standardmäßig jede Anwendungsdatei mit der Dateierweiterung ".deploy".  Deshalb muss der Administrator den Webserver nur so konfigurieren, dass die Blockierung der folgenden drei Dateierweiterungen aufgehoben wird:  
  
-   APPLICATION  
  
-   MANIFEST  
  
-   DEPLOY  
  
 Sie können diese Option aber deaktivieren, indem Sie die Auswahl der Option **Dateierweiterung ".deploy" verwenden** im [Publish Options Dialog Box](http://msdn.microsoft.com/de-de/fd9baa1b-7311-4f9e-8ffb-ae50cf110592) aufheben. In diesem Fall müssen Sie den Webserver so konfigurieren, dass die Blockierung aller von der Anwendung verwendeten Dateierweiterungen aufgehoben wird.  
  
 Dies gilt z. B. für die Dateierweiterungen MANIFEST, APPLICATION und DEPLOY, wenn Sie IIS verwenden und [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] nicht installiert ist, oder wenn Sie einen anderen Webserver verwenden \(z. B. Apache\).  
  
## ClickOnce und SSL \(Secure Sockets Layer\)  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen werden über SSL problemlos ausgeführt, es sei denn, in Internet Explorer wird eine Eingabeaufforderung zum SSL\-Zertifikat angezeigt.  Die Eingabeaufforderung kann angezeigt werden, wenn das Zertifikat einen Fehler aufweist, z. B. wenn die Sitenamen nicht übereinstimmen oder das Zertifikat abgelaufen ist.  Damit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] über eine SSL\-Verbindung ausgeführt werden kann, stellen Sie sicher, dass das Zertifikat aktuell ist und dass die Zertifikatdaten mit den Sitedaten übereinstimmen.  
  
## ClickOnce und Proxyauthentifizierung  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bietet ab .NET Framework 3.5 Unterstützung für die Windows Integrated Proxyauthentifizierung.  Es sind keine spezifischen machine.config\-Direktiven erforderlich.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bietet keine Unterstützung für andere Authentifizierungsprotokolle wie Basic oder Digest.  
  
 Sie können auch einen Hotfix für .NET Framework 2.0 anwenden, um diese Funktion zu aktivieren.  Weitere Informationen finden Sie unter "http:\/\/go.microsoft.com\/fwlink\/?LinkId\=158730".  
  
 Weitere Informationen finden Sie unter [\<defaultProxy\>\-Element \(Netzwerkeinstellungen\)](../Topic/%3CdefaultProxy%3E%20Element%20\(Network%20Settings\).md).  
  
## ClickOnce und Webbrowserkompatibilität  
 Derzeit werden [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Installationen nur gestartet, wenn die URL zum Bereitstellungsmanifest mit Internet Explorer geöffnet wird.  Eine Bereitstellung, deren URL von einer anderen Anwendung wie beispielsweise Microsoft Office Outlook gestartet wird, startet nur erfolgreich, wenn Internet Explorer als Standardwebbrowser eingestellt ist.  
  
> [!NOTE]
>  Mozilla Firefox wird unterstützt, wenn der Bereitstellungsanbieter nicht leer ist oder die Erweiterung für den Microsoft .NET Framework\-Assistenten installiert wurde.  Diese Erweiterung ist in .NET Framework 3.5 SP1 enthalten.  Zur XBAP\-Unterstützung wird das NPWPF\-Plug\-In nach Bedarf aktiviert.  
  
## Aktivieren von ClickOnce\-Anwendungen über Browserskripterstellung  
 Wenn Sie eine benutzerdefinierte Webseite entwickelt haben, die eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung mithilfe von Active Scripting startet, stellen Sie möglicherweise fest, dass die Anwendung auf einigen Computern nicht gestartet werden kann.  Internet Explorer enthält die Einstellung **Automatische Eingabeaufforderung für Dateidownloads**, die dieses Verhalten beeinflusst.  Diese Einstellung ist auf der Registerkarte **Sicherheit** im Menü **Optionen**, das dieses Verhalten beeinflusst, verfügbar.  Sie wird als **Automatische Eingabeaufforderung für Dateidownloads** bezeichnet und wird unter der Kategorie **Downloads** aufgeführt.  Die Eigenschaft ist für Intranetwebseiten standardmäßig auf **Aktivieren** und für Internetwebseiten standardmäßig auf **Deaktivieren** festgelegt.  Wenn für diese Einstellung **Deaktivieren** festgelegt ist, wird jeder Versuch blockiert, eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung programmgesteuert zu aktivieren \(indem beispielsweise ihre URL der `document.location`\-Eigenschaft zugewiesen wird\).  Unter diesen Umständen können Benutzer Anwendungen nur über einen selbst eingeleiteten Download starten, beispielsweise durch Klicken auf einen Link, für den die Anwendungs\-URL festgelegt ist.  
  
## Weitere Probleme mit der Serverkonfiguration  
  
##### Administratorberechtigungen erforderlich  
 Sie müssen über Administratorberechtigungen für den Zielserver verfügen, wenn Sie mit HTTP veröffentlichen.  Für IIS ist diese Berechtigungsebene erforderlich.  Wenn Sie nicht mit HTTP veröffentlichen, ist lediglich eine Schreibberechtigung für den Zielpfad erforderlich.  
  
##### Probleme mit der Serverauthentifizierung  
 Beim Veröffentlichen auf einem Remoteserver mit deaktivierter Option "Anonyme Anmeldung" erhalten Sie die folgende Warnung:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  Sie können NTLM\-Authentifizierung \(NT\-Abfrage\/Rückmeldung\) verwenden, wenn auf der Site Anmeldeinformationen oder andere Informationen als die Standardanmeldeinformationen angegeben werden müssen. Klicken Sie im Sicherheitsdialogfeld bei entsprechender Aufforderung auf **OK**, wenn Sie die angegebenen Anmeldeinformationen für zukünftige Sitzungen speichern möchten.  Diese Problemumgehung ist für die Standardauthentifizierung jedoch nicht möglich.  
  
## Verwenden von Webservern von Drittanbietern  
 Bei der Bereitstellung einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung auf einem anderen Webserver als einem IIS\-Server können Probleme auftreten, wenn der Server den falschen Inhaltstyp für wichtige [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Dateien, z. B. Bereitstellungsmanifest und Anwendungsmanifest, zurückgibt.  Um dieses Problem zu beheben, informieren Sie sich in der Hilfedokumentation des Webservers darüber, wie dem Server neue Inhaltstypen hinzugefügt werden, und stellen Sie sicher, dass die in der folgenden Tabelle aufgeführten Dateinamenerweiterungen den entsprechenden Inhaltstypen zugeordnet sind.  
  
|Dateinamenerweiterung|Inhaltstyp|  
|---------------------------|----------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## ClickOnce und zugeordnete Laufwerke  
 Wenn Sie Visual Studio verwenden, um eine ClickOnce\-Anwendung zu veröffentlichen, können Sie kein zugeordnetes Laufwerk als Installationspfad angeben.  Sie können für die ClickOnce\-Anwendung jedoch angeben, dass sie von einem zugeordneten Laufwerk installiert werden soll, indem Sie den Manifestgenerator und den Manifest\-Editor \(Mage.exe und MageUI.exe\) verwenden.  Weitere Informationen finden Sie unter [Mage.exe \(Tool zum Generieren und Bearbeiten von Manifesten\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md) und [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  
  
## FTP\-Protokoll wird nicht zum Installieren von Anwendungen unterstützt  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] unterstützt die Installation von Anwendungen über Webserver oder Dateiserver mit HTTP 1.1.  FTP, das File Transfer Protocol, wird nicht zum Installieren von Anwendungen unterstützt.  Sie können FTP nur zum Veröffentlichen von Anwendungen verwenden.  In der folgenden Tabelle werden die Unterschiede zusammengefasst:  
  
|URL\-Typ|Beschreibung|  
|--------------|------------------|  
|ftp:\/\/|Mit diesem Protokoll können Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung veröffentlichen.|  
|http:\/\/|Mit diesem Protokoll können Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung installieren.|  
|https:\/\/|Mit diesem Protokoll können Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung installieren.|  
|file:\/\/|Mit diesem Protokoll können Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung installieren.|  
  
## Windows XP SP2: Windows\-Firewall  
 Die Windows\-Firewall ist in Windows XP SP2 standardmäßig aktiviert.  Wenn Sie Anwendungen unter Windows XP entwickeln, können Sie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen trotzdem vom lokalen Server, auf dem IIS installiert ist, veröffentlichen und ausführen.  Sie können von einem anderen Computer jedoch nur auf den Server zugreifen, auf dem ISS ausgeführt wird, wenn Sie die Windows\-Firewall öffnen.  Anweisungen zur Verwaltung der Windows\-Firewall finden Sie in der Windows\-Hilfe.  
  
## Windows Server: Aktivieren von FrontPage\-Servererweiterungen  
 Zum Veröffentlichen von Anwendungen auf einem Windows\-Webserver mit HTTP sind FrontPage\-Servererweiterungen von Microsoft erforderlich.  
  
 FrontPage\-Servererweiterungen sind nicht standardmäßig mit Windows Server installiert.  Wenn Sie mithilfe von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf einem Windows Server\-Webserver veröffentlichen möchten, der HTTP mit FrontPage\-Servererweiterungen verwendet, müssen Sie zunächst FrontPage\-Servererweiterungen installieren.  Sie können die Installation mit dem Verwaltungstool Serververwaltung von Windows Server ausführen.  
  
## Windows Server: Gesperrte Inhaltstypen  
 Unter [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] werden alle Dateitypen durch IIS gesperrt, mit Ausnahme bestimmter bekannter Inhaltstypen \(z. B. HTM, HTML, TXT usw.\).  Um die Bereitstellung von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen mit diesem Server zu ermöglichen, müssen Sie die IIS\-Einstellungen ändern, damit Dateien vom Typ APPLICATION, MANIFEST oder andere benutzerdefinierte, von der Anwendung verwendete Dateitypen heruntergeladen werden können.  
  
 Wenn Sie die Bereitstellung mit einem IIS\-Server durchführen, führen Sie inetmgr.exe aus, und fügen Sie neue Dateitypen für die Standardwebseite hinzu:  
  
-   Für die Erweiterungen APPLICATION und MANIFEST sollte der MIME\-Typ "application\/x\-ms\-application" sein. Für andere Dateitypen sollte der MIME\-Typ "application\/octet\-stream" sein.  
  
-   Wenn Sie einen MIME\-Typ mit der Erweiterung "\*" und dem MIME\-Typ "application\/octet\-stream" erstellen, können Dateien mit nicht blockiertem Dateityp heruntergeladen werden.  \(Blockierte Dateitypen wie ASPX und ASMX können jedoch nicht heruntergeladen werden.\)  
  
 Genaue Anweisungen für die Konfiguration von MIME\-Typen unter Windows Server finden Sie im Microsoft Knowledge Base\-Artikel KB326965, "IIS 6.0 stellt keine Dateien mit unbekanntem MIME\-Typ bereit" unter [http:\/\/support.microsoft.com\/kb\/326965\/de\-de](http://support.microsoft.com/kb/326965/de-de).  
  
## Inhaltstypzuordnungen  
 Beim Veröffentlichen über HTTP sollte der Inhaltstyp für die APPLICATION\-Datei \(auch als MIME\-Typ bekannt\) "application\/x\-ms\-application" sein. Wenn [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] auf dem Server installiert ist, wird dies automatisch festgelegt.  Wenn das Programm nicht installiert ist, müssen Sie für vroot der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung \(oder den gesamten Server\) eine MIME\-Typ\-Verknüpfung erstellen.  
  
 Wenn Sie die Bereitstellung mit einem IIS\-Server durchführen, führen Sie inetmgr.exe aus, und fügen Sie den neuen Inhaltstyp "application\/x\-ms\-application" für die Erweiterung .application hinzu.  
  
## Probleme mit der HTTP\-Komprimierung  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] unterstützt Downloads mit HTTP\-Komprimierung, einer Webservertechnologie, bei der ein Datenstream vor dem Senden des Streams an den Client mithilfe des GZIP\-Algorithmus komprimiert wird.  Der Client, in diesem Fall [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], dekomprimiert den Stream vor dem Lesen der Dateien.  
  
 Wenn Sie IIS verwenden, können Sie die HTTP\-Komprimierung problemlos aktivieren.  Die aktivierte HTTP\-Komprimierung wirkt sich jedoch nur auf HTML\- und Textdateien aus.  Um die Komprimierung für Assemblys \(Erweiterung .dll\), XML\-Dateien \(.xml\), Bereitstellungsmanifeste \(.application\) und Anwendungsmanifeste \(.manifest\) zu aktivieren, müssen Sie diese Dateitypen der Liste der von IIS zu komprimierenden Typen hinzufügen.  Vor dem Hinzufügen der Dateitypen zur Bereitstellung werden nur Text und HTML\-Dateien komprimiert.  
  
 Ausführliche Anweisungen zu IIS finden Sie unter [How to Specify Additional Document Types for HTTP Compression](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## Siehe auch  
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)   
 [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md)