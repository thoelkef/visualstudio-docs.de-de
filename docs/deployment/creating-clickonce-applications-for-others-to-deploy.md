---
title: "Erstellen von ClickOnce-Anwendungen für andere bereitstellen | Microsoft Docs"
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
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: d3a9762872f74b39d8cef387703488c01647dbcc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>Erstellen von ClickOnce-Anwendungen für die Bereitstellung durch Dritte
Nicht alle Entwickler, die ClickOnce-Bereitstellungen erstellen, planen, die Anwendungen selbst bereitstellen. Viele davon Packen ihre Anwendung einfach mithilfe von ClickOnce und leiten dann die Dateien an einen Kunden, z. B. einem großen Unternehmen. Der Kunde wird zum Hosten der Anwendung in einem Netzwerk zuständig. In diesem Artikel werden einige der in solchen Bereitstellungen in Versionen von .NET Framework vor Version 3.5 auftretenden Probleme. Klicken Sie dann beschrieben eine neue Projektmappe bereitgestellt, mit der neuen Funktion für "Anwendungsmanifest für Vertrauensstellungsinformationen verwenden" in .NET Framework 3.5. Schließlich geht mit empfohlenen Vorgehensweisen zum Erstellen von ClickOnce-Bereitstellungen für Kunden, die noch ältere Versionen von .NET Framework verwenden.  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>Probleme beim Erstellen von Bereitstellungen für Kunden  
 Verschiedene Probleme auftreten, wenn Sie eine Bereitstellung für einen Kunden bereitstellen möchten. Das erste Problem Codesignatur. Um in einem Netzwerk bereitgestellt werden, müssen das Bereitstellungsmanifest und Anwendungsmanifest für eine ClickOnce-Bereitstellung sowohl mit einem digitalen Zertifikat signiert werden. Dies löst die Frage, ob der Entwickler oder der Kunde Zertifikat beim Signieren der Manifeste verwendet.  
  
 Die Frage, welches Zertifikat zu verwenden ist wichtig, wie die digitale Signatur des Bereitstellungsmanifests eine ClickOnce-Anwendungsidentität basiert. Wenn der Entwickler das Bereitstellungsmanifest signiert, konnte es zu Konflikten führen, wenn der Kunde ein großes Unternehmen, und mehr als eine Abteilung des Unternehmens eine angepasste Version der Anwendung stellt.  
  
 Angenommen Sie, dass Adventure Works eine Finanzabteilung und eine Personalabteilung verfügt. Beide Abteilungen Lizenz eine ClickOnce-Anwendung von der Microsoft Corporation, die Berichte aus Daten in einer SQL-Datenbank generiert. Microsoft stellt jede Abteilung mit einer Version der Anwendung, die für ihre Daten angepasst wird. Wenn die Anwendungen mit dem gleichen Authenticode-Zertifikat signiert sind, würde ein Benutzer versucht, die beide Anwendungen verwenden einen Fehler auftreten, wie ClickOnce die zweite Anwendung als Anwendung mit dem ersten identisch ansehen würde. In diesem Fall kann der Kunde unvorhersehbare und unerwünschte Nebeneffekte auftreten, die den Verlust von Daten lokal gespeichert werden, von der Anwendung enthalten.  
  
 Ein zusätzliches Problem zusammenhängt, Signieren von code die `deploymentProvider` -Elements im Bereitstellungsmanifest, wo nach Anwendungsupdates suchen ClickOnce. Dieses Element muss dem Bereitstellungsmanifest vor dem Signieren hinzugefügt werden. Wenn dieses Element danach hinzugefügt wird, muss das Bereitstellungsmanifest erneut signiert werden.  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>Durch den Kunden um das Bereitstellungsmanifest zu signieren.  
 Eine Lösung für dieses Problem nicht eindeutigen Bereitstellungen ist die Entwickler Signieren des Anwendungsmanifests und der Kunde Signieren des Bereitstellungsmanifests. Dieser Ansatz funktioniert, zwar führt es andere Probleme. Da ein Authenticode-Zertifikat eine geschützte Ressource bleiben muss, kann nicht der Kunde nur das Zertifikat für dem Entwickler zum Signieren der Bereitstellungsstatus geben. Während der Kunde das Bereitstellungsmanifest selbst anmelden kann mithilfe von kostenlos verfügbare Tools mit dem .NET Framework-SDK, kann dies erfordert mehr technische Kenntnisse der Kunde ist als zulässig oder angeben zu können. In solchen Fällen erstellt der Entwickler in der Regel eine Anwendung, Website oder anderen Mechanismen, die über die Kunden ihre Version der Anwendung für die Signierung senden kann.  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>Die Auswirkungen des Kunden anmelden, das Sicherheit für ClickOnce-Anwendung  
 Auch wenn der Entwickler und der Kunde zustimmt, dass der Kunde Signieren des Anwendungsmanifests sollte, löst daraufhin andere Probleme, die die Anwendungsidentität umgeben, besonders, wenn sie für die Bereitstellung einer vertrauenswürdigen Anwendung gilt. (Weitere Informationen zu diesem Feature finden Sie unter [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).) Angenommen Sie, Adventure Works möchte seine Clientcomputer so konfigurieren, dass jede Anwendung, die ihnen von der Microsoft Corporation zur Verfügung mit voller Vertrauenswürdigkeit ausgeführt wird. Wenn Adventure Works das Bereitstellungsmanifest signiert hat, wird ClickOnce Adventure-Arbeit Sicherheitssignatur verwenden, um zu bestimmen, die Vertrauensebene der Anwendung klicken.  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>Erstellen von Kundenbereitstellungen mit Anwendungsmanifest für Vertrauensstellung  
 ClickOnce in .NET Framework 3.5 enthält ein neues Feature, das Entwicklern und Kunden erhalten eine neue Projektmappe auf das Szenario, wie die Manifeste signiert werden soll. Das ClickOnce-Anwendungsmanifest unterstützt ein neues Element mit dem Namen `<useManifestForTrust>` mit der ein Entwickler, um anzugeben, dass die digitale Signatur des Anwendungsmanifests ist, was zum treffen von Entscheidungen zur Vertrauenswürdigkeit verwendet werden soll. Der Entwickler verwendet ClickOnce-Tools zum Packen – wie z. B. Mage.exe und MageUI.exe mit Visual Studio – auf dieses Element im Manifest Anwendung enthalten, als auch den Herausgebernamen und den Namen der Anwendung aus, die in das Manifest eingebettet werden sollen.  
  
 Bei Verwendung `<useManifestForTrust>`, das Bereitstellungsmanifest muss nicht mit einem Authenticode-Zertifikat von einer Zertifizierungsstelle ausgestellt signiert werden. Stattdessen können sie mit ein selbst signiertes Zertifikat sogenannte signiert werden. Ein selbstsigniertes Zertifikat generiert von den Kunden oder der Entwickler mithilfe des standardmäßigen .NET Framework SDK-Tools, und klicken Sie dann auf das Bereitstellungsmanifest mit der ClickOnce-Bereitstellung Standardtools angewendet. Weitere Informationen finden Sie unter [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx).  
  
 Verwenden ein selbstsigniertes Zertifikat für das Bereitstellungsmanifest bietet mehrere Vorteile. Durch den Wegfall für den Kunden abrufen oder erstellen ihre eigenen Authenticode-Zertifikat `<useManifestForTrust>` vereinfacht die Bereitstellung für den Kunden, während des Entwicklers, ihre eigenen branding Identität für die Anwendung zu erhalten. Das Ergebnis ist eine Reihe von signierten Bereitstellungen, die mehr Sicherheit und eindeutigen Identitäten. Dadurch werden Konflikte, die von der Bereitstellung von derselben Anwendung für mehrere Kunden auftreten kann.  
  
 Ausführliche Informationen zur Vorgehensweise: erstellen eine ClickOnce-Bereitstellung mit `<useManifestForTrust>` aktiviert ist, finden Sie unter [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung, ist nicht erforderlich Re-Signing und behält Branding-Informationen](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>Wie Anwendungsmanifest für Vertrauensstellung funktioniert zur Laufzeit  
 Um ein besseres Verständnis der Funktionsweise der mit dem Anwendungsmanifest für Vertrauensstellung zur Laufzeit zu erhalten, sollten Sie das folgende Beispiel aus. Eine ClickOnce-Anwendung, die das .NET Framework 3.5 ausgerichtet ist, wird von Microsoft erstellt. Das Anwendungsmanifest verwendet die `<useManifestForTrust>` Element und von Microsoft signiert ist. Adventure Works signiert das Bereitstellungsmanifest mithilfe eines selbstsignierten Zertifikats. Adventure Works-Clients sind so konfiguriert, dass jede Anwendung, die von Microsoft signiert vertraut wird.  
  
 Klickt ein Benutzer einen Link zu das Bereitstellungsmanifest, installiert ClickOnce die Anwendung auf dem Computer des Benutzers. Das Zertifikat und Bereitstellungsinformationen finden identifizieren Sie die Anwendung eindeutig für ClickOnce auf dem Clientcomputer. Wenn der Benutzer versucht, dieselbe Anwendung von einem anderen Speicherort erneut zu installieren, kann ClickOnce diese Identität verwenden, um zu bestimmen, dass die Anwendung bereits auf dem Client vorhanden ist.  
  
 Als Nächstes untersucht ClickOnce die Authenticode-Zertifikat, das zum Signieren des Anwendungsmanifests, die die Ebene der Vertrauenswürdigkeit bestimmt, die ClickOnce gewähren verwendet wird. Da Adventure Works seinen Clients vertrauen Sie jede Anwendung, die von Microsoft signiert so konfiguriert wurde, wird diese ClickOnce-Anwendung volle Vertrauenswürdigkeit gewährt. Weitere Informationen finden Sie unter [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>Erstellen von Kundenbereitstellungen für frühere Versionen  
 Was geschieht, wenn ein Entwickler ClickOnce-Anwendungen für Kunden die Bereitstellung erfolgt, die ältere Versionen von .NET Framework verwenden? In den folgenden Abschnitten werden mehrere empfohlene Lösungen sowie die vor- und Nachteile der einzelnen zusammengefasst.  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>Anmelde-Bereitstellungen für Kunden  
 Eine mögliche Bereitstellungsstrategie ist für den Entwickler um einen Mechanismus, um Bereitstellungen im Auftrag des Kunden zu signieren, mit dem privaten Schlüssel des Kunden zu erstellen. Dadurch wird verhindert, dass den Entwickler müssen private Schlüssel oder mehrere Bereitstellungspakete verwaltet. Der Entwickler gibt die gleiche Bereitstellung nur den einzelnen Kunden. Es ist Aufgabe der Kunde es mit dem Signaturzertifikat Dienst für ihre Umgebung anpassen.  
  
 Ein Nachteil dieser Methode ist die Zeit und Aufwand, die für die Implementierung erforderlich sind. Während ein solchen Diensts mithilfe der Tools in der .NET Framework-SDK erstellt werden kann, wird es des Lebenszyklus Weitere Entwicklungszeit hinzugefügt.  
  
 Wie weiter oben in diesem Thema erwähnt, ist ein weiterer Nachteil, dass jedes Kunden Version der Anwendung die gleiche Identität, hat der zu Konflikten führen könnte. Wenn dies eine Rolle spielt, kann der Entwickler das Namensfeld ändern, das während der Generierung des Bereitstellungsmanifests verwendet wird, um jede Anwendung einen eindeutigen Namen zu geben. Dies wird eine separate Identität für jede Version der Anwendung erstellen, und potenzielle Identität Konflikte vermeiden. Dieses Feld entspricht der `-Name` Argument Mage.exe und damit die **Namen** Feld der **Namen** Registerkarte in MageUI.exe.  
  
 Angenommen Sie, dass der Entwickler eine Anwendung mit dem Namen Application1 erstellt hat. Statt einer einzelnen Bereitstellung mit dem Name-Feld auf Application1 festgelegt, kann der Entwickler mehrere Bereitstellungen mit einer Variation kundenspezifische auf diesen Namen, z. B. Application1-KundeA, Application1-KundeB erstellen und so weiter.  
  
### <a name="deploy-using-a-setup-package"></a>Die Bereitstellung über ein Setup-Paket  
 Eine zweite mögliche Bereitstellungsstrategie ist zum Generieren eines Microsoft-Setup-Projekts zum Ausführen der ersten Bereitstellung von ClickOnce-Anwendung. Dies kann in einem von mehreren verschiedenen Formaten angegeben werden: als MSI-Bereitstellung, wie eine ausführbare Datei (. (EXE) oder als eine CAB-Datei zusammen mit einem Batch-Skript.  
  
 Verwenden dieses Verfahren, würde der Entwickler der Kunde eine Bereitstellung bereitstellen, die enthält die Anwendungsdateien, das Anwendungsmanifest und ein Bereitstellungsmanifest, das als Vorlage dient. Der Kunde würde das Setup-Programm ausgeführt, das aufgefordert würden sie für eine bereitstellungs-URL (Server oder Dateifreigabe Speicherort aus dem Benutzer die ClickOnce-Anwendung installiert werden), sowie ein digitales Zertifikat. Die Setup-Anwendung kann auch auswählen, um zusätzliche ClickOnce-Konfigurationsoptionen, z. B. Kontrollkästchen Updateintervall aufzufordern. Nachdem diese Informationen gesammelt wurden, würde das Setup-Programm echte Bereitstellungsmanifest zu generieren, Signieren Sie sie und veröffentlichen die ClickOnce-Anwendung auf dem angegebenen Server.  
  
 Es gibt drei Möglichkeiten, die sich der Kunde das Bereitstellungsmanifest in dieser Situation kann:  
  
1.  Kunden können sich auf ein gültiges Zertifikat von einer Zertifizierungsstelle (CA) ausgegeben.  
  
2.  Eine Variation dieser Ansatz kann der Kunde auswählen, dass ihre Bereitstellungsmanifest mit einem selbstsignierten Zertifikat signiert. Der Nachteil hierbei ist, dass er führt die Anwendung die Wörter "Unbekannter Herausgeber" angezeigt, wenn der Benutzer gefragt, ob es installiert ist. Der Vorteil ist jedoch, dass es dadurch verhindert, dass kleinere Kunden die Zeit und Geld für ein von einer Zertifizierungsstelle ausgestelltes Zertifikat ausgeben müssen.  
  
3.  Schließlich kann Entwickler ihre eigenen selbstsignierten Zertifikats in der Setup-Paket einschließen. Die potenziellen Probleme mit Anwendungsidentität, die weiter oben in diesem Thema erläutert wird.  
  
 Der Nachteil der Setup-Projekt Bereitstellungsmethode ist die Zeit und Aufwand erforderlich, um eine benutzerdefinierte Bereitstellung-Anwendung erstellen.  
  
### <a name="have-customer-generate-deployment-manifest"></a>Haben Kunden generieren Bereitstellungsmanifest  
 Eine dritte mögliche Bereitstellungsstrategie ist nur die Anwendungsdateien und das Anwendungsmanifest zur hand deaktiviert an den Kunden. In diesem Szenario wird der Kunde verantwortlich für die Verwendung von .NET Framework SDK zum Erstellen und Signieren des Bereitstellungsmanifests.  
  
 Der Nachteil dieser Methode ist, dass dies erfordert, dass der Kunde die .NET Framework SDK-Tools zu installieren und ein Entwickler oder Systemadministrator, die bereits Erfahrung mit ihnen wird. Einige Kunden verlangen vielleicht eine Lösung, die nur wenig oder keine technische Aufwand Ihrerseits erforderlich sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von ClickOnce-Anwendungen für Tests und Produktionsserver ohne erneutes Signieren](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung, die kein erneutes Signieren erfordert und Brandinginformationen beibehält](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)