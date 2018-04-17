---
title: Registrieren von Projekt- und Elementvorlagen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85c22d0191d015979dff5a4845c4dda0af96ee60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="registering-project-and-item-templates"></a>Registrieren von Projekt- und Elementvorlagen
Projekttypen müssen die Verzeichnisse registrieren, wo ihre Projekt- und Element Vorlagen befinden. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet die Registrierungsinformationen Ihre Projekttypen zugeordnet, welche anzuzeigende in der **neues Projekt hinzufügen** und **neues Element hinzufügen** Dialogfelder.  
  
 Weitere Informationen zu Vorlagen finden Sie unter [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="registry-entries-for-projects"></a>Registrierungseinträge für Projekte  
 Die folgenden Beispiele zeigen die Registrierungseinträge unter HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*Version*>. Die zugehörigen Tabellen werden die Elemente, die in den Beispielen verwendete erläutert.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|name|Typ|Beschreibung|  
|----------|----------|-----------------|  
|@|REG_SZ|Der Standardname der Projekte dieser Art.|  
|DisplayName|REG_SZ|Ressourcen-ID mit dem Namen aus der Satelliten-DLL abgerufen werden sollen, die unter Pakete registriert werden.|  
|Package|REG_SZ|Klassen-ID des Pakets unter "Pakete" registriert.|  
|ProjectTemplatesDir|REG_SZ|Der Standardpfad der Projektvorlage für Dateien. Die Projektvorlage-Dateien werden angezeigt, indem die **neues Projekt** Vorlage.|  
  
### <a name="registering-item-templates"></a>Registrieren von Elementvorlagen  
 Sie müssen das Verzeichnis, in dem Sie Vorlagen speichern, registrieren.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|name|Typ|Beschreibung|  
|----------|----------|-----------------|  
|@|REG_SZ|Ressourcen-ID für Elementvorlagen hinzufügen.|  
|TemplatesDir|REG_SZ|Pfad der Projektelemente angezeigt, klicken Sie im Dialogfeld für die **neues Element hinzufügen** Assistenten.|  
|TemplatesLocalizedSubDir|REG_SZ|Ressourcen-ID, der eine Zeichenfolge, die das Unterverzeichnis des TemplatesDir mit dem Namen enthält lokalisierte Vorlagen. Da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lädt die Zeichenfolgenressource Satelliten-DLLs haben sie ausgeführt wird, jede Satelliten-DLL kann eine andere lokalisierte Unterverzeichnisnamen enthalten.|  
|SortPriority|REG_DWORD|Legen Sie SortPriority, um die Reihenfolge steuern, in der Vorlagen, in angezeigt werden, der **neues Element hinzufügen** (Dialogfeld). Größere SortPriority Werte, die weiter oben in der Vorlagenliste angezeigt werden.|  
  
### <a name="registering-file-filters"></a>Dateifilter registrieren  
 Sie können optional Filter registrieren, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet, wenn er für Dateinamen aufgefordert werden. Z. B. die [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filter für die die **geöffnete Datei** Dialogfeld können Sie:  
  
 **Visual C#-Dateien (\*cs,\*RESX,\*"Settings",\*.xsd,\*"WSDL");\*. Cs,\*RESX,\*"Settings",\*.xsd,\*"WSDL")**  
  
 Um die Registrierung von mehreren Filtern zu unterstützen, ist jedem Filter in einem eigenen Unterschlüssel unter HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio registriert\\<*Version*> \Projects\\{} \< *ProjectGUID*>} \Filters\\<*Unterschlüssel*>. Der Name des Unterschlüssels ist beliebig. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Name des Unterschlüssels ignoriert und nur die Werte verwendet.  
  
 Sie können die Kontexte steuern, in denen ein Filter verwendet wird, durch Festlegen von Flags, die in der folgenden Tabelle gezeigt. Wenn ein Filter keine Flags festgelegt, wird es nach dem häufig verwendete Filter in aufgeführt werden die **vorhandenes Element hinzufügen** Dialogfeld und die **geöffnete Datei** (Dialogfeld), aber es wird nicht in verwendet werden die **in Dateien suchen**  (Dialogfeld).  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|name|Typ|Beschreibung|  
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG_DWORD|Stellt den Filter eine häufig verwendete Filter in der **in Dateien suchen** (Dialogfeld). Häufig verwendete Filter werden in der Filterliste vor Filtern, die nicht markiert als allgemeiner aufgeführt.|  
|CommonOpenFilesFilter|REG_DWORD|Stellt den Filter eine häufig verwendete Filter in der **Dateiöffnungsmodus** (Dialogfeld). Häufig verwendete Filter werden in der Filterliste vor Filtern, die nicht markiert als allgemeiner aufgeführt.|  
|FindInFilesFilter|REG_DWORD|Führt den Filter nach dem häufig verwendete Filter in der **in Dateien suchen** (Dialogfeld).|  
|NotOpenFileFilter|REG_DWORD|Gibt an, dass der Filter nicht, in verwendet wird der **Dateiöffnungsmodus** (Dialogfeld).|  
|NotAddExistingItemFilter|REG_DWORD|Gibt an, dass der Filter nicht, in verwendet wird der **vorhandenes Element hinzufügen** (Dialogfeld).|  
|SortPriority|REG_DWORD|Legen Sie SortPriority, um die Reihenfolge steuern, in der Filter angezeigt werden. Größere SortPriority Werte, die weiter oben in der Filterliste angezeigt werden.|  
  
## <a name="directory-structure"></a>Verzeichnisstruktur  
 VSPackages können Dateien und Ordnern an einer beliebigen Stelle auf einem lokalen oder Remotecomputer Datenträger einfügen als die Position über die integrierte Entwicklungsumgebung (IDE) registriert ist. Zur Vereinfachung der Organisation empfehlen wir jedoch die folgende Verzeichnisstruktur Ihres Produkts-Installationspfad.  
  
 \Templates  
  
 \Projects (enthält die Projektvorlagen)  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems (enthält die Projektelemente)  
  
 \Class  
  
 \Form  
  
 \Web Seite  
  
 \HelperFiles (enthält die Dateien, die in mehreren Dateien Projektelementen verwendet)  
  
 \WizardFiles  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Assistenten](../../extensibility/internals/wizards.md)   
 [Lokalisieren von Anwendungen](../../ide/localizing-applications.md)   
 [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)