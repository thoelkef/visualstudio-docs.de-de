---
title: Erstellen von ClickOnce-Anwendungen für andere bereitstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b74e8a988505c5386b444df27f7726a8ceb51a62
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870775"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>Erstellen von ClickOnce-Anwendungen für andere bereitstellen
Beim Versuch, die Anwendungen selbst bereitstellen, ist nicht für alle Entwickler, die ClickOnce-Bereitstellungen erstellen möchten. Viele von ihnen Packen Sie einfach ihre Anwendung mithilfe von ClickOnce und leiten dann die Dateien für einen Kunden, wie z. B. ein großes Unternehmen. Der Kunde ist dafür verantwortlich sind, zum Hosten der Anwendung im Netzwerk. Dieses Thema behandelt einige der Probleme, die sich solche Bereitstellungen in Versionen von .NET Framework vor Version 3.5. Klicken Sie dann beschrieben eine neue Projektmappe, die mithilfe der neuen "Verwenden von Manifest für die Vertrauensstellung"-Funktion in .NET Framework 3.5. Schließlich endet er mit empfohlenen Vorgehensweisen zum Erstellen von ClickOnce-Bereitstellungen für Kunden, die noch ältere Versionen von .NET Framework verwenden.  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>Probleme im Zusammenhang mit Bereitstellungen für Kunden erstellen  
 Mehrere Probleme auftreten, wenn Sie eine Bereitstellung für einen Kunden bereitstellen möchten. Das erste Problem betrifft die Codesignatur. Um in einem Netzwerk bereitgestellt werden, müssen das Bereitstellungsmanifest und Anwendungsmanifest einer ClickOnce-Bereitstellung sowohl mit einem digitalen Zertifikat signiert werden. Dies wirft die Frage, ob für die Manifeste signieren des Entwicklers oder des Kunden Zertifikat verwendet.  
  
 Die Frage, welches Zertifikat verwenden, ist entscheidend, wie die digitale Signatur des Bereitstellungsmanifests eine ClickOnce-Anwendungsidentität basiert. Wenn der Entwickler das Bereitstellungsmanifest signiert, kann es zu Konflikten kommen, wenn der Kunde ein großes Unternehmen ist und mehr als eine Abteilung des Unternehmens wird eine angepasste Version der Anwendung bereitgestellt.  
  
 Angenommen Sie, dass Adventure Works eine Finanzabteilung und eine Personalabteilung verfügt. Beiden Abteilungen lizenzieren, eine ClickOnce-Anwendung von der Microsoft Corporation, die Berichte aus Daten in einer SQL-Datenbank generiert wird. Microsoft stellt jede Abteilung mit einer Version der Anwendung, die für ihre Daten angepasst wird. Wenn die Anwendungen mit dem gleichen Authenticode-Zertifikat signiert sind, würde ein Benutzer versucht, die beide Anwendungen verwenden einen Fehler auftreten, wie ClickOnce auf die zweite Anwendung als mit dem ersten identisch betrachten würden. In diesem Fall kann der Kunde unvorhersehbar und unerwünschte Nebeneffekte auftreten, die den Verlust von Daten lokal gespeichert, von der Anwendung enthalten.  
  
 Ein zusätzliches Problem mit der zum Signieren von code die `deploymentProvider` -Elements im Bereitstellungsmanifest, die mitteilt, wo Sie suchen nach Anwendungsupdates, ClickOnce. Dieses Element muss auf das Bereitstellungsmanifest vor dem unterzeichnen es hinzugefügt werden. Wenn dieses Element später hinzugefügt wird, muss das Bereitstellungsmanifest erneut signiert werden.  
  
### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>Muss der Kunde zum Signieren des verteilungsmanifests  
 Eine Lösung, um dieses Problem nicht eindeutigen Bereitstellungen ist, die Entwickler Signieren des Anwendungsmanifests und der Kunde anmelden, das Bereitstellungsmanifest. Dieser Ansatz funktioniert, zwar führt es andere Probleme. Da es sich bei einem Authenticode-Zertifikat eine geschützte Ressource bleiben muss, kann nicht der Kunde nur das Zertifikat für dem Entwickler zum Signieren der bereitstellungs festlegen. Während der Kunde Signieren des verteilungsmanifests selbst kann mithilfe der frei verfügbaren Tools mit dem .NET Framework SDK, erfordern diese mehr technisches Wissen als der Kunde bereit, oder bereitstellen. In solchen Fällen erstellt der Entwickler in der Regel eine Anwendung, Website oder anderen Mechanismus, durch die Kunden ihre Version der Anwendung für die Signierung übermitteln kann.  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>Die Auswirkungen von Kunden, die Anmeldung an der Sicherheit für ClickOnce-Anwendung  
 Auch wenn der Entwickler und Kunden zustimmen, dass der Kunde das Anwendungsmanifest signieren muss, löst daraufhin andere Probleme, die die Identität der Anwendung, umschließen, vor allem, weil sie für die Bereitstellung einer vertrauenswürdigen Anwendung gilt. (Weitere Informationen zu diesem Feature finden Sie unter [Übersicht über die Bereitstellung von vertrauenswürdigen Anwendung](../deployment/trusted-application-deployment-overview.md).) Angenommen Sie, dass die Adventure Works möchte seine Clientcomputer so konfigurieren, dass jede Anwendung, die für sie bereitgestellt werden, von der Microsoft Corporation mit voller Vertrauenswürdigkeit ausgeführt wird. Adventure Works, das Bereitstellungsmanifest anmelden, wird ClickOnce Adventure Work Security-Signatur verwenden, um zu bestimmen, die Vertrauensebene der Anwendung klicken.  
  
## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>Erstellen von Bereitstellungen von Kunden durch Verwenden des Anwendungsmanifests für die Vertrauensstellung  
 ClickOnce in .NET Framework 3.5 enthält ein neues Feature, das Entwicklern und Kunden erhalten eine neue Projektmappe auf das Szenario wie die Manifeste signiert werden sollen. Das ClickOnce-Anwendungsmanifest unterstützt ein neues Element mit dem Namen `<useManifestForTrust>` , ermöglicht, dass ein Entwickler, der besagt, dass die digitale Signatur des Anwendungsmanifests ist, was zum treffen von Entscheidungen über Vertrauensstellungen verwendet werden sollte. Der Entwickler verwendet ClickOnce Tools zum Packen, wie z. B. *Mage.exe*, *MageUI.exe*, und Visual Studio – dieses Element im Anwendungsmanifest enthalten, sowie sowohl den Herausgebernamen einbetten und der Name der Anwendung im Manifest.  
  
 Bei Verwendung `<useManifestForTrust>`, das Bereitstellungsmanifest muss nicht mit einem Authenticode-Zertifikat ausgestellt, die von einer Zertifizierungsstelle signiert werden. Stattdessen können sie mit ein selbst signiertes Zertifikat sogenannten signiert werden. Ein selbst signiertes Zertifikat ist entweder vom Kunden oder der Entwickler mithilfe von .NET Framework SDK-Standardtools vom verwendet zu werden, und klicken Sie dann auf das Bereitstellungsmanifest mit den Standardtools der ClickOnce-Bereitstellung angewendet werden. Weitere Informationen finden Sie unter ["MakeCert"](/windows/desktop/SecCrypto/makecert).  
  
 Verwenden ein selbstsigniertes Zertifikat für das Bereitstellungsmanifest bietet mehrere Vorteile. Durch den Wegfall des Kunden zum Abrufen oder erstellen ihre eigenen Authenticode-Zertifikat, `<useManifestForTrust>` vereinfacht die Bereitstellung für den Kunden, während den Entwickler, ihre eigenen branding Identität für die Anwendung zu erhalten. Das Ergebnis ist eine Reihe von signierten Bereitstellungen, die sicherer und verfügen über eindeutige Identitäten. Dadurch werden Konflikte, die von der Bereitstellung von der gleichen Anwendung für mehrere Kunden auftreten kann.  
  
 Ausführliche Informationen zur Vorgehensweise: erstellen eine ClickOnce-Bereitstellung mit `<useManifestForTrust>` aktiviert ist, finden Sie [Exemplarische Vorgehensweise: Manuelles bereitstellen eine ClickOnce-Anwendung, die kein erneutes Signieren erfordert und Brandinginformationenbeibehält](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>Wie funktioniert das Anwendungsmanifest für die Vertrauensstellung zur Laufzeit  
 Um ein besseres Verständnis der Funktionsweise der mit dem Anwendungsmanifest für die Vertrauensstellung zur Laufzeit zu erhalten, erwägen Sie das folgende Beispiel aus. Eine ClickOnce-Anwendung, die .NET Framework 3.5 ausgerichtet ist, wird von Microsoft erstellt. Das Anwendungsmanifest verwendet die `<useManifestForTrust>` Element und wird von Microsoft signiert. Adventure Works signiert das Bereitstellungsmanifest mithilfe eines selbstsignierten Zertifikats. Adventure Works-Clients so konfiguriert werden, dass um jede Anwendung, die von Microsoft signiert zu vertrauen.  
  
 Klickt ein Benutzer einen Link auf das Bereitstellungsmanifest, wird die Anwendung von ClickOnce auf dem Computer des Benutzers installiert. Die Zertifikat und der Bereitstellung Informationen identifizieren Sie die Anwendung eindeutig von ClickOnce auf dem Clientcomputer. Wenn der Benutzer versucht, dieselbe Anwendung von einem anderen Speicherort erneut zu installieren, kann ClickOnce diese Identität verwenden, um zu bestimmen, dass die Anwendung bereits auf dem Client vorhanden ist.  
  
 Als Nächstes untersucht ClickOnce das Authenticode-Zertifikat, das verwendet wird, sich das Anwendungsmanifest, das die Ebene der Vertrauenswürdigkeit bestimmt, die ClickOnce gewähren. Da Adventure Works seinen Clients, dass jede Anwendung, die von Microsoft signiert vertrauen konfiguriert hat, wird diese ClickOnce-Anwendung auf volle Vertrauenswürdigkeit gewährt. Weitere Informationen finden Sie unter [Übersicht über die Bereitstellung von vertrauenswürdigen Anwendung](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="create-customer-deployments-for-earlier-versions"></a>Erstellen von Bereitstellungen von Kunden für frühere Versionen  
 Was geschieht, wenn ein Entwickler ClickOnce-Anwendungen für Kunden bereitgestellt wird, die ältere Versionen von .NET Framework verwenden? In den folgenden Abschnitten werden mehrere empfohlene Lösungen sowie die vor- und Nachteile der einzelnen zusammengefasst.  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>SSO-Bereitstellungen für Kunden  
 Eine mögliche Bereitstellung-Strategie ist für die der Entwickler einen Mechanismus, um die Bereitstellungen im Auftrag ihrer Kunden, melden Sie sich mit dem privaten Schlüssel des Kunden zu erstellen. Dadurch wird verhindert, dass den Entwickler private Schlüssel oder mehrere Bereitstellungspakete verwaltet werden müssen. Der Entwickler gibt nur derselben Bereitstellung für Kunden. Es ist der Kunde kann es für ihre Umgebung anpassen, indem Sie mithilfe der.  
  
 Ein Nachteil dieser Methode ist der Zeit- und Kostenaufwand, die für die Implementierung erforderlich sind. Während ein solcher Dienst mithilfe der Tools in .NET Framework SDK erstellt werden kann, wird er länger Entwicklung des Lebenszyklus hinzugefügt.  
  
 Wie weiter oben in diesem Thema erwähnt, ist ein weiterer Nachteil, dass jedes Kunden Version der Anwendung die gleiche Identität, hat dies kann zu Konflikten führen. Wenn dies relevant ist, kann der Entwickler das Namensfeld ändern, das beim Generieren des Bereitstellungsmanifests verwendet wird, um jede Anwendung einen eindeutigen Namen zu geben. Dadurch werden eine eigene Identität für jede Version der Anwendung zu erstellen und mögliche Identität Konflikte vermeiden. Dieses Feld entspricht der `-Name` Argument für Mage.exe, und klicken Sie auf die **Namen** Feld der **Namen** Registerkarte in MageUI.exe.  
  
 Angenommen Sie, dass der Entwickler eine Anwendung namens Application1 erstellt hat. Statt einer einzelnen Bereitstellung mit dem Name-Feld, das auf Application1 festgelegt, kann der Entwickler mehrere Bereitstellungen erstellen, mit einer kundenspezifischen Variation auf diesen Namen, z. B. Application1-Kunde, Application1-Kunde b, und so weiter.  
  
### <a name="deploy-using-a-setup-package"></a>Bereitstellung mithilfe eines Setup-Pakets  
 Eine zweite mögliche Bereitstellungsstrategie ist zum Generieren eines Microsoft-Setup-Projekts zum Ausführen der ersten Bereitstellung der ClickOnce-Anwendung. Dies kann in einem von mehreren verschiedenen Formaten bereitgestellt werden: als ein MSI-Bereitstellung, eine ausführbare Setupdatei (. (EXE), oder als eine CAB-Datei zusammen mit einem Stapelverarbeitungsskript.  
  
 Mithilfe dieser Technik, würde der Entwickler dem Kunden eine Bereitstellung bereitstellen, die enthält die Anwendungsdateien, das Anwendungsmanifest und ein Bereitstellungsmanifest, das als Vorlage dient. Der Kunde würde das Setup-Programm, führen sie, das dazu auffordern wird für eine bereitstellungs-URL (dem Server oder Dateifreigabe Speicherort aus dem Benutzer die ClickOnce-Anwendung installieren), sowie ein digitales Zertifikat. Die Setup-Anwendung können auch zusätzliche ClickOnce-Konfigurationsoptionen, z. B. Intervall zum Aktualisieren von Überprüfung angefordert. Nachdem diese Informationen zusammengestellt ist, würde das Setup-Programm echte Bereitstellungsmanifest zu generieren, melden Sie sich und veröffentlichen die ClickOnce-Anwendung auf dem angegebenen.  
  
 Es gibt drei Möglichkeiten, dass der Kunde das Bereitstellungsmanifest in dieser Situation anmelden kann:  
  
1. Der Kunde kann es sich um ein gültiges von einer Zertifizierungsstelle (CA) ausgestelltes Zertifikat verwenden.  
  
2. Als eine Variante zu diesem Ansatz ist können Kunden ihre Bereitstellungsmanifest mit einem selbstsignierten Zertifikat signiert. Der Nachteil ist, dass hierdurch die Wörter "Unbekannter Herausgeber" angezeigt wird, wenn der Benutzer aufgefordert wird, an, ob es installiert die Anwendung. Der Vorteil ist jedoch, dass sie dadurch verhindert, dass kleinere Kunden müssen die Zeit und Geld für ein von einer Zertifizierungsstelle ausgestelltes Zertifikat erforderlich.  
  
3. Schließlich kann der Entwickler ihre eigenen selbstsignierten Zertifikats in das Setup-Paket enthalten. Dies führt die potenziellen Probleme mit Anwendungsidentität, die weiter oben in diesem Thema.  
  
   Der Nachteil der Setup-Projekt Bereitstellungsmethode ist der Zeit- und Kostenaufwand erforderlich, um eine benutzerdefinierte Anwendung erstellen.  
  
### <a name="have-customer-generate-deployment-manifest"></a>Kunden Sie Bereitstellungsmanifest zu generieren.  
 Eine dritte mögliche Bereitstellungsstrategie ist zum Weitergeben deaktiviert nur die Anwendung Dateien und Anwendungsmanifest an den Kunden. In diesem Szenario ist der Kunde für die Verwendung von .NET Framework SDK zum Generieren und Signieren des Bereitstellungsmanifests verantwortlich.  
  
 Der Nachteil dieser Methode ist, dass es erfordert, dass der Kunde die .NET Framework SDK-Tools zu installieren und ein Entwickler oder Systemadministrator, die bereits Erfahrung mit der sie ist. Einige Kunden möglicherweise eine Lösung erfordern, die nur wenig oder keine technische Aufwand Ihrerseits erforderlich sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von ClickOnce-Anwendungen für Test- und produktionsumgebungen Server ohne erneutes Signieren](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)   
 [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Exemplarische Vorgehensweise: Bereitstellen einer ClickOnce-Anwendung manuell, die kein erneutes Signieren erfordert und Brandinginformationen beibehält](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)