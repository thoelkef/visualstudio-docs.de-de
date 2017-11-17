---
title: Sicherheit, Versionsverwaltung und Manifesten Probleme in ClickOnce-Bereitstellungen | Microsoft Docs
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
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: "21"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 603ff665e2c01abe62954e4e65e49a095d358b29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Probleme mit Sicherheit, Versionsverwaltung und Manifesten in ClickOnce-Bereitstellungen
Es gibt eine Vielzahl von Problemen mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Sicherheit, anwendungsversionsverwaltung, und manifest Syntax und Semantik, die dazu eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nicht für eine erfolgreiche Bereitstellung.  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce und Windows Vista-Benutzerkontensteuerung  
 In [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], Anwendungen standardmäßig als Standardbenutzer, ausführen, auch wenn der aktuelle Benutzer sich mit einem Konto angemeldet ist, die über Administratorberechtigungen verfügt. Wenn eine Anwendung eine Aktion, die Administratorberechtigungen erfordert ausführen muss, weist das Betriebssystem, das dann den Benutzer zur Eingabe ihrer Administratoranmeldeinformationen aufgefordert werden. Dieses Feature, das Benutzerkontensteuerung (UAC) benannt wird, wird verhindert, dass Anwendungen von Änderungen, die das gesamte Betriebssystem ohne explizite Zustimmung des Benutzers beeinflussen können. Windows-Anwendungen deklarieren, erfordern diese berechtigungserweiterung durch Angabe der `requestedExecutionLevel` Attribut in der `trustInfo` Abschnitt Anwendungsmanifest.  
  
 Aufgrund von das Risiko der Offenlegung von Anwendungen für die Erhöhung der Rechte für Sicherheitsangriffe [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen können keine berechtigungserweiterung angefordert, wenn für den Client UAC aktiviert ist. Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, die versucht, legen Sie dessen `requestedExecutionLevel` -Attribut `requireAdministrator` oder `highestAvailable` installiert nicht auf [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].  
  
 In einigen Fällen die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] versucht die Anwendung möglicherweise aufgrund von Installer Erkennungslogik mit Administratorberechtigungen ausgeführt, auf [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. In diesem Fall können Sie festlegen der `requestedExecutionLevel` -Attribut in das Anwendungsmanifest `asInvoker`. Dies bewirkt, dass die Anwendung zur Ausführung ohne Erhöhung der Rechte. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]Dieses Attribut hinzugefügt automatisch alle Anwendungsmanifeste.  
  
 Wenn Sie eine Anwendung, die über Administratorberechtigungen für die gesamte Lebensdauer der Anwendung erforderlich sind entwickeln, sollten Sie die Anwendung stattdessen mithilfe von Windows Installer (MSI)-Technologie bereitstellen. Weitere Informationen finden Sie unter [Grundlagen von Windows Installer](../extensibility/internals/windows-installer-basics.md).  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>Online-Anwendung Kontingente und teilweise Vertrauenswürdigkeit Anwendungen  
 Wenn Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung online "anstelle von" über eine Installation ausgeführt wird, muss es in das Kontingent für onlineanwendungen ereignissitzungspuffer passen. Darüber hinaus darf keine netzwerkanwendung, die mit einem eingeschränkten Satz von Sicherheitsberechtigungen, z. B. bei teilweiser Vertrauenswürdigkeit ausgeführt, größer als die Hälfte der die Kontingentgröße sein.  
  
 Weitere Informationen und Anweisungen dazu, wie Sie das Kontingent für die online-Anwendung zu ändern, finden Sie unter [ClickOnce-Cache: Übersicht](../deployment/clickonce-cache-overview.md).  
  
