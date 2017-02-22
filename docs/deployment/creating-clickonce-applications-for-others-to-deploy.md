---
title: "Creating ClickOnce Applications for Others to Deploy | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "preserved branding information"
  - "useManifestForTrust element"
  - "customer deployments [ClickOnce]"
  - "multiple ClickOnce deployment and branding"
  - "ClickOnce applications, previous .NET Framework versions"
  - "application manifests [ClickOnce]"
  - "<useManifestForTrust> element"
  - "manifests [ClickOnce]"
  - "trust applications, ClickOnce"
  - "ClickOnce applications, deployed by others"
  - "ClickOnce applications, previous .NET Framework"
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Creating ClickOnce Applications for Others to Deploy
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nicht alle Entwickler, die ClickOnce\-Bereitstellungen erstellen, beabsichtigen, die Anwendungen selbst bereitzustellen.  Viele Entwickler packen ihre Anwendung einfach mithilfe von ClickOnce und geben diese Dateien dann an einen Kunden, beispielsweise an ein großes Unternehmen, weiter.  Ab diesem Zeitpunkt liegt die Verantwortung für das Hosten der Anwendung im Firmennetzwerk beim Kunden.  In diesem Thema werden einige Probleme erörtert, die im Zusammenhang mit derartigen Bereitstellungen in .NET Framework\-Versionen vor Version 3.5 auftreten können.  Anschließend wird ein neuer Lösungsansatz beschrieben, der auf der neuen Funktion "Anwendungsmanifest für Vertrauensstellungsinformationen verwenden" in .NET Framework 3.5 basiert.  Abschließend werden empfohlene Strategien zum Erstellen von ClickOnce\-Bereitstellungen für Kunden erläutert, die ältere Versionen von .NET Framework einsetzen.  
  
## Probleme beim Erstellen von Bereitstellungen für Kunden  
 Wenn Sie beabsichtigen, eine Bereitstellung an einen Kunden weiterzugeben, sind einige Punkte zu klären.  Der erste Punkt ist die Codesignatur.  Damit Bereitstellungs\- und Anwendungsmanifest einer ClickOnce\-Bereitstellung in einem Netzwerk bereitgestellt werden können, müssen beide mit einem digitalen Zertifikat signiert werden.  Dabei stellt sich die Frage, ob zum Signieren der Manifeste das Zertifikat des Entwicklers oder das des Kunden verwendet werden soll.  
  
 Die Frage, welches Zertifikat verwendet werden sollte, ist extrem wichtig, da die Identität einer ClickOnce\-Anwendung auf der digitalen Signatur des Bereitstellungsmanifests basiert.  Wenn das Bereitstellungsmanifest vom Entwickler signiert wird, könnten Konflikte entstehen, wenn es sich beim Kunden beispielsweise um ein Großunternehmen mit mehreren Abteilungen handelt, in denen eine angepasste Version der Anwendung eingesetzt wird.  
  
 Angenommen, Adventure Works verfügt über eine Finanzabteilung und eine Personalabteilung.  Beide Abteilungen haben von der Microsoft Corporation eine Lizenz für eine ClickOnce\-Anwendung erworben, durch die Berichte aus den in einer SQL\-Datenbank gespeicherten Daten generiert werden.  Microsoft liefert an jede Abteilung eine Anwendungsversion aus, die speziell an die Abteilungsdaten angepasst ist.  Wenn die Anwendungen mit demselben Authenticode\-Zertifikat signiert werden, erhält ein Benutzer, der versucht, beide Anwendungen zu verwenden, eine Fehlermeldung, da die zweite Anwendung von ClickOnce als identisch mit der ersten Anwendung angesehen würde.  In diesem Fall könnten auf Kundenseite unvorhersehbare und unerwünschte Nebeneffekte auftreten, beispielsweise der Verlust von Daten, die lokal von der Anwendung gespeichert wurden.  
  
 Ein zusätzliches Problem bei der Codesignierung bereitet das `deploymentProvider`\-Element im Bereitstellungsmanifest, durch das ClickOnce darüber informiert wird, wo Anwendungsupdates gesucht werden sollen.  Dieses Element muss dem Bereitstellungsmanifest vor dem Signieren hinzugefügt werden.  Wenn das Element danach hinzugefügt wird, muss das Bereitstellungsmanifest erneut signiert werden.  
  
