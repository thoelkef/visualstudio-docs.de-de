---
title: "Security, Versioning, and Manifest Issues in ClickOnce Deployments | Microsoft Docs"
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
  - "versioning, ClickOnce applications"
  - "ClickOnce applications, Windows Vista User Account Control"
  - "ClickOnce applications, versioning issues"
  - "security, ClickOnce applications"
  - "Windows 7, ClickOnce deployments"
  - "ClickOnce applications, manifest issues"
  - "User Account Control, ClickOnce applications"
  - "Windows Vista, ClickOnce deployments"
  - "manifests [ClickOnce]"
  - "ClickOnce applications, security issues"
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Security, Versioning, and Manifest Issues in ClickOnce Deployments
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verschiedenartige Probleme mit der Sicherheit, Versionsverwaltung für Anwendungen sowie Manifestsyntax und \-semantik von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] können eine erfolgreiche [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung verhindern.  
  
## Benutzerkontensteuerung in ClickOnce und Windows Vista  
 In [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] werden Anwendungen standardmäßig als Standardbenutzer ausgeführt, selbst wenn der aktuelle Benutzer mit einem Konto angemeldet ist, das über Administratorberechtigungen verfügt.  Wenn in einer Anwendung eine Aktion ausgeführt werden muss, für die Administratorberechtigungen erforderlich sind, wird das Betriebssystem benachrichtigt, das daraufhin den Benutzer auffordert, Administrator\-Anmeldeinformationen einzugeben.  Dieses Feature wird als Benutzerkontensteuerung \(User Account Control, UAC\) bezeichnet und verhindert, dass Anwendungen ohne die ausdrückliche Genehmigung durch einen Benutzer Änderungen vornehmen, die Auswirkungen auf das gesamte Betriebssystem haben können.  Windows\-Anwendungen benötigen diese Berechtigungserweiterung, da sie das `requestedExecutionLevel`\-Attribut im `trustInfo`\-Bereich des Anwendungsmanifests angeben.  
  
 Aufgrund des Risikos von Angriffen, dem Anwendungen bei der Sicherheitserweiterung unterliegen, können [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] \-Anwendungen keine Berechtigungserweiterung anfordern, wenn UAC für den Client aktiviert ist.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen, die versuchen, ihr `requestedExecutionLevel`\-Attribut auf `requireAdministrator` oder `highestAvailable` einzustellen, werden unter [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] nicht installiert.  
  
 Möglicherweise versucht die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung, aufgrund der Erkennungslogik des Installationsprogramms unter [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] bei der Ausführung Administratorberechtigungen zu verwenden.  In diesem Fall können Sie das `requestedExecutionLevel`\-Attribut im Anwendungsmanifest auf `asInvoker` festlegen.  Dadurch wird die Anwendung selbst ohne Erweiterung ausgeführt. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] fügt das Attribut automatisch allen Anwendungsmanifesten hinzu.  
  
 Wenn Sie eine Anwendung entwickeln, die für die gesamte Anwendungslebendauer Administratorberechtigungen erfordert, erwägen Sie stattdessen, die Anwendung mit der Windows Installer\-Technologie \(MSI\) bereitzustellen.  Weitere Informationen finden Sie unter [Windows Installer\-Grundlagen](../extensibility/internals/windows-installer-basics.md).  
  
## Kontingente für Onlineanwendungen und teilweise vertrauenswürdige Anwendungen  
 Wenn eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung nicht installiert, sondern online ausgeführt wird, muss sie dem für Onlineanwendungen reservierten Kontingent entsprechen.  Darüber hinaus darf die Größe einer Netzwerkanwendung, die beispielsweise aufgrund eingeschränkter Sicherheitsberechtigungen nur teilweise vertrauenswürdig ist, 50 % des Kontingents nicht überschreiten.  
  
 Weitere Informationen sowie Anweisungen dazu, wie das Kontingent für Onlineanwendungen geändert wird, finden Sie unter [ClickOnce Cache Overview](../deployment/clickonce-cache-overview.md).  
  
## Versionsprobleme  
 Wenn Sie einer Assembly einen starken Namen zuweisen und ihre Versionsnummer erhöhen, um ein Anwendungsupdate zu kennzeichnen, können Probleme auftreten.  Jede Assembly, die mit einem Verweis auf eine Assembly mit einem starken Namen kompiliert wurde, muss ebenfalls erneut kompiliert werden, da die Assembly andernfalls versucht, weiterhin auf die ältere Version zu verweisen.  Die Assembly versucht dies, weil in ihrer Bindungsanforderung der alte Versionswert verwendet wird.  
  
 Angenommen, es ist eine Assembly mit starkem Namen in einem eigenen Projekt mit Version 1.0.0.0 vorhanden.  Nach dem Kompilieren der Assembly fügen Sie sie als Verweis in das Projekt ein, das die Hauptanwendung enthält.  Wenn Sie nun die Assembly aktualisieren, die Version auf 1.0.0.1 erhöhen und versuchen, die Assembly bereitzustellen, ohne die Anwendung ebenfalls erneut zu kompilieren, ist die Anwendung zur Laufzeit nicht in der Lage, die Assembly zu laden.  
  
 Dieser Fehler kann nur auftreten, wenn Sie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Manifeste manuell bearbeiten. Wenn Sie die Bereitstellung hingegen mit [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] generieren, sollte der Fehler nicht auftreten.  
  
