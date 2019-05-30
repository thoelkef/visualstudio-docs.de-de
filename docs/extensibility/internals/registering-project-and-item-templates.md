---
title: Registrieren von Projekt- und Elementvorlagen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84beaf97bda8d94872be22c6f5d247a746d1ecd3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319511"
---
# <a name="registering-project-and-item-templates"></a>Registrieren von Projekt- und Elementvorlagen
Projekttypen müssen die Verzeichnisse registrieren, wo sich ihre Projekt- und Projekt Vorlagen befinden. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Bestimmt die Registrierungsinformationen Ihrer Projekttypen zugeordnet, was für die anzuzeigenden in die **neues Projekt hinzufügen** und **neues Element hinzufügen** Dialogfelder.

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

|Name|Typ|Beschreibung|
|----------|----------|-----------------|
|@|REG_SZ|Der Standardname der Projekte dieser Art.|
|DisplayName|REG_SZ|Ressourcen-ID mit dem Namen aus der Satelliten-DLL abgerufen werden, die unter Pakete registriert werden.|
|Package|REG_SZ|Klassen-ID des Pakets unter Pakete registriert.|
|ProjectTemplatesDir|REG_SZ|Der Standardpfad der Projektvorlage Dateien. Die Projektvorlage-Dateien werden angezeigt, durch die **neues Projekt** Vorlage.|

### <a name="registering-item-templates"></a>Registrieren von Elementvorlagen
 Sie müssen das Verzeichnis registrieren, wo Sie Vorlagen speichern.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Name | Typ | Beschreibung |
|--------------------------|-----------| - |
| @ | REG_SZ | Ressourcen-ID für Element hinzufügen-Vorlagen. |
| TemplatesDir | REG_SZ | Pfad der Projektelemente angezeigt, in das Dialogfeld für die **neues Element hinzufügen** Assistenten. |
| TemplatesLocalizedSubDir | REG_SZ | Ressourcen-ID der eine Zeichenfolge, die mit dem Namen das Unterverzeichnis des TemplatesDir enthält lokalisierte Vorlagen. Da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lädt die Zeichenfolgenressource aus Satelliten-DLLs bei Bedarf, jede Satelliten-DLL kann einem anderen lokalisierten Unterverzeichnisnamen enthalten. |
| SortPriority | REG_DWORD | Legen Sie SortPriority zur Steuerung der Reihenfolge, in der Vorlagen, in angezeigt werden, der **neues Element hinzufügen** Dialogfeld. Größere SortPriority-Werte, die weiter oben in der Vorlagenliste angezeigt werden. |

### <a name="registering-file-filters"></a>Dateifilter registrieren
 Sie können optional Filter registrieren, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet werden, wenn es für Dateinamen aufgefordert werden. Z. B. die [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtern Sie nach der **geöffnete Datei** Dialogfeld können Sie:

 **Visual C#-Dateien (\*cs,\*RESX,\*Settings,\*.xsd,\*.wsdl);\*. Cs,\*RESX,\*Settings,\*.xsd,\*.wsdl)**

 Um die Registrierung von mehreren Filtern zu unterstützen, ist jeder Filter in eine eigene Unterschlüssel HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio registriert\\<*Version*> \Projects\\{} \< *ProjectGUID*>} \Filters\\<*Unterschlüssel*>. Der Name des Unterschlüssels ist frei wählbar. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignoriert der Unterschlüssel des Namen und nur die Werte verwendet.

 Sie können die Kontexte steuern, in denen ein Filter verwendet wird, durch Festlegen von Flags, die in der folgenden Tabelle gezeigt. Wenn ein Filter keine Flags festlegen, wird er nach dem häufig verwendete Filter in der **vorhandenes Element hinzufügen** im Dialogfeld und der **geöffnete Datei** (Dialogfeld), aber es wird nicht in verwendet werden die **in Dateien suchen**  Dialogfeld.

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
|----------|----------|-----------------|
|CommonFindFilesFilter|REG_DWORD|Stellt den Filter eine häufig verwendete Filter in der **in Dateien suchen** Dialogfeld. Allgemeine Filter werden in der Filterliste vor Filtern, die nicht so häufig gekennzeichnet aufgeführt.|
|CommonOpenFilesFilter|REG_DWORD|Stellt den Filter eine häufig verwendete Filter in der **geöffnete Datei** Dialogfeld. Allgemeine Filter werden in der Filterliste vor Filtern, die nicht so häufig gekennzeichnet aufgeführt.|
|FindInFilesFilter|REG_DWORD|Führt den Filter nach dem häufig verwendete Filter in der **in Dateien suchen** Dialogfeld.|
|NotOpenFileFilter|REG_DWORD|Gibt an, dass der Filter nicht, in verwendet wird der **geöffnete Datei** Dialogfeld.|
|NotAddExistingItemFilter|REG_DWORD|Gibt an, dass der Filter nicht, in verwendet wird der **vorhandenes Element hinzufügen** Dialogfeld.|
|SortPriority|REG_DWORD|Legen Sie SortPriority zur Steuerung der Reihenfolge, in der Filter angezeigt werden. Größere SortPriority-Werte, die weiter oben in der Filterliste angezeigt werden.|

## <a name="directory-structure"></a>Verzeichnisstruktur
 VSPackages können Vorlagendateien und Ordner an einer beliebigen Stelle auf einem Datenträger lokaler oder remote einfügen als die Position über die integrierte Entwicklungsumgebung (IDE) registriert ist. Für die Organisation zu vereinfachen empfehlen wir jedoch die folgende Verzeichnisstruktur unter Installationspfad Ihres Produkts.

 \Templates

 \Projects (enthält die Projektvorlagen)

 \Applications

 \Components

 \ ...

 \ProjectItems (die Projektelemente enthält)

 \Class

 \Form

 \Web Page

 \HelperFiles (enthält die in der Projektelemente mit mehreren Dateien verwendeten Dateien)

 \WizardFiles

## <a name="see-also"></a>Siehe auch

- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Assistenten](../../extensibility/internals/wizards.md)
- [Lokalisieren von Anwendungen](../../ide/globalizing-and-localizing-applications.md)
- [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)