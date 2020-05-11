---
title: Registrieren von Projekt- und Artikelvorlagen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b64504c39b1fc3c4a82530b265cfd0e96832b4f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705826"
---
# <a name="registering-project-and-item-templates"></a>Registrieren von Projekt- und Elementvorlagen
Projekttypen müssen die Verzeichnisse registrieren, in denen sich ihre Projekt- und Projektelementvorlagen befinden. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verwendet die Registrierungsinformationen, die Ihren Projekttypen zugeordnet sind, um zu bestimmen, was in den Dialogfeldern **Neues Projekt hinzufügen** und Neues Element **hinzufügen** angezeigt werden soll.

 Weitere Informationen zu Vorlagen finden Sie unter [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Registrierungseinträge für Projekte
 Die folgenden Beispiele zeigen Registrierungseinträge unter HKEY_LOCAL_MACHINE-Software-Microsoft-VisualStudio-Version\\<*Version*>. In den beigefügten Tabellen werden die in den Beispielen verwendeten Elemente erläutert.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Name|type|BESCHREIBUNG|
|----------|----------|-----------------|
|@|REG_SZ|Standardname von Projekten dieser Art.|
|DisplayName|REG_SZ|Ressourcen-ID des Namens, der aus der unter Pakete registrierten Satelliten-DLL abgerufen werden soll.|
|Paket|REG_SZ|Klassen-ID des unter Pakete registrierten Pakets.|
|ProjectTemplatesDir|REG_SZ|Standardpfad der Projektvorlagendateien. Die Projektvorlagendateien werden in der Vorlage **"Neues Projekt"** angezeigt.|

### <a name="registering-item-templates"></a>Registrieren von Elementvorlagen
 Sie müssen das Verzeichnis registrieren, in dem Sie Elementvorlagen speichern.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Name | type | BESCHREIBUNG |
|--------------------------|-----------| - |
| @ | REG_SZ | Ressourcen-ID für Elementvorlagen hinzufügen. |
| VorlagenDir | REG_SZ | Pfad der Projektelemente, die im Dialogfeld für den Assistenten **zum Hinzufügen neuer Artikel** angezeigt werden. |
| VorlagenLokalisiertSubDir | REG_SZ | Ressourcen-ID einer Zeichenfolge, die das Unterverzeichnis von TemplatesDir benennt, das lokalisierte Vorlagen enthält. Da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Zeichenfolgenressource aus Satelliten-DLLs geladen wird, kann jede Satelliten-DLL einen anderen lokalisierten Unterverzeichnisnamen enthalten. |
| SortPriority | REG_DWORD | Legen Sie SortPriority fest, um die Reihenfolge zu steuern, in der Vorlagen im Dialogfeld **Neues Element** hinzufügen angezeigt werden. Größere SortPriority-Werte werden früher in der Vorlagenliste angezeigt. |

### <a name="registering-file-filters"></a>Registrieren von Dateifiltern
 Optional können Sie Filter [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registrieren, die verwendet werden, wenn Dateinamen aufgefordert werden. Der [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Filter für das Dialogfeld **Datei öffnen** lautet z. B.:

 **Visuelle C-Dateien\*(\*.cs,\*.resx,\*.settings,\*.xsd, .wsdl); \*.cs,\*.resx,\*.settings,\*.xsd,\*.wsdl)**

 Um die Registrierung mehrerer Filter zu unterstützen, wird jeder Filter in seinem\\<eigenen Unterschlüssel unter HKEY_LOCAL_MACHINE-Software-Microsoft-VisualStudio-Version*Version*>-Projekte,\\\<*ProjectGUID*>- und\\<*-filter-Unterschlüssel*> registriert. Der Unterschlüsselname ist willkürlich; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignoriert den Namen des Unterschlüssels und verwendet nur seine Werte.

 Sie können die Kontexte steuern, in denen ein Filter verwendet wird, indem Sie Flags festlegen, die in der folgenden Tabelle angezeigt werden. Wenn für einen Filter keine Flags festgelegt sind, wird er nach den allgemeinen Filtern im Dialogfeld **VorhandeneElemente hinzufügen** und im Dialogfeld **Datei** öffnen aufgelistet, wird jedoch nicht im Dialogfeld **"In Dateien suchen"** verwendet.

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

|Name|type|BESCHREIBUNG|
|----------|----------|-----------------|
|CommonFindFilesFilter|REG_DWORD|Macht den Filter zu einem der allgemeinen Filter im Dialogfeld **"In Dateien suchen".** Allgemeine Filter werden in der Filterliste aufgeführt, bevor Filter nicht als häufig markiert werden.|
|CommonOpenFilesFilter|REG_DWORD|Macht den Filter zu einem der allgemeinen Filter im Dialogfeld **Datei** öffnen. Allgemeine Filter werden in der Filterliste aufgeführt, bevor Filter nicht als häufig markiert werden.|
|FindInFilesFilter|REG_DWORD|Listet den Filter nach den allgemeinen Filtern im Dialogfeld **Suchen in Dateien** auf.|
|NotOpenFileFilter|REG_DWORD|Gibt an, dass der Filter im Dialogfeld **Datei** öffnen nicht verwendet wird.|
|NotAddExistingItemFilter|REG_DWORD|Gibt an, dass der Filter im Dialogfeld **Vorhandene** Elemente hinzufügen nicht verwendet wird.|
|SortPriority|REG_DWORD|Legen Sie SortPriority fest, um die Reihenfolge zu steuern, in der Filter angezeigt werden. Größere SortPriority-Werte werden früher in der Filterliste angezeigt.|

## <a name="directory-structure"></a>Verzeichnisstruktur
 VSPackages kann Vorlagendateien und Ordner überall auf einem lokalen oder Remotedatenträger speichern, solange der Speicherort über die integrierte Entwicklungsumgebung (IDE) registriert wird. Aus Gründen der Organisation wird jedoch die folgende Verzeichnisstruktur unter dem Installationspfad Ihres Produkts empfohlen.

 Vorlagen

 Projekte (enthält die Projektvorlagen)

 •Anwendungen

 •Komponenten

 \ ...

 ProjectItems (enthält die Projektelemente)

 Klasse

 Formular

 •Webseite

 "HelperFiles" (enthält die Dateien, die in Projektelementen mit mehreren Dateien verwendet werden)

 •WizardFiles

## <a name="see-also"></a>Weitere Informationen

- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Assistenten](../../extensibility/internals/wizards.md)
- [Lokalisierung von Anwendungen](../../ide/globalizing-and-localizing-applications.md)
- [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
