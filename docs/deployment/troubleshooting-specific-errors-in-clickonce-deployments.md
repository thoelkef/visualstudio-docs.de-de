---
title: "Troubleshooting Specific Errors in ClickOnce Deployments | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired"
  - "Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "deploying applications, ClickOnce"
  - "troubleshooting ClickOnce deployments"
  - "ClickOnce deployment, troubleshooting"
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Troubleshooting Specific Errors in ClickOnce Deployments
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema werden die folgenden häufigen Fehler aufgelistet, die beim Bereitstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung auftreten können. Darüber hinaus werden Schritte zum Lösen der einzelnen Probleme beschrieben.  
  
## Allgemeine Fehler  
  
#### Wenn Sie eine APPLICATION\-Datei suchen, geschieht nichts, oder in Internet Explorer wird XML gerendert, oder das Dialogfeld Ausführen oder Speichern unter wird angezeigt.  
 Dieser Fehler wird wahrscheinlich durch Inhaltstypen \(auch als MIME\-Typen bekannt\) verursacht, die nicht richtig auf dem Server oder Client registriert werden.  
  
 Stellen Sie zunächst sicher, dass der Server so konfiguriert ist, dass dem Inhaltstyp "application\/x\-ms\-application" die Erweiterung .application zugeordnet wird.  
  
 Stellen Sie bei ordnungsgemäßer Konfiguration des Servers sicher, dass [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] auf dem Computer installiert ist.  Wenn [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] installiert ist und das Problem weiterhin auftritt, versuchen Sie es mit einer Deinstallation und anschließenden Neuinstallation von [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]. Dadurch wird der Inhaltstyp auf dem Client neu registriert.  
  