### Signieren des Bereitstellungsmanifests durch den Kunden  
 Eine Lösung des Problems nicht einheitlicher Bereitstellungen besteht darin, das Anwendungsmanifest vom Entwickler und das Bereitstellungsmanifest vom Kunden signieren zu lassen.  Obwohl dieser Ansatz funktioniert, wirft er weitere Probleme auf.  Da ein Authenticode\-Zertifikat eine geschützte Urkunde bleiben muss, kann der Kunde das Zertifikat nicht einfach an den Entwickler aushändigen, damit er die Bereitstellung signieren kann.  Obwohl der Kunde das Bereitstellungsmanifest mithilfe frei erhältlicher Tools aus dem .NET Framework SDK selbst signieren kann, ist dazu u. U. mehr technisches Wissen erforderlich, als der Kunde aufbringen will oder kann.  In solchen Fällen erstellt der Entwickler normalerweise eine Anwendung, eine Website oder einen anderen Mechanismus, über den der Kunde seine Anwendungsversion zum Signieren übermitteln kann.  
  
### Auswirkung der Signierung durch den Kunden auf die ClickOnce\-Anwendungssicherheit  
 Auch wenn Entwickler und Kunde übereinkommen, dass das Anwendungsmanifest vom Kunden signiert werden soll, entstehen dadurch neue Probleme hinsichtlich der Anwendungsidentität, insbesondere was die Bereitstellung vertrauenswürdiger Anwendungen betrifft.  \(Weitere Informationen über dieses Feature finden Sie unter [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md).\) Angenommen, die Clientcomputer von Adventure Works sollen so konfiguriert werden, dass alle von der Microsoft Corporation gelieferten Anwendungen mit voller Vertrauenswürdigkeit ausgeführt werden.  Wenn das Anwendungsmanifest von Adventure Works signiert wird, verwendet ClickOnce die Sicherheitssignatur von Adventure Works, um die Vertrauensebene der Anwendung zu bestimmen.  
  
