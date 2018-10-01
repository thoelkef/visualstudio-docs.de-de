---
title: Probleme mit Sicherheit, Versionsverwaltung und Manifesten in ClickOnce-Bereitstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
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
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 1274a636dd49a2ade1f21941d24817a0d54d49c4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516218"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Probleme mit Sicherheit, Versionsverwaltung und Manifesten in ClickOnce-Bereitstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Probleme mit Sicherheit, Versionsverwaltung und Manifesten in ClickOnce-Bereitstellungen](https://docs.microsoft.com/visualstudio/deployment/security-versioning-and-manifest-issues-in-clickonce-deployments).  
  
Es gibt eine Vielzahl von Problemen bei der [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Sicherheit, versionsverwaltung von Anwendungen, und manifest-Syntax und Semantik, die dazu führen können, dass eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nicht für eine erfolgreiche Bereitstellung.  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce und Windows Vista-Benutzerkontensteuerung  
 In [!INCLUDE[windowsver](../includes/windowsver-md.md)], Anwendungen standardmäßig als ein Standardbenutzer ausführen, auch wenn der aktuelle Benutzer sich mit einem Konto angemeldet ist, die über Administratorberechtigungen verfügt. Wenn eine Anwendung eine Aktion, die Administratorberechtigungen erforderlich sind durchführen muss, weist er das Betriebssystem, das dann den Benutzer zur Eingabe ihrer Anmeldeinformationen aufgefordert werden. Diese Funktion, die Benutzerkontensteuerung (UAC) benannt wird, verhindert, dass Anwendungen vornehmen von Änderungen, die ohne explizite Zustimmung des Benutzers das gesamte Betriebssystem betreffen können. Windows-Anwendungen zu deklarieren, erfordern diese Ausweitung von Berechtigungen durch Angabe der `requestedExecutionLevel` -Attribut in der `trustInfo` Abschnitt Anwendungsmanifest.  
  
 Aufgrund des Risikos von Anwendungen für erhöhte Rechte für Sicherheitsangriffe verfügbar zu machen [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen können nicht über erweiterte Berechtigungen anfordern, wenn UAC, für den Client aktiviert ist. Alle [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung, die versucht, legen Sie dessen `requestedExecutionLevel` Attribut `requireAdministrator` oder `highestAvailable` installiert nicht auf [!INCLUDE[windowsver](../includes/windowsver-md.md)].  
  
 In einigen Fällen Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] möglicherweise wird versucht, die aufgrund der Logik zur Erkennung von Installer mit Administratorberechtigungen ausgeführt, auf [!INCLUDE[windowsver](../includes/windowsver-md.md)]. In diesem Fall können Sie festlegen der `requestedExecutionLevel` -Attribut in das Anwendungsmanifest `asInvoker`. Dadurch wird die Anwendung selbst für die Ausführung ohne erhöhte Rechte. [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] alle Anwendungsmanifeste hinzugefügt automatisch dieses Attribut.  
  
 Wenn Sie eine Anwendung, die über Administratorberechtigungen für die gesamte Lebensdauer der Anwendung erforderlich sind entwickeln, sollten Sie erwägen, Bereitstellen der Anwendung, indem Sie stattdessen die Windows Installer (MSI)-Technologie verwenden. Weitere Informationen finden Sie unter [Windows Installer-Grundlagen](../extensibility/internals/windows-installer-basics.md).  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>Online-Anwendung-Kontingente und teilweise Vertrauenswürdigkeit Anwendungen  
 Wenn Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung online "anstelle von" durch eine Installation ausgeführt wird, muss es in das festgelegte Kontingent reserviert für online-Anwendungen passen. Darüber hinaus eine netzwerkanwendung, die bei teilweiser Vertrauenswürdigkeit wie z. B. mit einem eingeschränkten Satz von Sicherheitsberechtigungen ausgeführt, größer als die Hälfte der Größe des Speicherkontingents für den nicht möglich.  
  
 Weitere Informationen und Anweisungen dazu, wie Sie das Kontingent für die online-Anwendung zu ändern, finden Sie unter [Übersicht über die ClickOnce-Cache](../deployment/clickonce-cache-overview.md).  
  
## <a name="versioning-issues"></a>Probleme bei der versionsverwaltung  
 Sie können Probleme auftreten, wenn Sie Ihrer Assembly einen starken Namen zuweisen und erhöht die Versionsnummer der Assembly ein Anwendungsupdate entsprechend. Jede Assembly kompiliert, die mit einem Verweis auf eine Assembly mit starkem Namen selbst neu kompiliert werden muss, oder die Assembly wird versucht, auf die ältere Version verweisen. Die Assembly wird diese verwenden, da die Assembly den alte Wert in seine bindungsanforderung verwendet wird.  
  
 Angenommen Sie, dass Sie in einem eigenen Projekt mit Version 1.0.0.0 eine Assembly mit starkem Namen verfügen. Nach dem Kompilieren der Assemblys an, fügen Sie ihn als Verweis auf das Projekt, das Ihre hauptanwendung enthält. Wenn Sie die Assembly zu aktualisieren, erhöhen die Version 1.0.0.1, und versuchen Sie es, bereitzustellen, ohne auch die Anwendung erneut zu kompilieren, wird die Anwendung nicht zum Laden der Assembly zur Laufzeit möglich sein.  
  
 Dieser Fehler kann auftreten, nur, wenn Sie Bearbeiten Ihrer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Manifeste manuell; Sie sollten diesen Fehler nicht feststellen, wenn Sie Ihre Bereitstellung mit generieren [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)].  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Einzelne .NET Framework-Assemblys angeben im Manifest  
 Ihre Anwendung kann nicht geladen werden, wenn Sie manuell bearbeitet haben eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung in einer älteren Version von Verweisen auf eine [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Assembly. Z. B., wenn Sie einen Verweis auf die Assembly System.Net für eine Version von hinzugefügt haben die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] vor der Version, die im Manifest angegeben wird, klicken Sie dann ein Fehler würde auftreten. Sie sollten im Allgemeinen nicht versuchen, geben Sie die Verweise auf einzelne [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Assemblys der Version, die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] für die die Anwendung ausgeführt wird als eine Abhängigkeit im Anwendungsmanifest angegeben ist.  
  
## <a name="manifest-parsing-issues"></a>Probleme mit der Manifestanalyse  
 Die Manifestdateien, mit denen [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sind XML-Dateien, und sie müssen wohlgeformt und gültig sein: sie müssen unterliegen den Regeln der XML-Syntax und verwenden Sie nur Elemente und Attribute, die in der entsprechenden XML-Schema definiert.  
  
 Etwas, das Probleme, in einer Manifestdatei verursachen können wird einen Namen für Ihre Anwendung auswählen, die ein Sonderzeichen, wie z. B. eine einfache oder doppelte Anführungszeichen enthält. Der Name der Anwendung ist Teil der [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Identität. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Derzeit wird analysiert keine Identitäten, die Sonderzeichen enthalten. Wenn Ihre Anwendung nicht aktivieren, stellen Sie sicher, dass Sie nur alphabetische und numerische Zeichen für den Namen, und versuchen sie erneut bereitstellen.  
  
 Wenn Sie Ihre bereitstellungs- noch die Anwendungsmanifeste manuell bearbeitet haben, Sie möglicherweise unbeabsichtigt sie beschädigt. Beschädigtes Manifest wird verhindert, dass eine korrekte [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Installation. Sie können solche Fehler zur Laufzeit Debuggen, indem Sie auf **Details** auf die **ClickOnce-Fehler** (Dialogfeld), und die Fehlermeldung in das Protokoll lesen. Das Protokoll Listet die folgenden Meldungen:  
  
-   Eine Beschreibung der Syntaxfehler, und die Zeilennummer und Zeichenposition Position, in dem der Fehler aufgetreten ist.  
  
-   Der Name der ein Element oder Attribut verwendet wird, gegen das Schema des Manifests. Wenn Sie XML manuell den Manifesten hinzugefügt haben, müssen Sie die Erweiterungen, die von Manifestschemas verglichen werden soll. Weitere Informationen finden Sie unter [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md) und [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md).  
  
-   Ein ID-Konflikt auftritt. Dependency-Verweise in bereitstellungs- und Anwendungsmanifeste müssen in beiden eindeutig sein ihre `name` und `publicKeyToken` Attribute. Wenn beide Attribute zwischen zwei beliebigen Elementen in einem Manifest übereinstimmen, ist das manifest Analyse nicht erfolgreich.  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Vorsichtsmaßnahmen bei der Manifeste oder Anwendungen manuell zu ändern.  
 Wenn Sie ein Anwendungsmanifest aktualisieren, müssen Sie sowohl das Anwendungsmanifest und das Bereitstellungsmanifest erneut signieren. Das Bereitstellungsmanifest enthält einen Verweis auf das Anwendungsmanifest, das diese Dateihash und seiner digitalen Signatur enthält.  
  
### <a name="precautions-with-deployment-provider-usage"></a>Vorsichtsmaßnahmen bei der Bereitstellung Anbieter Nutzung  
 Die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellungsmanifest hat einen `deploymentProvider` Eigenschaft verweist auf den vollständigen Pfad des Speicherorts aus, in dem die Anwendung installiert und gewartet werden soll:  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Dieser Pfad wird festgelegt, wenn [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wird die Anwendung erstellt und ist obligatorisch, zu den installierten Anwendungen. Der Pfad verweist auf den Standardspeicherort, in denen die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Installer installiert die Anwendung aus, und Suchen nach Updates. Bei Verwendung von der **Xcopy** -Befehl zum Kopieren einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung an einen anderen Speicherort, aber keine Änderungen der `deploymentProvider` -Eigenschaft, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wird immer noch zurückgreifen am ursprünglichen Speicherort, wenn versucht wird, Herunterladen der die Anwendung.  
  
 Wenn Sie eine Anwendung verschieben oder kopieren möchten, müssen Sie auch aktualisieren die `deploymentProvider` Pfad, damit der Client vom neuen Speicherort vornimmt. Aktualisiert diesen Pfad ist vor allem relevant, wenn Sie die Anwendungen installiert haben. Für online-Anwendungen, die immer über die ursprüngliche URL, die Einstellung gestartet, werden die `deploymentProvider` ist optional. Wenn `deploymentProvider` festgelegt ist, wird es berücksichtigt werden; andernfalls wird zum Starten der Anwendung verwendete URL als Basis-URL verwendet werden, zum Herunterladen von Anwendungsdateien.  
  
> [!NOTE]
>  Jedes Mal, wenn Sie das Manifest aktualisieren, müssen Sie es auch erneut signieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)