#### In der Fehlermeldung wird angegeben, dass die Anwendungsdateien nicht abgerufen werden konnten,da die Bereitstellungsdateien fehlen oder der Anwendungsdownload unterbrochen wurde. Sie werden aufgefordert, auf Netzwerkfehler zu überprüfen und es später erneut zu versuchen.  
 Diese Meldung bedeutet, dass eine oder mehrere Dateien, auf die in den [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Manifesten verwiesen wird, nicht heruntergeladen werden können.  Versuchen Sie zur Behebung dieses Fehlers, die URL herunterzuladen, die von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nicht heruntergeladen werden kann.  Mögliche Ursachen:  
  
-   Wenn die Protokolldatei den Fehler "403 \(Verboten\)" oder "404 \(Nicht gefunden\)" enthält, stellen Sie sicher, dass die Konfiguration des Webservers das Herunterladen dieser Datei zulässt.  Weitere Informationen finden Sie unter [Server and Client Configuration Issues in ClickOnce Deployments](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
-   Wenn die CONFIG\-Datei vom Server blockiert wird, finden Sie weiter unten in diesem Thema im Abschnitt "Downloadfehler beim Versuch, eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung mit einer CONFIG\-Datei zu installieren" weitere Informationen.  
  
-   Bestimmen Sie, ob der Fehler aufgetreten ist, weil die `deploymentProvider`\-URL im Bereitstellungsmanifest auf einen anderen Speicherort zeigt als die für die Aktivierung verwendete URL.  
  
-   Überprüfen Sie das [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Protokoll auf fehlende Dateien, und stellen Sie sicher, dass alle Dateien auf dem Server vorhanden sind.  
  
-   Überprüfen Sie, ob Netzwerkverbindungsfehler aufgetreten sind. Diese Fehler können darauf zurückzuführen sein, dass die Verbindung während des Downloads vom Clientcomputer getrennt wurde.  
  
#### Downloadfehler beim Versuch, eine ClickOnce\-Anwendung mit einer CONFIG\-Datei zu installieren  
 Eine Visual Basic\-Anwendung für Windows enthält standardmäßig die Datei App.config.  Wenn ein Benutzer versucht, eine Installation von einem Webserver auszuführen, auf dem Windows Server 2003 ausgeführt wird, tritt ein Problem auf, da dieses Betriebssystem die Installation von CONFIG\-Dateien aus Sicherheitsgründen blockiert.  Damit die CONFIG\-Datei installiert werden kann, klicken Sie im Dialogfeld **Veröffentlichungsoptionen** auf **Dateierweiterung ".deploy" verwenden**.  
  
 Sie müssen auch für Dateien mit den Erweiterungen .application, .manifest und .deploy die entsprechenden Inhaltstypen \(auch als MIME\-Typen bekannt\) festlegen.  Weitere Informationen finden Sie in der Webserverdokumentation.  
  
 Weitere Informationen finden Sie unter "Windows Server 2003: Gesperrte Inhaltstypen" in [Server and Client Configuration Issues in ClickOnce Deployments](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
#### Fehlermeldung: "Anwendung ist nicht korrekt formatiert" wird ausgegeben, und die Protokolldatei enthält den Eintrag "XML signature is invalid".  
 Stellen Sie sicher, dass Sie die Manifestdatei aktualisiert und neu signiert haben.  Veröffentlichen Sie die Anwendung erneut mit Hilfe von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], oder verwenden Sie MAGE, um die Anwendung neu zu signieren.  
  
#### Die Anwendung wurde auf dem Server aktualisiert, das Update wird jedoch vom Client nicht heruntergeladen.  
 Dieses Problem kann eventuell gelöst werden, indem Sie eine der folgenden Aufgaben ausführen:  
  
-   Überprüfen Sie die `deploymentProvider`\-URL im Bereitstellungsmanifest.  Stellen Sie sicher, dass Sie die Daten am gleichen Speicherort aktualisieren, auf den `deploymentProvider` zeigt.  
  
-   Überprüfen Sie das Updateintervall im Bereitstellungsmanifest.  Wenn es sich um ein periodisches Intervall handelt, z. B. alle sechs Stunden, überprüft [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vor Ablauf dieser Zeit nicht auf Updates.  Sie können das Manifest ändern, sodass bei jedem Anwendungsstart auf Updates überprüft wird.  Das Ändern des Updateintervalls eignet sich als Option für die Entwicklungszeit, um die Installation von Updates sicherzustellen, beeinträchtigt jedoch die Anwendungsaktivierung.  
  
-   Versuchen Sie, die Anwendung über das Menü "Start" neu zu starten.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] hat das Update möglicherweise im Hintergrund erkannt, fordert Sie jedoch erst bei der nächsten Aktivierung zum Installieren der Daten auf.  
  
#### Während des Updates tritt ein Fehler mit folgendem Protokolleintrag auf: "Der Verweis in der Bereitstellung stimmt nicht mit der im Anwendungsmanifest definierten Identität überein."  
 Möglicherweise tritt dieser Fehler auf, weil Sie das Bereitstellungs\- und Anwendungsmanifest manuell bearbeitet haben, und dies hat dazu geführt, dass die Beschreibung der Identität einer Assembly in einem Manifest nicht mehr mit der entsprechenden Beschreibung in dem anderen Manifest synchron ist.  Die Identität einer Assembly besteht aus ihrem Namen, ihrer Version, ihrer Kultur und ihrem Token des öffentlichen Schlüssels.  Untersuchen Sie die Identitätsbeschreibungen in den Manifesten, und beseitigen Sie ggf. Abweichungen.  
  
#### Die erste Aktivierung von einer lokalen Festplatte oder CD\-ROM ist erfolgreich, jede weitere Aktivierung über das Startmenü schlägt jedoch fehl.  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwendet die Deployment Provider\-URL, um Updates für die Anwendung abzurufen.  Stellen Sie sicher, dass die URL auf den richtigen Speicherort zeigt.  
  
#### Fehler: "Die Anwendung kann nicht gestartet werden."  
 Diese Fehlermeldung gibt normalerweise an, dass bei der Installation der Anwendung im [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Speicher ein Problem aufgetreten ist.  Entweder liegt ein Fehler in der Anwendung vor, oder der Speicher ist beschädigt.  Möglicherweise wird in der Protokolldatei angegeben, wo der Fehler aufgetreten ist.  
  
 Gehen Sie wie folgt vor:  
  
-   Stellen Sie sicher, dass die Identität des Bereitstellungsmanifests, des Anwendungsmanifests und der Hauptanwendungsdatei \(EXE\-Datei\) eindeutig ist.  
  
-   Stellen Sie sicher, dass die Dateipfade nicht länger als 100 Zeichen sind.  Wenn die Anwendung Dateipfade enthält, die zu lang sind, überschreiten Sie möglicherweise die Längenbegrenzung für zu speichernde Pfade.  Verringern Sie die Pfadlänge, und wiederholen Sie die Installation.  
  
#### PrivatePath\-Einstellungen in der CONFIG\-Datei der Anwendung werden nicht berücksichtigt.  
 Um PrivatePath \(Fusionsüberprüfungspfade\) zu verwenden, muss die Anwendung volle Vertrauenswürdigkeit anfordern.  Ändern Sie das Anwendungsmanifest, sodass volle Vertrauenswürdigkeit angefordert wird, und wiederholen Sie den Vorgang.  
  
#### Während der Deinstallation wird in einer Meldung angezeigt, dass die Anwendung nicht deinstalliert werden konnte.  
 Diese Meldung bedeutet i. d. R., dass die Anwendung bereits entfernt wurde oder der Speicher beschädigt ist.  Nachdem Sie auf **OK** geklickt haben, wird der Eintrag für die Anwendung im Dialogfeld **Software** entfernt.  
  
#### Während der Installation wird die Meldung angezeigt, dass die Plattformabhängigkeiten nicht installiert sind.  
 Im GAC \(Global Assembly Cache\) fehlt eine zur Ausführung der Anwendung erforderliche Komponente.  
  
## Veröffentlichen mit Visual Studio  
  
#### Die Veröffentlichung in Visual Studio schlägt fehl  
 Stellen Sie sicher, dass Sie über die Berechtigung verfügen, auf dem Zielserver zu veröffentlichen.  Wenn Sie beispielsweise an einem Terminalservercomputer nicht als Administrator, sondern als normaler Benutzer angemeldet sind, haben Sie vermutlich keine Berechtigung, auf dem lokalen Webserver zu veröffentlichen.  
  
 Wenn Sie mit einer URL veröffentlichen, stellen Sie sicher, dass auf dem Zielcomputer FrontPage\-Servererweiterungen aktiviert sind.  
  
#### Fehlermeldung: Die Website '\<Site\>' kann nicht erstellt werden.Die Komponenten zur Kommunikation mit den FrontPage\-Servererweiterungen sind nicht installiert.  
 Vergewissern Sie sich, dass auf dem Computer, von dem aus Sie veröffentlichen, Microsoft Visual Studio Web Authoring Component installiert ist.  Unter Express wird diese Komponente in der Standardeinstellung nicht installiert.  Weitere Informationen finden Sie unter [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=102310](http://go.microsoft.com/fwlink/?LinkId=102310).  
  
#### Fehlermeldung: Die Datei „Microsoft.Windows.Common\-Controls, Version\= 6.0.0.0, Culture\=\*, PublicKeyToken\=6595b64144ccf1df, ProcessorArchitecture\=\*, Type\=win32“ wurde nicht gefunden  
 Diese Fehlermeldung wird ausgegeben, wenn Sie versuchen, eine WPF\-Anwendung mit aktivierten visuellen Stilen zu veröffentlichen.  Zum Beheben dieses Problems finden Sie unter [How to: Publish a WPF Application with Visual Styles Enabled](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).  
  
## Verwenden von MAGE  
  
#### Beim Versuch, mit einem Zertifikat aus dem Zertifikatspeicher zu signieren, wird ein leeres Meldungsfeld ausgegeben.  
 Führen Sie im Dialogfeld **Signierung** die folgenden Schritte aus:  
  
-   Wählen Sie **Mit gespeichertem Zertifikat signieren** aus.  
  
-   Wählen Sie ein Zertifikat aus der Liste aus. Das erste Zertifikat ist nicht die Standardauswahl.  
  
#### Wenn Sie das Signieren abbrechen, tritt eine Ausnahme auf.  
 Dies ist ein bekanntes Problem.  Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Manifeste müssen signiert werden.  Wählen Sie einfach eine der Signierungsoptionen aus, und klicken Sie auf **OK**.  
  
## Weitere Fehler  
 Die folgende Tabelle enthält einige häufige Fehlermeldungen, die ein Benutzer bei der Installation einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung auf dem Clientcomputer erhalten kann.  Neben jeder Fehlermeldung wird eine Beschreibung mit der wahrscheinlichen Fehlerursache aufgelistet.  
  
|Fehlermeldung|Beschreibung|  
|-------------------|------------------|  
|Die Anwendung kann nicht gestartet werden.  Wenden Sie sich an den Herausgeber der Anwendung.<br /><br /> Die Anwendung kann nicht gestartet werden.  Wenden Sie sich an den Hersteller der Anwendung, um Unterstützung zu erhalten.|Hierbei handelt es sich um generische Fehlermeldungen, die ausgegeben werden, wenn die Anwendung nicht gestartet werden kann und keine weitere Ursache gefunden wird.  Häufig bedeutet dies, dass die Anwendung in irgendeiner Weise beschädigt ist bzw. dass der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Speicher defekt ist.|  
|Vorgang kann nicht fortgesetzt werden.  Die Anwendung ist nicht ordnungsgemäß formatiert.  Wenden Sie sich an den Herausgeber der Anwendung, um Unterstützung zu erhalten.<br /><br /> Fehler bei der Validierung der Anwendung.  Der Vorgang kann nicht fortgesetzt werden.<br /><br /> Anwendungsdateien können nicht abgerufen werden.  Die Dateien in der Bereitstellung sind beschädigt.|Eine der Manifestdateien in der Bereitstellung enthält eine ungültige Syntax oder einen Hash, die bzw. der mit der entsprechenden Datei nicht abgestimmt werden kann.  Dieser Fehler kann auch darauf hinweisen, dass das in einer Assembly eingebettete Manifest beschädigt ist.  Erstellen Sie die Bereitstellung neu, und kompilieren Sie die Anwendung erneut, oder suchen Sie die Fehler in den Manifesten, und beheben Sie sie manuell.|  
|Anwendung kann nicht abgerufen werden.  Authentifizierungsfehler.<br /><br /> Die Anwendung konnte nicht installiert werden.  Die Anwendungsdateien wurden auf dem Server nicht gefunden.  Wenden Sie sich an den Herausgeber der Anwendung oder den Administrator, um Unterstützung zu erhalten.|Mindestens eine Datei in der Bereitstellung kann nicht heruntergeladen werden, da Sie keine Zugriffsberechtigung besitzen.  Die Ursache kann ein vom Webserver zurückgegebener Fehler 403 \(Unzulässig\) sein, der u. U. ausgegeben wird, wenn eine der Dateien in der Bereitstellung über eine Dateinamenerweiterung verfügt, durch die sie vom Webserver als geschützte Datei eingestuft wird.  Außerdem kann für den Zugriff auf ein Verzeichnis, in dem eine oder mehrere Anwendungsdateien enthalten sind, ein Benutzername und Kennwort erforderlich sein.|  
|Die Anwendung kann nicht heruntergeladen werden.  Der Anwendung fehlen erforderliche Dateien.  Wenden Sie sich an den Hersteller der Anwendung oder den Systemadministrator, um Unterstützung zu erhalten.|Mindestens eine der im Anwendungsmanifest aufgelisteten Dateien kann nicht auf dem Server gefunden werden.  Überprüfen Sie, ob Sie alle abhängigen Dateien der Bereitstellung hochgeladen haben, und wiederholen Sie den Vorgang.|  
|Die Anwendung konnte nicht heruntergeladen werden.  Überprüfen Sie die Netzwerkverbindung, oder wenden Sie sich an den Systemadministrator oder Netzwerk\-Dienstanbieter.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kann keine Netzwerkverbindung zum Server herstellen.  Überprüfen Sie die Verfügbarkeit des Servers und den Netzwerkzustand.|  
|URLDownloadToCacheFile\-Fehler mit HRESULT' '\<number\>'.  Beim Download von '\<file\>' ist ein Fehler aufgetreten.|Wenn auf dem Bereitstellungszielcomputer die erweiterte Sicherheitseinstellung im Internet Explorer  auf "Beim Wechsel zwischen sicherem und nicht sicherem Modus warnen" eingestellt ist und wenn die Setup\-URL der zu installierenden ClickOnce\-Anwendung von einer nicht sicheren zu einer sichern Site \(oder umgekehrt\) umgeleitet wird, tritt bei der Installation ein Fehler auf, da sie von der Warnmeldung des Internet Explorers unterbrochen wird.<br /><br /> Zum Vermeiden dieser Warnung bestehen folgende Möglichkeiten:<br /><br /> -   Deaktivieren Sie die Sicherheitsoption.<br />-   Stellen Sie sicher, dass beim Umleiten der Setup\-URL nicht die Sicherheitsmodi geändert werden.<br />-   Entfernen Sie die Umleitung völlig, und verweisen Sie auf die tatsächliche Setup\-URL.|  
|Beim Schreiben auf die Festplatte ist ein Fehler aufgetreten.  Möglicherweise ist nicht genügend Speicherplatz auf dem Datenträger verfügbar.  Wenden Sie sich an den Hersteller der Anwendung oder den Systemadministrator, um Unterstützung zu erhalten.|Dies kann bedeuten, dass nicht genügend Festplattenspeicher zum Speichern der Anwendung verfügbar ist. Es kann jedoch auch ein allgemeiner E\/A\-Fehler vorliegen, der beim Speichern der Anwendungsdateien auf dem Laufwerk auftritt.|  
|Die Anwendung kann nicht gestartet werden.  Nicht genügend Speicherplatz auf dem Datenträger vorhanden.|Die Festplatte ist voll.  Geben Sie Speicherplatz frei, und versuchen Sie erneut, die Anwendung auszuführen.|  
|Es wird versucht, zu viele bereitgestellte Aktivierungen gleichzeitig zu laden.|Unter [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist die Anzahl unterschiedlicher Anwendungen, die gleichzeitig gestartet werden können, eingeschränkt.  Hierdurch sollen hauptsächlich böswillige Denial\-of\-Service\-Angriffe auf den lokalen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Dienst verhindert werden. Benutzer, die versuchen, dieselbe Anwendung mehrmals kurz hintereinander zu starten, erhalten immer nur eine einzige Instanz der Anwendung.|  
|Verknüpfungen können nicht über das Netzwerk aktiviert werden.|Verknüpfungen mit einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung können nur über die lokale Festplatte gestartet werden.  Sie können nicht gestartet werden, indem Sie eine URL öffnen, die auf eine Verknüpfungsdatei auf einem Remoteserver verweist.|  
|Die Anwendung ist zu groß für die Onlineausführung mit teilweiser Vertrauenswürdigkeit.  Wenden Sie sich an den Hersteller der Anwendung oder den Systemadministrator, um Unterstützung zu erhalten.|Die Größe einer mit teilweiser Vertrauenswürdigkeit ausgeführten Anwendung darf 50 % des Kontingents für Onlineanwendungen \(standardmäßig 250 MB\) nicht überschreiten.|  
  
## Siehe auch  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)   
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)