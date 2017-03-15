---
title: "Statuspersistenz und die Visual Studio-IDE | Microsoft Docs"
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
  - "IDE-Einstellungen, Statuspersistenz"
  - "Benutzereinstellungen [Visual Studio SDK], beibehalten"
  - "Seiten „Extras – Optionen“ [Visual Studio SDK], Einstellungen beibehalten"
  - "IDE, Statuspersistenz"
  - "Persistenz, Benutzereinstellungen"
ms.assetid: fdd49bb1-ed3b-4428-b685-de65c3215c1c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Statuspersistenz und die Visual Studio-IDE
Der **Einstellungen importieren und exportieren** Befehl für das **Extras** Menü der integrierten Entwicklungsumgebung \(IDE\) importiert und exportiert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Anpassungen der Umgebung.  Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Einstellungen [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] APIs in einem VSPackage aktivieren, die beibehalten werden sollen Einstellungskategorien Variablen Zustand \(Gruppen\) zu definieren, eine oder mehrere **Einstellungen importieren und exportieren** , wenn ein Benutzer den Befehl auswählt.  
  
 Ein GUID eindeutig identifiziert eine Einstellungskategorie und wird in einem eigenen Registrierungseintrag definiert, so genannte ein *benutzerdefinierter Einstellungs\-Punkt*.  
  
> [!NOTE]
>  Die standardmäßige Implementierungen der Seiten **Extras**des**OptionenToolbox**und des `Microsoft.VisualStudio.Shell.DialogPage` bieten Unterstützung für Persistenz automatisch.  Die Einstellungen API können den standardmäßigen Mechanismus überschrieben werden.  Weitere Informationen finden Sie unter [Erweitern der Toolbox](../misc/extending-the-toolbox.md), [Optionen\-Seiten](../misc/options-pages.md) und <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
## In diesem Abschnitt  
 [Unterstützung für Benutzereinstellungen](../extensibility/internals/support-for-user-settings.md)  
 Beschreibt die Registrierungseinstellungen \(benutzerdefinierter Einstellungs\-Punkt\) und Attribute, die verwendet werden, um eine Implementierung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Einstellungen an, die von bestimmten VSPackage verwendet wird.  
  
 [Gewusst wie: Exportieren von Einstellungen mithilfe von Interop\-Assemblys](../misc/how-to-export-settings-by-using-interop-assemblies.md)  
 Stellt eine ausführliche Beschreibung darüber bereit, wie Sie Unterstützung zum Speichern von Konfigurationsdaten mithilfe des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Einstellungen für Interop\-Assembly basiertes Mechanismus für die VSPackages implementiert.  
  
 [Gewusst wie: Verwenden von Interopassemblys zum Importieren von Einstellungen](../misc/how-to-use-interop-assemblies-to-import-settings.md)  
 Stellt eine ausführliche Beschreibung darüber bereit, wie Sie Unterstützung für das Abrufen von Konfigurationsdaten mithilfe des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Einstellungen für Interop\-Assembly basiertes Mechanismus für die VSPackages implementiert.  
  
 [Exportieren von Einstellungen](../misc/exporting-settings.md)  
 Enthält eine ausführliche Beschreibung darüber, wie die Unterstützung zum Speichern von Konfigurationsdaten mithilfe des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Fehlerbehandlungsmechanismus für verwaltetes Paketframework basiertes Einstellungen VSPackages implementiert.  
  
 [Importieren von Einstellungen](../misc/importing-settings.md)  
 Stellt eine ausführliche Beschreibung darüber bereit, wie Sie Unterstützung für das Abrufen von Konfigurationsdaten mithilfe des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Fehlerbehandlungsmechanismus für verwaltetes Paketframework basiertes Einstellungen VSPackages implementiert.  
  
## Verwandte Abschnitte  
 [Working with Settings](http://msdn.microsoft.com/de-de/4c0a56ab-6091-4ebc-9dc7-52c40846bacb)  
 Beschreibt, wie die Export\/Import abschnitte der IDE verwaltet.  
  
 [Optionen\-Seiten](../misc/options-pages.md)  
 Beschreibt die Unterstützung, die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] automatisch zum Verwalten von vorhandenen oder neuen Seiten erstellenden **Extras Optionen** zulässig.  
  
 [Erweitern der Toolbox](../misc/extending-the-toolbox.md)  
 Erläutert die Unterstützung, die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] automatisch zum Verwalten oder das Erweitern **Toolbox**zulässig.  
  
 [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)  
 Beschreibt, wie mit dem Programm VSPackage Benutzereinstellungen erhält und verwaltet.