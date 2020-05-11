---
title: Registrieren eines Projekttyps | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05ac1f393632934f193f5f4efaaf9e5459ffbb14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705871"
---
# <a name="registering-a-project-type"></a>Registrieren eines Projekttyps
Wenn Sie einen neuen Projekttyp erstellen, müssen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Sie Registrierungseinträge erstellen, mit denen Sie ihren Projekttyp erkennen und mit ihm arbeiten können. In der Regel erstellen Sie diese Registrierungseinträge mithilfe einer Registrierungsskriptdatei (.rgs).

 Im folgenden Beispiel stellen die Anweisungen aus der Registrierung ggf. Standardpfade und Daten bereit, gefolgt von einer Tabelle, die Einträge aus dem Registrierungsskript für jede Anweisung enthält. Die Tabellen enthalten die Skripteinträge und zusätzliche Informationen zu den Anweisungen.

> [!NOTE]
> Die folgenden Registrierungsinformationen sollen ein Beispiel für den Typ und die Zwecke der Einträge in den Registrierungsskripts sein, die Sie schreiben, um Ihren Projekttyp zu registrieren. Ihre tatsächlichen Einträge und deren Verwendung können je nach den spezifischen Anforderungen Ihres Projekttyps variieren. Sie sollten die verfügbaren Beispiele überprüfen, um eine zu finden, die dem Typ des Projekts, das Sie entwickeln, sehr ähnlich ist, und dann das Registrierungsskript für dieses Beispiel überprüfen.

 Die folgenden Beispiele stammen aus HKEY_CLASSES_ROOT.

## <a name="example"></a>Beispiel

```
\.figp
   @="FigPrjFile"
   "Content Type"="text/plain"
\.figp\ShellNew
   "NullFile"=""
\FigPrjFile
   @="Figure Project File"
\DefaultIcon
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"
\shell\open
   @="&Open in Visual Studio"
\shell\open\command
   @="devenv.exe \"%1\""
```

|Name|type|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|Name und Beschreibung der Projekttypdateien mit der Erweiterung .figp.|
|`Content Type`|REG_SZ|`Text/plain`|Inhaltstyp für die Projektdateien.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Standardsymbol, das für ein Projekt dieses Typs verwendet wird. Die %MODULE%-Anweisung wird in der Registrierung an den Standardspeicherort der Projekttyp-DLL abgeschlossen.|
|`@`|REG_SZ|`&Open in Visual Studio`|Standardanwendung, in der dieser Projekttyp geöffnet wird.|
|`@`|REG_SZ|`devenv.exe "%1"`|Standardbefehl, der ausgeführt wird, wenn ein Projekt dieses Typs geöffnet wird.|

 Die folgenden Beispiele stammen aus HKEY_LOCAL_MACHINE und befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-99.0Exp-Pakete].

