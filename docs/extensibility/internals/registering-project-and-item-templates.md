---
title: "Registrieren von Projekt- und Elementvorlagen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekte [Visual Studio SDK], Hinzufügen von Elementen"
  - "im Dialogfeld Neues Element hinzufügen-Registrierung"
  - "Dialogfeld "Neues Element hinzufügen""
  - "Im Dialogfeld Neues Projekt hinzufügen"
  - "Registrierung im Dialogfeld Neues Projekt hinzufügen"
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# Registrieren von Projekt- und Elementvorlagen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Projekttypen müssen die Verzeichnisse registrieren, wo sich ihre Projekt\- und Element Vorlagen befinden.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Bestimmt die Registrierungsinformationen, die Ihre Projekttypen zugeordnet, was zum Anzeigen in der **Neues Projekt hinzufügen** und **Neues Element hinzufügen** Dialogfelder.  
  
 Weitere Informationen zu Vorlagen finden Sie unter [Hinzufügen von Projekt\- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## Registrierungseinträge für Projekte  
 Die folgenden Beispiele zeigen die Registrierungseinträge unter HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ \<*Version*\>. Die zugehörigen Tabellen werden die Elemente, die in den Beispielen verwendete erläutert.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|Name|Typ|Beschreibung|  
|----------|---------|------------------|  
|@|REG\_SZ|Der Standardname der Projekte dieser Art.|  
|DisplayName|REG\_SZ|Ressourcen\-ID des Namens aus der Satelliten\-DLL abgerufen werden sollen, die unter Pakete registriert werden.|  
|Package|REG\_SZ|Klassen\-ID des Pakets unter Pakete registriert.|  
|ProjectTemplatesDir|REG\_SZ|Der Standardpfad der Projektvorlage Dateien. Die Projektvorlage\-Dateien werden angezeigt, durch die **Neues Projekt** Vorlage.|  
  
### Registrieren von Elementvorlagen  
 Sie müssen das Verzeichnis registrieren, wo Sie Vorlagen speichern.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|Name|Typ|Beschreibung|  
|----------|---------|------------------|  
|@|REG\_SZ|Ressourcen\-ID für Elementvorlagen hinzufügen.|  
|TemplatesDir|REG\_SZ|Pfad der Projektelemente angezeigt wird, klicken Sie im Dialogfeld für die **Neues Element hinzufügen** Assistenten.|  
|TemplatesLocalizedSubDir|REG\_SZ|Ressourcen\-ID, der eine Zeichenfolge, die mit dem Namen TemplatesDir im Unterverzeichnis enthält lokalisierte Vorlagen. Da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lädt die Zeichenfolgenressource Satelliten\-DLLs wurden, jede Satelliten\-DLL kann eine andere lokalisierte Unterverzeichnisnamen enthalten.|  
|SortPriority|REG\_DWORD|Legen Sie SortPriority, um die Reihenfolge zu bestimmen, in der Vorlagen, in angezeigt werden, der **Neues Element hinzufügen** \(Dialogfeld\). Größere SortPriority Werte werden oben in der Vorlagenliste angezeigt.|  
  
### Registrieren der Dateifilter  
 Sie können optional Filter registrieren, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird verwendet, wenn für Dateinamen gefragt werden. Z. B. die [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filter für die die **geöffnete Datei** Dialogfeld ist:  
  
 **Visual C\#\-Dateien \(\*.cs, \*.resx, \*.settings, \*.xsd, \*.WSDL\); \*.cs, \*.resx, \*.settings, \*.xsd, \*.WSDL\)**  
  
 Um die Registrierung von mehreren Filtern zu unterstützen, wird jeder Filter in einen eigenen Unterschlüssel unter HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ registriert \<*Version*\> \\Projects\\ {\<*ProjectGUID*\>} \\Filters\\ \<*Unterschlüssel*\>. Der Name des Unterschlüssels ist beliebig. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignoriert den Unterschlüssel Namen und nur die Werte verwendet.  
  
 Sie können die Kontexte steuern, in denen ein Filter verwendet wird, durch Festlegen von Flags, die in der folgenden Tabelle dargestellt. Wenn ein Filter keine Flags festgelegt, wird es aufgeführt nach häufig verwendete Filter in der **Vorhandenes Element hinzufügen** \(Dialogfeld\) und die **Datei öffnen** \(Dialogfeld\), aber es wird nicht in verwendet werden die **in Dateien suchen** im Dialogfeld.  
  
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
  
|Name|Typ|Beschreibung|  
|----------|---------|------------------|  
|CommonFindFilesFilter|REG\_DWORD|Stellt den Filter eine der häufig verwendete Filter in der **in Dateien suchen** \(Dialogfeld\). Häufig verwendete Filter sind in der Liste der Filter vor Filtern, die nicht als allgemeine aufgeführt.|  
|CommonOpenFilesFilter|REG\_DWORD|Stellt den Filter eine der häufig verwendete Filter in der **geöffnete Datei** \(Dialogfeld\). Häufig verwendete Filter sind in der Liste der Filter vor Filtern, die nicht als allgemeine aufgeführt.|  
|FindInFilesFilter|REG\_DWORD|Führt den Filter nach dem häufig verwendete Filter in der **in Dateien suchen** \(Dialogfeld\).|  
|NotOpenFileFilter|REG\_DWORD|Gibt an, dass der Filter nicht, in verwendet wird der **geöffnete Datei** \(Dialogfeld\).|  
|NotAddExistingItemFilter|REG\_DWORD|Gibt an, dass der Filter nicht, in verwendet wird der **Vorhandenes Element hinzufügen** \(Dialogfeld\).|  
|SortPriority|REG\_DWORD|Legen Sie SortPriority, um die Reihenfolge zu bestimmen, in der Filter angezeigt werden. Größere SortPriority Werte, die weiter oben in der Filterliste werden angezeigt.|  
  
## Verzeichnisstruktur  
 VSPackages können Vorlagendateien und Ordner an einer beliebigen Stelle auf einem lokalen oder remote\-Datenträger, ablegen, solange die Position über die integrierte Entwicklungsumgebung \(IDE\) registriert ist. Zur Vereinfachung der Organisation empfehlen wir jedoch die folgende Verzeichnisstruktur unter Installationspfad des Produkts.  
  
 \\Templates  
  
 \\Projects \(enthält die Projektvorlagen\)  
  
 \\Applications  
  
 \\Components  
  
 \\ ...  
  
 \\ProjectItems \(enthält die Projektelemente\)  
  
 \\Class  
  
 \\Form  
  
 \\Web Seite  
  
 \\HelperFiles \(enthält die Dateien, die in mehreren Dateien Projektelemente verwendet\)  
  
 \\WizardFiles  
  
## Siehe auch  
 [Hinzufügen von Projekt\- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Assistenten](../../extensibility/internals/wizards.md)   
 [Lokalisieren von Anwendungen](../../ide/localizing-applications.md)   
 [CATIDs für Objekte, die in der Regel verwendet werden, um Projekte zu erweitern.](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)