## <a name="versioning-issues"></a>Versionsprobleme  
 Es können Probleme auftreten, wenn Sie die Assembly einen starken Namen zuweisen und die Versionsnummer der Assembly ein Anwendungsupdate entsprechend erhöhen. Jede Assembly kompiliert, die mit einem Verweis auf eine Assembly mit starkem Namen muss selbst neu kompiliert werden, oder die Assembly versucht, die ältere Version zu verweisen. Die Assembly wird dies versucht, weil die Assembly den alten Versionswert in seine bindungsanforderung verwendet wird.  
  
 Angenommen Sie, dass Sie in einem eigenen Projekt mit Version 1.0.0.0 eine Assembly mit starkem Namen verfügen. Nach dem Kompilieren der Assemblys, fügen Sie ihn als Verweis auf das Projekt, das die Hauptassembly der Anwendung enthält. Wenn Sie die Assembly aktualisieren, die Version auf 1.0.0.1 erhöhen, und versuchen bereitzustellen, ohne auch die Anwendung neu zu kompilieren, wird die Anwendung nicht zum Laden der Assembly zur Laufzeit sein.  
  
 Dieser Fehler kann auftreten, nur, wenn Sie bearbeiten die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifeste manuell; Sie sollten diesen Fehler nicht auftreten, wenn Sie Ihre mit generieren [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Angeben von einzelnen .NET Framework-Assemblys im Manifest  
 Die Anwendung kann nicht geladen werden, wenn Sie manuell bearbeitet haben eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung in einer älteren Version von Verweisen eine [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Assembly. Angenommen, wenn Sie einen Verweis auf die Assembly System.Net für eine Version von hinzugefügt der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] vor der Version, die im Manifest angegeben wird, klicken Sie dann ein Fehler würde auftreten. Sie sollten im Allgemeinen nicht versuchen, geben Sie die Verweise auf einzelne [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Assemblys der Version der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] für die die Anwendung ausgeführt wird als eine Abhängigkeit im Anwendungsmanifest angegeben ist.  
  
## <a name="manifest-parsing-issues"></a>Analysieren von Problemen Manifest  
 Die Manifestdateien, mit denen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sind XML-Dateien, und sie müssen wohlgeformt und gültig sein: sie müssen unterliegen die Regeln der XML-Syntax und verwenden Sie nur Elemente und Attribute, die in den entsprechenden XML-Schema definiert.  
  
 Etwas, das in einer Manifestdatei zu Problemen führen können auszuwählen einen Namen für Ihre Anwendung, die ein Sonderzeichen, wie z. B. eine einfache oder doppelte Anführungszeichen enthält. Der Name der Anwendung ist Teil der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Identität. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]derzeit analysiert nicht Identitäten, die Sonderzeichen enthalten. Wenn Ihre Anwendung nicht aktivieren, stellen Sie sicher, dass Sie nur alphabetische und numerische Zeichen für den Namen, und versuchen es erneut bereitzustellen.  
  
 Wenn Sie Ihre Bereitstellung oder Manifeste manuell bearbeitet haben, Sie möglicherweise unbeabsichtigt sie beschädigt. Beschädigtes Manifest wird verhindert, dass eine richtige [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Installation. Sie können solche Fehler zur Laufzeit Debuggen, indem Sie auf **Details** auf die **ClickOnce-Fehler** (Dialogfeld), und lesen die Fehlermeldung in das Protokoll. Das Protokoll werden eine der folgenden Meldungen angezeigt:  
  
-   Eine Beschreibung der Syntaxfehler und die Zeilennummer und die Zeichen Position, wo der Fehler aufgetreten ist.  
  
-   Der Name des Elements oder Attributs in Verstoß gegen das Schema des Manifests verwendet. Wenn Sie XML manuell die Manifeste hinzugefügt haben, müssen Sie die Erweiterungen in das manifest Schemas zu vergleichen. Weitere Informationen finden Sie unter [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md) und [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md).  
  
-   Ein ID-Konflikt. Abhängigkeitsverweisen in bereitstellungs- und Anwendungsmanifeste müssen in beiden eindeutig sein ihre `name` und `publicKeyToken` Attribute. Wenn beide Attribute zwischen zwei beliebigen Elementen innerhalb eines Manifests übereinstimmen, wird das manifest Analyse nicht erfolgreich.  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Vorsichtsmaßnahmen beim Manifesten oder Anwendungen manuell zu ändern  
 Wenn Sie ein Anwendungsmanifest aktualisieren, müssen Sie das Anwendungsmanifest und das Bereitstellungsmanifest erneut signieren. Das Bereitstellungsmanifest enthält einen Verweis auf das Anwendungsmanifest, das diese Datei Hash und ihrer digitalen Signatur enthält.  
  
### <a name="precautions-with-deployment-provider-usage"></a>Vorsichtsmaßnahmen, die mit der Bereitstellung Dienstanbieter-Nutzungsendpunkt  
 Die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsmanifest hat einen `deploymentProvider` Eigenschaft verweist auf den vollständigen Pfad des Speicherorts aus, in dem die Anwendung installiert und gewartet werden soll:  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Dieser Pfad wird festgelegt, wenn [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] die Anwendung erstellt und ist zwingend vorgeschrieben, zu den installierten Anwendungen. Der Pfad verweist auf den Standardpfad an, in dem die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Installer installiert die Anwendung aus, und Suchen nach Updates. Bei Verwendung von der **Xcopy** Befehl zum Kopieren einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung an einen anderen Speicherort, aber nicht die `deploymentProvider` -Eigenschaft, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wird weiterhin verweisen zurück an den ursprünglichen Speicherort beim Versuch zum Herunterladen der die Anwendung.  
  
 Wenn Sie eine Anwendung verschieben oder kopieren möchten, müssen Sie auch Aktualisieren der `deploymentProvider` Pfad, damit der Client tatsächlich von den neuen Speicherort installiert. Aktualisieren diesen Pfad ist meist Besorgnis installierte Anwendungen. Für online-Anwendungen, die immer über die ursprüngliche URL festlegen gestartet werden die `deploymentProvider` ist optional. Wenn `deploymentProvider` festgelegt ist, wird es berücksichtigt; die URL zum Starten der Anwendung verwendet wird, andernfalls als Basis-URL verwendet werden, zum Herunterladen der Anwendungsdateien.  
  
> [!NOTE]
>  Jedes Mal, wenn Sie das Manifest aktualisieren, müssen Sie auch erneut signieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)