## <a name="example"></a>Beispiel

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
   "CompanyName"="Microsoft"
   "ProductName"="Figure Project Sample"
   "ProductVersion"="9.0"
   "MinEdition"="professional"
   "ID"=dword:00000001
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL
   "DllName"="FigPrjUI.dll"
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation
   "FigProjects"=""
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"
```

|Name|type|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|`@` (Standard)|REG_SZ|`FigPrj Project VSPackage`|Lokalisierbarer Name dieses registrierten VSPackage (Projekttyp).|
|`InprocServer32`|REG_SZ|`%MODULE%`|Pfad des Projekttyps DLL. Die IDE lädt diese DLL und übergibt die VSPackage CLSID, `DllGetClassObject` um das <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> Objekt zu erstellen.|
|`CompanyName`|REG_SZ|`Microsoft`|Name des Unternehmens, das den Projekttyp entwickelt hat.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Name für den Projekttyp.|
|`ProductVersion`|REG_SZ|`9.0`|Versionsnummer der Projekttypfreigabe.|
|`MinEdition`|REG_SZ|`professional`|Ausgabe des VSPackage, das registriert wird.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Der Paketladeschlüssel für das Projekt VSPackage. Der Schlüssel wird überprüft, wenn ein Projekt geladen wird, nachdem die Umgebung gestartet wurde.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Dateiname der Satelliten-DLL, die lokalisierte Ressourcen für den Projekttyp enthält.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Pfad der Satelliten-DLL.|
|`FigProjectsEvents`|REG_SZ|Siehe Anweisung für Wert.|Bestimmt die Textzeichenfolge, die für dieses Automatisierungsereignis zurückgegeben wird.|
|`FigProjectItemsEvents`|REG_SZ|Siehe Anweisung für Wert.|Bestimmt die Textzeichenfolge, die für dieses Automatisierungsereignis zurückgegeben wird.|

 Alle folgenden Beispiele befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-9.0Exp-Projekte].

## <a name="example"></a>Beispiel

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
   @="#4"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000000
   "FindInFilesFilter"=dword:00000000
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2
      (Folder 2 contains settings for Find in Files filters.)
   @="#5"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000001
   "FindInFilesFilter"=dword:00000001
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Name|type|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|Standardname der Projekte dieses Typs.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Ressourcen-ID des Namens, der aus der unter Pakete registrierten Satelliten-DLL abgerufen werden soll.|
|`Package`|REG_SZ|`%CLSID_Package%`|Klassen-ID des VSPackage, das unter Pakete registriert ist.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Standardpfad der Projektvorlagendateien. Dies sind die Dateien, die in der Vorlage "Neues Projekt" angezeigt werden.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Standardpfad der Projektelementvorlagendateien. Dies sind die Dateien, die in der Vorlage "Neues Element hinzufügen" angezeigt werden.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Aktiviert die IDE, das Dialogfeld **Öffnen** zu implementieren.|
|`PossibleProjectExtensions`|REG_SZ|`figp`|Wird von der IDE verwendet, um zu bestimmen, ob das zu öffnende Projekt von diesem Projekttyp (Projektfactory) verarbeitet wird. Das Format für mehr als einen Eintrag ist eine durch Semikolons getrennte Liste. Beispiel: "vdproj;vdp".|
|`DefaultProjectExtension`|REG_SZ|`.figp`|Wird von der IDE als Standarddateinamenerweiterung für den Vorgang Speichern unter verwendet.|
|`Filter Settings`|REG_DWORD|Verschiedene, siehe Anweisungen und Kommentare nach der Tabelle.|Diese Einstellungen werden verwendet, um die verschiedenen Filter für die Anzeige von Dateien in UI-Dialogfeldern festzulegen.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Ressourcen-ID für Elementvorlagen hinzufügen.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Pfad der Projektelemente, die im Dialogfeld für die Vorlage **"Neues Element hinzufügen"** angezeigt werden.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Bestimmt die Sortierreihenfolge im Strukturknoten von Dateien, die im Dialogfeld **Neues Element** hinzufügen angezeigt werden.|

 Die folgende Tabelle zeigt die Filteroptionen, die im vorherigen Codesegment verfügbar sind.

|Filteroption|BESCHREIBUNG|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Gibt an, dass der Filter einer der allgemeinen Filter im Dialogfeld **"In Dateien suchen"** ist. Die allgemeinen Filter werden in der Filterliste aufgeführt, bevor die Filter nicht als häufig markiert sind.|
|`CommonOpenFilesFilter`|Gibt an, dass der Filter einer der allgemeinen Filter im Dialogfeld **Datei** öffnen ist. Die allgemeinen Filter werden in der Filterliste aufgeführt, bevor die Filter nicht als häufig markiert sind.|
|`FindInFilesFilter`|Gibt an, dass der Filter einer der Filter im Dialogfeld **"In Dateien suchen"** sein wird und nach den allgemeinen Filtern aufgelistet wird.|
|`NotOpenFileFilter`|Gibt an, dass der Filter nicht im Dialogfeld **Datei** öffnen verwendet wird.|
|`NotAddExistingItemFilter`|Gibt an, dass der Filter nicht im Dialogfeld **VorhandeneElemente** hinzufügen verwendet wird.|

 Wenn für einen Filter nicht eines oder mehrere dieser Flags festgelegt sind, wird der Filter standardmäßig im Dialogfeld Vorhandene Elemente **hinzufügen** und im Dialogfeld **Datei** öffnen verwendet, nachdem die allgemeinen Filter aufgelistet wurden. Der Filter wird im Dialogfeld **"In Dateien suchen"** nicht verwendet.

 Alle folgenden Beispiele befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-9.0Exp-Projekte].

## <a name="example"></a>Beispiel

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Name|type|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Ressourcen-ID für neue Projektvorlagen.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Standardpfad für Projekte des registrierten Projekttyps.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Legt die Sortierreihenfolge von Projekten fest, die im Dialogfeld des Assistenten für neue Projekte angezeigt werden.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 gibt an, dass Projekte dieses Typs nur im Dialogfeld Neues Projekt angezeigt werden.|

 Alle folgenden Beispiele befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-9.0Exp-Projekte].

## <a name="example"></a>Beispiel

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Name|type|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|Keine|Standardwert, der angibt, dass die folgenden Einträge für die Projekteinträge "Verschiedene Dateien" gelten.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Ressourcen-ID-Wert für die Vorlagendateien Neue Elemente hinzufügen.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Standardpfad der Elemente, die im Dialogfeld **Neues Element** hinzufügen angezeigt werden.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Legt die Sortierreihenfolge für die Anzeige im Strukturknoten des Dialogfelds **Neues Element hinzufügen** fest.|

 Das folgende Beispiel befindet sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-9.0Exp-Menüs].

## <a name="example"></a>Beispiel

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 Der Menüeintrag verweist die IDE auf die Ressource, die zum Abrufen der Menüinformationen verwendet wird. Wenn diese Daten in der Menüdatenbank zusammengeführt wurden, wird derselbe Schlüssel im Abschnitt MenusMerged der Registrierung hinzugefügt. Das VSPackage sollte nichts unter dem Abschnitt MenusMerged direkt ändern. Im Feld Daten in der folgenden Tabelle befinden sich drei durch Kommas getrennte Felder. Das erste Feld identifiziert einen vollständigen Pfad einer Menüressourcendatei:

- Wenn das erste Feld weggelassen wird, wird die Menüressource aus der Satelliten-DLL geladen, die von der VSPackage-GUID identifiziert wird.

  Das zweite Feld identifiziert eine Menüressourcen-ID vom Typ CTMENU:

- Wenn die Ressourcen-ID angegeben ist und der Dateipfad vom ersten Parameter bereitgestellt wird, wird eine Menüressource aus dem vollständigen Dateipfad geladen.

- Wenn die Ressourcen-ID angegeben wird, der Dateipfad jedoch nicht, wird die Menüressource aus der Satelliten-DLL geladen.

- Wenn der vollständige Dateipfad angegeben und die Ressourcen-ID weggelassen wird, wird erwartet, dass es sich bei der zu ladenden Datei um eine CTO-Datei handelt.

  Das letzte Feld gibt die Versionsnummer für die CTMENU-Ressource an. Sie können das Menü erneut zusammenführen, indem Sie die Versionsnummer ändern.

|Name|type|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|%CLSID_Package %|REG_SZ|`,1000,1`|Die Ressource, die die Menüinformationen abrufen soll.|

 Alle folgenden Beispiele befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-9.0Exp-NewProjectTemplates].

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Name|type|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Ressourcen-ID-Wert für die Vorlagen für das neue Projekt des Figures-Projekts.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Standardpfad des Verzeichnisses "Neue Projekte". Elemente in diesem Verzeichnis werden im Dialogfeld des **Assistenten für neues Projekt** angezeigt.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Legt die Reihenfolge fest, in der Projekte im Strukturknoten des Dialogfelds **Neues Projekt** angezeigt werden.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 gibt an, dass Projekte dieses Typs nur im Dialogfeld **Neues Projekt** angezeigt werden.|

 Das folgende Beispiel befindet sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-9.0Exp-InstalledProducts].

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|Name|type|Daten|BESCHREIBUNG|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|Klassen-ID des registrierten VSPackage.|
|`UseInterface`|REG_DWORD|`1`|1 gibt an, dass die Benutzeroberfläche für die Interaktion mit diesem Projekt verwendet wird. 0 gibt an, dass keine UI-Schnittstelle vorhanden ist.|

 Die.vsz-Dateien, die neue Projekttypen steuern, enthalten häufig einen RELATIVE_PATH Eintrag. Dieser Pfad ist relativ zum Pfad, der unter dem Eintrag "ProductDir" des Projekttyps im folgenden Setupschlüssel angegeben ist:

 HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-7.0Exp-Setup

 Die Enterprise Frameworks-Projektvorlagen fügen beispielsweise die folgenden Registrierungseinträge hinzu:

 HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-7.0Exp-Setup-EF-ProductDir = C:-Programmdateien, Microsoft Visual Studio, EnterpriseFrameworks

 Das bedeutet, wenn Sie einen PROJECT_TYPE=EF-Eintrag in die .vsz-Datei aufnehmen, findet die Umgebung Ihre .vsz-Dateien im zuvor angegebenen ProductDir-Verzeichnis.

## <a name="see-also"></a>Weitere Informationen
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)
- [Erstellen von Projektinstanzen mithilfe von Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