## Angeben von einzelnen .NET Framework\-Assemblys im Manifest  
 Ihre Anwendung kann nicht geladen werden, wenn Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung manuell bearbeitet haben, um auf eine ältere Version einer [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Assembly zu verweisen.  Wenn Sie z. B. einen Verweis auf die System.Net\-Assembly für eine Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] hinzugefügt haben, die älter ist als die im Manifest angegebene, tritt ein Fehler auf.  Sie sollten im Allgemeinen nicht versuchen, Verweise auf einzelne [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Assemblys anzugeben, da die Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], die für die Ausführung Ihrer Anwendung verwendet wird, als Abhängigkeit im Anwendungsmanifest angegeben wird.  
  
## Probleme mit der Manifestanalyse  
 Die von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwendeten Manifestdateien sind XML\-Dateien und müssen wohlgeformt und gültig sein. Sie müssen den XML\-Syntaxregeln entsprechen und nur Elemente und Attribute verwenden, die im relevanten XML\-Schema definiert sind.  
  
 Probleme in einer Manifestdatei können dadurch verursacht werden, dass für die Anwendung ein Name mit Sonderzeichen ausgewählt wird, z. B. einfache oder doppelte Anführungszeichen.  Der Name der Anwendung ist Teil ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Identität.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] analysiert derzeit keine Identitäten, die Sonderzeichen enthalten.  Wenn Ihre Anwendung nicht aktiviert werden kann, stellen Sie sicher, dass für den Namen nur alphabetische und numerische Zeichen verwendet werden. Versuchen Sie dann, die Anwendung erneut bereitzustellen.  
  
 Möglicherweise wurde das Bereitstellungs\- oder Anwendungsmanifest bei der manuellen Bearbeitung versehentlich beschädigt.  Ein beschädigtes Manifest verhindert eine ordnungsgemäße [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Installation.  Sie können derartige Fehler zur Laufzeit debuggen, indem Sie im Dialogfeld **ClickOnce\-Fehler** auf **Details** klicken und die Fehlermeldung im Protokoll lesen.  Das Protokoll enthält eine der folgenden Meldungen:  
  
-   Eine Beschreibung des Syntaxfehlers sowie die Zeilennummer und Zeichenposition des Fehlers.  
  
-   Den Namen eines Elements oder Attributs, dessen Verwendung gegen das Schema des Manifests verstößt.  Wenn Sie den Manifesten XML\-Code manuell hinzugefügt haben, müssen Sie diesen mit den Manifestschemas vergleichen.  Weitere Informationen finden Sie unter [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md) und [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
-   Einen ID\-Konflikt.  Abhängigkeitsverweise in Bereitstellungs\- und Anwendungsmanifesten müssen im `name`\-Attribut und im `publicKeyToken`\-Attribut eindeutig sein.  Wenn die beiden Attribute bei zwei Elementen in einem Manifest übereinstimmen, schlägt die Manifestanalyse fehl.  
  
## Vorkehrungen beim manuellen Ändern von Manifesten oder Anwendungen  
 Wenn Sie ein Anwendungsmanifest aktualisieren, müssen Sie sowohl das Anwendungsmanifest als auch das Bereitstellungsmanifest erneut signieren.  Das Bereitstellungsmanifest enthält einen Verweis auf das Anwendungsmanifest mit dem Hash dieser Datei und ihrer digitalen Signatur.  
  
### Vorkehrungen beim Verwenden der deploymentProvider\-Eigenschaft  
 Das [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungsmanifest enthält eine `deploymentProvider`\-Eigenschaft, die auf den vollständigen Pfad des Speicherorts verweist, von dem die Anwendung installiert und gewartet werden soll.  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Dieser Pfad wird festgelegt, wenn [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] die Anwendung erstellt, und er ist für installierte Anwendungen obligatorisch.  Der Pfad verweist auf den Standardspeicherort, von dem aus das [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Installationsprogramm die Anwendung installiert und in dem nach Updates gesucht wird.  Wenn Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung mit dem Befehl **xcopy** an einen anderen Speicherort kopieren, ohne die `deploymentProvider`\-Eigenschaft zu ändern, versucht [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] trotzdem, die Anwendung vom ursprünglichen Speicherort herunterzuladen.  
  
 Wenn Sie eine Anwendung verschieben oder kopieren möchten, müssen Sie auch den `deploymentProvider`\-Pfad aktualisieren, damit der Client die Installation vom neuen Speicherort vornimmt.  Das Aktualisieren dieses Pfads ist meistens erforderlich, wenn Sie Anwendungen installiert haben.  Bei Onlineanwendungen, die immer über die ursprüngliche URL gestartet werden, ist das Festlegen von `deploymentProvider` optional.  Wenn `deploymentProvider` festgelegt ist, wird diese Eigenschaft berücksichtigt, andernfalls fungiert die zum Aktivieren der Anwendung verwendete URL als Basis\-URL zum Herunterladen der Anwendungsdateien.  
  
> [!NOTE]
>  Bei jedem Aktualisieren des Anwendungsmanifests müssen Sie es auch erneut signieren.  
  
## Siehe auch  
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)   
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md)