## Erstellen von Kundenbereitstellungen mithilfe von "Anwendungsmanifest für Vertrauensstellungsinformationen verwenden"  
 ClickOnce in .NET Framework 3.5 bietet ein neues Feature, mit dem Entwickler und Kunden eine neue Möglichkeit zum Signieren von Manifesten erhalten.  Das ClickOnce\-Anwendungsmanifest unterstützt ein neues Element mit dem Namen `<useManifestForTrust>`, mit dessen Hilfe ein Entwickler angeben kann, dass für Entscheidungen über die Vertrauenswürdigkeit die digitale Signatur des Anwendungsmanifests verwendet werden sollte.  Der Entwickler verwendet ClickOnce\-Tools zum Packen, z. B. Mage.exe, MageUI.exe und Visual Studio, um dieses Element in das Anwendungsmanifest aufzunehmen und um sowohl den Herausgebernamen als auch den Namen der Anwendung in das Manifest einzubetten.  
  
 Bei Verwendung von `<useManifestForTrust>` muss das Bereitstellungsmanifest nicht mit einem von einer Zertifizierungsstelle ausgestellten Authenticode\-Zertifikat signiert werden.  Stattdessen kann es mit einem so genannten selbstsignierten Zertifikat signiert werden.  Ein selbstsigniertes Zertifikat wird entweder vom Kunden oder Entwickler unter Verwendung von .NET Framework SDK\-Standardtools generiert und dann mithilfe der standardmäßigen ClickOnce\-Bereitstellungstools auf das Bereitstellungsmanifest angewendet.  Weitere Informationen finden Sie unter [Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md).  
  
 Die Verwendung eines selbstsignierten Zertifikats für das Bereitstellungsmanifest bietet mehrere Vorteile.  Da der Kunde kein eigenes Authenticode\-Zertifikat mehr anfordern oder erstellen muss, vereinfacht `<useManifestForTrust>` die Bereitstellung für den Kunden, während der Entwickler die eigene Brandingidentität der Anwendung beibehalten kann.  Das Ergebnis sind signierte Bereitstellungen, die sicherer sind und über eindeutige Anwendungsidentitäten verfügen.  Dies verhindert Konflikte, die sich aus der Bereitstellung derselben Anwendung für mehrere Kunden ergibt.  
  
 Schrittweise Informationen über das Erstellen einer ClickOnce\-Bereitstellung mit aktiviertem `<useManifestForTrust>` finden Sie unter [Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re\-Signing and that Preserves Branding Information](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### Funktionsweise von "Anwendungsmanifest für Vertrauensstellungsinformationen verwenden" zur Laufzeit  
 Um einen besseren Einblick zu erhalten, wie die Verwendung des Anwendungsmanifests für Vertrauensstellungsinformationen zur Laufzeit funktioniert, sollten Sie folgendes Beispiel beachten.  Von Microsoft wird eine ClickOnce\-Anwendung erstellt, die auf .NET Framework 3.5 abzielt.  Das Anwendungsmanifest verwendet das `<useManifestForTrust>`\-Element und wird von Microsoft signiert.  Adventure Works signiert das Bereitstellungsmanifest mit einem selbstsignierten Zertifikat.  Adventure Works\-Clients werden so konfiguriert, dass alle von Microsoft signierten Anwendungen als vertrauenswürdig angesehen werden.  
  
 Wenn der Anwender auf einen Link zum Bereitstellungsmanifest klickt, wird die Anwendung durch ClickOnce auf dem Computer des Benutzers installiert.  Durch das Zertifikat und die Bereitstellungsinformationen wird die Anwendung auf dem Clientcomputer eindeutig für ClickOnce identifiziert.  Wenn der Benutzer versucht, dieselbe Anwendung von einem anderen Speicherort erneut zu installieren, kann ClickOnce anhand dieser Identitätsinformationen feststellen, dass die Anwendung bereits auf dem Client vorhanden ist.  
  
 Anschließend überprüft ClickOnce das zum Signieren des Anwendungsmanifests verwendete Authenticode\-Zertifikat, durch das die von ClickOnce gewährte Vertrauensebene bestimmt wird.  Da die Clients von Adventure Works so konfiguriert wurden, dass alle von Microsoft signierten Anwendungen als vertrauenswürdig angesehen werden, wird dieser ClickOnce\-Anwendung volle Vertrauenswürdigkeit gewährt.  Weitere Informationen finden Sie unter [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md).  
  
## Erstellen von Kundenbereitstellungen für frühere Versionen  
 Was geschieht, wenn ein Entwickler ClickOnce\-Anwendungen für Kunden bereitstellt, die eine ältere Version von .NET Framework verwenden?  Die folgenden Abschnitte bieten einen Überblick über mehrere empfohlene Lösungen, die zusammen mit den jeweiligen Vorteilen und Nachteilen aufgeführt sind.  
  
### Signieren von Bereitstellungen im Namen des Kunden  
 Eine mögliche Bereitstellungsstrategie besteht für den Entwickler im Erstellen eines Mechanismus zum Signieren von Bereitstellungen im Namen seiner Kunden, indem der eigene private Schlüssel des Kunden verwendet wird.  Dadurch wird verhindert, dass der Entwickler private Schlüssel oder mehrere Bereitstellungspakete verwalten muss.  Der Entwickler liefert jedem Kunden einfach die gleiche Bereitstellung.  Es ist dem Kunden überlassen, die Bereitstellung unter Verwendung des Signierungsdiensts an seine Umgebung anzupassen.  
  
 Ein Nachteil dieser Methode sind die Zeit und die Kosten, die zu deren Implementierung aufgewendet werden.  Obwohl ein derartiger Dienst mithilfe der im .NET Framework SDK enthaltenen Tools erstellt werden kann, verlängert sich die Entwicklungszeit innerhalb des Produktlebenszyklus.  
  
 Wie bereits in diesem Thema erwähnt, besteht ein weiterer Nachteil darin, dass die Anwendungsversion jedes Kunden über dieselbe Anwendungsidentität verfügt, was zu Konflikten führen könnte.  Wenn dies Probleme aufwirft, kann der Entwickler das beim Generieren des Bereitstellungsmanifests verwendete Namensfeld ändern, um jeder Anwendung einen eindeutigen Namen zu geben.  Dadurch wird für jede Version der Anwendung eine separate Identität erstellt und ein möglicher Identitätskonflikt vermieden.  Dieses Feld entspricht dem `-Name`\-Argument für Mage.exe, nicht aber dem Feld **Name** auf der Registerkarte **Name** in MageUI.exe.  
  
 Beispiel: Der Entwickler hat eine Anwendung mit dem Namen Anwendung1 erstellt.  Anstatt eine einzelne Bereitstellung mit dem Eintrag Anwendung1 im Namensfeld zu erstellen, kann der Entwickler mehrere Bereitstellungen mit einer kundenspezifischen Variante für diesen Namen erstellen, wie Anwendung1\-KundeA, Anwendung1\-KundeB usw.  
  
### Bereitstellen unter Verwendung eines Setuppakets  
 Eine zweite mögliche Bereitstellungsstrategie ist das Generieren eines Microsoft\-Setup\-Projekts, um die ClickOnce\-Anwendung erstmalig bereitzustellen.  Dazu können viele verschiedene Formate verwendet werden: MSI\-Bereitstellung, ausführbare Setup\-Datei \(.EXE\) oder CAB\-Datei \(.cab\) zusammen mit einer Batchdatei.  
  
 Mit diesem Verfahren gibt der Entwickler eine Bereitstellung an den Kunden weiter, die die Anwendungsdateien, das Anwendungsmanifest und ein Bereitstellungsmanifest enthält, das als Vorlage dient.  Der Kunde führt das Setupprogramm aus, in dem eine Bereitstellungs\-URL \(der Speicherort der Server\- oder Dateifreigabe, von der Benutzer die ClickOnce\-Anwendung installieren\) sowie ein digitales Zertifikat angefordert wird.  Die Setupanwendung kann außerdem zusätzliche Optionen für die ClickOnce\-Konfiguration anfordern, z. B. das Intervall für die Updateüberprüfung.  Nachdem diese Informationen vollständig abgerufen wurden, wird das echte Bereitstellungsmanifest vom Setupprogramm generiert und signiert sowie die ClickOnce\-Anwendung am angegebenen Serverspeicherort veröffentlicht.  
  
 Der Kunde hat in dieser Situation drei Möglichkeiten, das Bereitstellungsmanifest zu signieren:  
  
1.  Der Kunde kann ein gültiges von einer Zertifizierungsstelle ausgegebenes Zertifikat verwenden.  
  
2.  Alternativ kann der Kunde sein Bereitstellungsmanifest mit einem selbstsignierten Zertifikat signieren.  Der Nachteil besteht darin, dass die Anwendung die Meldung "Unbekannter Herausgeber" ausgibt, wenn der Benutzer gefragt wird, ob er die Anwendung installieren möchte.  Der Vorteil besteht allerdings darin, dass kleinere Kunden die Zeit und Kosten einsparen können, die für ein von einer Zertifizierungsstelle ausgestelltes Zertifikat anfallen würden.  
  
3.  Schließlich kann der Entwickler ein eigenes selbstsigniertes Zertifikat in das Setuppaket aufnehmen.  Dies kann zu Problemen mit der Anwendungsidentität führen, die bereits früher in diesem Thema erörtert wurden.  
  
 Der Nachteil bei der Verwendung eines Setup\-Projekts für die Bereitstellung liegt in der Zeit und den Kosten, die zum Erstellen einer benutzerdefinierten Bereitstellungsanwendung erforderlich sind.  
  
### Generieren des Bereitstellungsmanifests durch den Kunden  
 Eine dritte mögliche Bereitstellungsstrategie besteht darin, lediglich die Anwendungsdateien und das Anwendungsmanifest an den Kunden auszuhändigen.  In diesem Szenario ist der Kunde dafür verantwortlich, das Bereitstellungsmanifest mithilfe des .NET Framework SDKs zu generieren und zu signieren.  
  
 Der Nachteil dieser Methode liegt darin, dass der Kunde die .NET Framework SDK\-Tools installieren und ein Entwickler oder Systemadministrator beim Kunden sich mit diesen Tools auskennen muss.  Einige Kunden verlangen vielleicht eine Lösung, die wenige oder keine technische Kenntnisse ihrerseits erfordert.  
  
## Siehe auch  
 [Deploying ClickOnce Applications For Testing and Production Servers without Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re\-Signing and that Preserves Branding Information](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)