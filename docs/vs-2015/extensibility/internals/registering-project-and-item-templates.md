---
title: Registrieren von Projekt-und Element Vorlagen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a06e7a292d960e675ad4b0de97499557542fef1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185835"
---
# <a name="registering-project-and-item-templates"></a>Registrieren von Projekt- und Elementvorlagen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projekttypen müssen die Verzeichnisse registrieren, in denen sich Ihre Projekt-und Projekt Element Vorlagen befinden. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] verwendet die Registrierungsinformationen, die den Projekttypen zugeordnet sind, um zu bestimmen, was in den Dialogfeldern **Neues Projekt hinzufügen** und **Neues Element hinzufügen** angezeigt werden soll.  
  
 Weitere Informationen zu Vorlagen finden Sie unter [Hinzufügen von Projekt-und Projekt Element Vorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="registry-entries-for-projects"></a>Registrierungseinträge für Projekte  
 Die folgenden Beispiele zeigen Registrierungseinträge unter HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ < *Version*>. In den zugehörigen Tabellen werden die in den Beispielen verwendeten Elemente erläutert.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|Name|type|BESCHREIBUNG|  
|----------|----------|-----------------|  
|@|REG_SZ|Standardname der Projekte dieser Art.|  
|DisplayName|REG_SZ|Die Ressourcen-ID des Namens, der von der Satelliten-DLL abgerufen werden soll, die unter Packages registriert ist.|  
|Paket|REG_SZ|Klassen-ID des Pakets, das unter "Packages" registriert ist.|  
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
  
|Name|type|BESCHREIBUNG|  
|----------|----------|-----------------|  
|@|REG_SZ|Ressourcen-ID für Element Vorlagen hinzufügen.|  
|Templatesdir|REG_SZ|Der Pfad der Projekt Elemente, die im Dialogfeld für den Assistenten zum **Hinzufügen eines neuen Elements** angezeigt werden.|  
|Templateslocalizedsubdir|REG_SZ|Die Ressourcen-ID einer Zeichenfolge, die das Unterverzeichnis von templatesdir benennt, das lokalisierte Vorlagen enthält. Da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] die Zeichen folgen Ressource aus Satelliten-DLLs lädt, kann jede Satelliten-DLL einen anderen lokalisierten Unterverzeichnis Namen enthalten.|  
|SortPriority|REG_DWORD|Legen Sie SortPriority fest, um die Reihenfolge zu steuern, in der Vorlagen im Dialogfeld **Neues Element hinzufügen** angezeigt werden. Größere SortPriority-Werte werden zuvor in der Vorlagenliste angezeigt.|  
  
### <a name="registering-file-filters"></a>Registrieren von Dateifiltern  
 Optional können Sie Filter registrieren, die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] von verwendet werden, wenn Sie zur Eingabe von Dateinamen aufgefordert werden. Der [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Filter für das Dialogfeld " **Datei öffnen** " lautet beispielsweise wie folgt:  
  
 **Visual c#-Dateien ( \* . cs, \* . resx, \* . Settings, \* . xsd, \* . WSDL); \* . CS, \* . resx, \* . Settings, \* . xsd, \* . WSDL)**  
  
 Um die Registrierung mehrerer Filter zu unterstützen, wird jeder Filter in seinem eigenen Unterschlüssel unter HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ < *Version*> \projects \\ { \<*ProjectGUID*> } \filters unter \\ < *Schlüssel*> registriert. Der Name des unter Schlüssels ist willkürlich. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ignoriert den Namen des unter Schlüssels und verwendet lediglich seine Werte.  
  
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
  
|Name|type|BESCHREIBUNG|  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Projekt-und Projekt Element Vorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [The](../../extensibility/internals/wizards.md)   
 [Lokalisieren von Anwendungen](../../ide/localizing-applications.md)   
 [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
