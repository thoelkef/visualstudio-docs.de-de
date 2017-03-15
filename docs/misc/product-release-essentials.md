---
title: "Grundlagen zu Produktversionen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Bereitstellung, Grundlagen"
  - "Installation [Visual Studio SDK], Grundlagen"
ms.assetid: 28370bc8-f3a7-4c5e-9b35-8331cda14ff4
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Grundlagen zu Produktversionen
Ein angenehmes und stabiles Setuperlebnis hinterlässt in den Köpfen der Benutzer einen bleibenden Eindruck hinsichtlich Ihres [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Integrationsprodukts. Ein unangenehmes Setuperlebnis hinterlässt ebenfalls einen bleibenden Eindruck, daher stellt das Befolgen bewährter Methoden beim Entwickeln und Testen des Setups einen lohnenden Aufwand dar.  
  
## Entwickeln von Setuppaketen für Windows Installer  
 Windows Installer ist der empfohlene Installations\- und Konfigurationsdienst für Windows und für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Integrationsprodukte.  
  
> [!NOTE]
>  Die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]\-Dokumentation zur Installation von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Integrationsprodukten baut auf Windows Installer\-Konzepten auf, behandelt Windows Installer aber nicht selbst. Links zu relevanten Abschnitten der Windows Installer\-Dokumentation finden Sie in der folgenden Tabelle.  
  
 Im Setupkontext bezieht sich *Komponente* auf eine Windows Installer\-Komponente. Komponenten enthalten Ressourcen wie Dateien und Registrierungseinträge und werden als Einheit installiert und entfernt.  
  
|Aufgabe|Weitere Informationen finden Sie unter|  
|-------------|--------------------------------------------|  
|Weitere Informationen zu Windows Installer.|[Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx)|  
|Ermitteln Sie Ihre Systemanforderungen für VSPackage.|-   [Ermitteln von Systemanforderungen](../extensibility/internals/detecting-system-requirements.md)|  
|Erfahren Sie, wie Sie ein VSPackage in einem Setuppaket registrieren.|-   [VSPackage\-Registrierung](../extensibility/internals/vspackage-registration.md)<br />-   [Befehle, die nach der Installation ausgeführt werden müssen](../extensibility/internals/commands-that-must-be-run-after-installation.md)|  
|Weitere Informationen erhalten Sie in einem Installationspaketbeispiel.|-   Setupbeispiel zur IronPython\-Integration|  
  
## Unterstützung von parallelen Produkten  
 „Parallel“ \(manchmal auch als *SxS* bezeichnet\) bezieht sich auf die Fähigkeit, mehrere Versionen desselben Produkts parallel installieren und sogar gleichzeitig ausführen zu können. Für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Integrationsprodukte bezieht sich dieser Begriff auch auf die Tatsache, dass die parallele Ausführung von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] selbst unterstützt wird.  
  
|Aufgabe|Weitere Informationen finden Sie unter|  
|-------------|--------------------------------------------|  
|Erhalten Sie weitere Informationen zur Unterstützung von mehreren Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in Ihrem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Integrationsprodukt.|-   [Auswählen zwischen freigegebenen und versioniert VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md)<br />-   [Verwaltung von Komponenten](../extensibility/internals/component-management.md)|  
|Erhalten Sie weitere Informationen zur Unterstützung Ihres [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Integrationsprodukts.|-   [Auswählen zwischen freigegebenen und versioniert VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md)<br />-   [Registrieren von Dateinamenerweiterungen für Seite\-an\-Seite\-Installationen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)<br />-   [Ermitteln von Systemanforderungen](../extensibility/internals/detecting-system-requirements.md)<br />-   [Befehle, die nach der Installation ausgeführt werden müssen](../extensibility/internals/commands-that-must-be-run-after-installation.md)|  
  
## Testen Ihres Visual Studio\-Integrationsprodukts  
 Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-VSIT\-Suite \(Visual Studio Integration Test\) umfasst eine Reihe von Tests, mit denen überprüft wird, ob ein VSPackage ordnungsgemäß in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integriert wurde. VSIT testet keine VSPackage\-Funktionen, hilft aber dabei sicherzustellen, dass ein VSPackage keine anderen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Funktionen beeinträchtigt. Weitere Informationen finden Sie unter [Visual Studio\-Integrationstests](http://msdn.microsoft.com/de-de/8d741735-7d93-46c2-ab93-01da7a0e016d).