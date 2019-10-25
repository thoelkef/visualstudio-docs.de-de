---
title: Registrieren von Projekt-und Element Vorlagen | Microsoft-Dokumentation
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
ms.openlocfilehash: 2e35a476ab8fe8d8de3ce11dd117de4c84a3befa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724626"
---
# <a name="registering-project-and-item-templates"></a>Registrieren von Projekt- und Elementvorlagen
Projekttypen müssen die Verzeichnisse registrieren, in denen sich Ihre Projekt-und Projekt Element Vorlagen befinden. in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] werden die mit den Projekttypen verknüpften Registrierungsinformationen verwendet, um zu bestimmen, was in den Dialogfeldern **Neues Projekt hinzufügen** und **Neues Element hinzufügen** angezeigt werden soll.

 Weitere Informationen zu Vorlagen finden Sie unter [Hinzufügen von Projekt-und Projekt Element Vorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Registrierungseinträge für Projekte
 In den folgenden Beispielen werden die Registrierungseinträge unter HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ <*Version*> gezeigt. In den zugehörigen Tabellen werden die in den Beispielen verwendeten Elemente erläutert.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|-Name|Geben Sie Folgendes ein:|Beschreibung|
|----------|----------|-----------------|
|@|REG_SZ|Standardname der Projekte dieser Art.|
|DisplayName|REG_SZ|Die Ressourcen-ID des Namens, der von der Satelliten-DLL abgerufen werden soll, die unter Packages registriert ist.|
|Package|REG_SZ|Klassen-ID des Pakets, das unter "Packages" registriert ist.|
|Projecttemplatesdir|REG_SZ|Standardpfad der Projektvorlagen Dateien. Die Projektvorlagen Dateien werden von der **neuen Projekt** Vorlage angezeigt.|

### <a name="registering-item-templates"></a>Registrieren von Element Vorlagen
 Sie müssen das Verzeichnis registrieren, in dem Sie Element Vorlagen speichern.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| -Name | Geben Sie Folgendes ein: | Beschreibung |
|--------------------------|-----------| - |
| @ | REG_SZ | Ressourcen-ID für Element Vorlagen hinzufügen. |
| Templatesdir | REG_SZ | Der Pfad der Projekt Elemente, die im Dialogfeld für den Assistenten zum **Hinzufügen eines neuen Elements** angezeigt werden. |
| Templateslocalizedsubdir | REG_SZ | Die Ressourcen-ID einer Zeichenfolge, die das Unterverzeichnis von templatesdir benennt, das lokalisierte Vorlagen enthält. Da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Zeichen folgen Ressource aus Satelliten-DLLs lädt, kann jede Satelliten-DLL einen anderen lokalisierten Unterverzeichnis Namen enthalten. |
| SortPriority | REG_DWORD | Legen Sie SortPriority fest, um die Reihenfolge zu steuern, in der Vorlagen im Dialogfeld **Neues Element hinzufügen** angezeigt werden. Größere SortPriority-Werte werden zuvor in der Vorlagenliste angezeigt. |

### <a name="registering-file-filters"></a>Registrieren von Dateifiltern
 Optional können Sie Filter registrieren, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet, wenn Sie zur Eingabe von Dateinamen aufgefordert werden. Der [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Filter für das Dialogfeld **Datei öffnen** lautet beispielsweise wie folgt:

 **Visuelle C# Dateien (\*. cs, \*. resx, \*. Settings, \*. xsd, \*. WSDL); \*. cs, \*. resx, \*. Settings, 0. xsd, 1. WSDL)**

 Um die Registrierung mehrerer Filter zu unterstützen, wird jeder Filter unter HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ <*Version*> \projects \\ {\<*ProjectGuid*>} \filters in seinem eigenen Unterschlüssel registriert. \\ <*Unterschlüssel*>. Der Name des unter Schlüssels ist willkürlich.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignoriert den Namen des unter Schlüssels und verwendet lediglich seine Werte.

 Sie können die Kontexte, in denen ein Filter verwendet wird, Steuern, indem Sie Flags festlegen, die in der folgenden Tabelle aufgeführt sind. Wenn für einen Filter keine Flags festgelegt sind, wird er nach den allgemeinen Filtern im Dialogfeld **Vorhandenes Element hinzufügen** und im Dialogfeld **Datei öffnen** aufgelistet. es wird jedoch nicht im Dialogfeld **in Dateien suchen** verwendet.

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

|-Name|Geben Sie Folgendes ein:|Beschreibung|
|----------|----------|-----------------|
|Commonfindfilesfilter|REG_DWORD|Macht den Filter zu einem der allgemeinen Filter im Dialogfeld **in Dateien suchen** . Allgemeine Filter sind in der Filterliste aufgeführt, bevor Filter als "Allgemein" gekennzeichnet sind.|
|Commonopenfilesfilter|REG_DWORD|Macht den Filter zu einem der allgemeinen Filter im Dialogfeld **Datei öffnen** . Allgemeine Filter sind in der Filterliste aufgeführt, bevor Filter als "Allgemein" gekennzeichnet sind.|
|Findinfilesfilter|REG_DWORD|Listet den Filter nach den allgemeinen Filtern im Dialogfeld **in Dateien suchen auf** .|
|Notopenfilefilter|REG_DWORD|Gibt an, dass der Filter im Dialogfeld " **Datei öffnen** " nicht verwendet wird.|
|Notadde xistingitemfilter|REG_DWORD|Gibt an, dass der Filter nicht im Dialogfeld **Vorhandenes Element hinzufügen** verwendet wird.|
|SortPriority|REG_DWORD|Legen Sie SortPriority fest, um die Reihenfolge zu steuern, in der Filter angezeigt werden. Größere SortPriority-Werte werden zuvor in der Filterliste angezeigt.|

## <a name="directory-structure"></a>Verzeichnisstruktur
 VSPackages können Vorlagen Dateien und-Ordner auf einem lokalen oder Remote Datenträger platzieren, sofern der Speicherort über die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) registriert ist. Zur Erleichterung der Organisation wird jedoch die folgende Verzeichnisstruktur unter dem Installationspfad Ihres Produkts empfohlen.

 \Vorlagen

 \Projects (enthält die Projektvorlagen)

 \Anwendungen

 \Components

 \ ...

 \Projectitems (enthält die Projekt Elemente)

 \Class

 \Form

 \Webseite

 \Helperfiles (enthält die Dateien, die in Projekt Elementen mit mehreren Dateien verwendet werden)

 \Wizardfiles

## <a name="see-also"></a>Siehe auch

- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Assistenten](../../extensibility/internals/wizards.md)
- [Lokalisieren von Anwendungen](../../ide/globalizing-and-localizing-applications.md)
- [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)