---
title: Registrieren einen Projekttyp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8e6c91f2c92dd121cd135aef4291c7f7983206ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134632"
---
# <a name="registering-a-project-type"></a>Registrieren einen Projekttyp
Wenn Sie einen neuen Projekttyp erstellen, müssen Sie die Registrierungseinträge, die es ermöglichen erstellen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erkannt werden und Arbeiten mit Ihrem Project-Typs. Diese Registrierungseinträge wird normalerweise mithilfe einer Registrierung-Skriptdatei (.rgs) erstellen.  
  
 Im folgenden Beispiel wird die Anweisungen aus der Registrierung geben Sie Standardpfade und Daten, sofern zutreffend, gefolgt von einer Tabelle, die Einträge aus dem Registrierungsskript "for each-Anweisung enthält. Die Tabellen enthalten die skripteinträgen und zusätzliche Informationen zu den Anweisungen.  
  
> [!NOTE]
>  Die folgenden Registrierungsinformationen dient als ein Beispiel für den Typ und Zweck der Einträge in der Registrierungsskripts an, die Sie zum Registrieren Ihres Projekttyps geschrieben werden. Die tatsächliche Einträge und deren Verwendung variieren basierend auf den jeweiligen Anforderungen Ihres Projekts-Typs. Sie sollten überprüfen Sie die Beispielen zu suchen, die den Typ des Projekts sehr ähnlich, die Sie entwickeln und überprüfen Sie die Registrierungsdatei für dieses Beispiel.  
  
 In den folgenden Beispielen werden von HKEY_CLASSES_ROOT.  
  
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
  
|name|Typ|Daten|Beschreibung|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|Name und Beschreibung des Projekts geben Sie Dateien, die die Erweiterung .figp aufweisen.|  
|`Content Type`|REG_SZ|`Text/plain`|Der Inhaltstyp für die Projektdateien.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Das Standardsymbol für Projekt dieses Typs verwendet. Die %-Modul %-Anweisung ist in der Registrierung auf der standardmäßige Speicherort der DLL-Projekttyp abgeschlossen.|  
|`@`|REG_SZ|`&Open in Visual Studio`|Standard-Anwendung, in dem dieser Projekttyp geöffnet wird.|  
|`@`|REG_SZ|`devenv.exe "%1"`|Standardbefehl, der ausgeführt wird, wenn ein Projekt dieses Typs geöffnet ist.|  
  
 In den folgenden Beispielen werden von HKEY_LOCAL_MACHINE und befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].  
  
## <a name="example"></a>Beispiel  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
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
  
|name|Typ|Daten|Beschreibung|  
|----------|----------|----------|-----------------|  
|`@` (Standard)|REG_SZ|`FigPrj Project VSPackage`|Lokalisierbare Name dieses registriert VSPackage (Projekttyp).|  
|`InprocServer32`|REG_SZ|`%MODULE%`|Pfad der DLL-Projekttyp. Die IDE diese DLL lädt und übergibt die CLSID VSPackage zu `DllGetClassObject` abzurufenden <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> zum Erstellen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> Objekt.|  
|`CompanyName`|REG_SZ|`Microsoft`|Der Name des Unternehmens, das den Projekttyp entwickelt.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|Der Name für den Projekttyp.|  
|`ProductVersion`|REG_SZ|`9.0`|Lassen Sie die Versionsnummer des Project-Typs.|  
|`MinEdition`|REG_SZ|`professional`|Die Edition des VSPackage registriert wird.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Schlüssel für das VSPackage-Projekt Laden des Pakets. Der Schlüssel wird überprüft, wenn ein Projekt geladen wird, nach dem Start der umgebungs.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Der Dateiname der Satelliten-DLL, die lokalisierte Ressourcen für den Projekttyp enthält.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Pfad der Satelliten-DLL.|  
|`FigProjectsEvents`|REG_SZ|Finden Sie die Anweisung nach Wert.|Bestimmt die Textzeichenfolge, die für dieses Automatisierungsereignis zurückgegeben.|  
|`FigProjectItemsEvents`|REG_SZ|Finden Sie die Anweisung nach Wert.|Bestimmt die Textzeichenfolge, die für dieses Automatisierungsereignis zurückgegeben.|  
  
 Die folgenden Beispiele befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Beispiel  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
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
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|name|Typ|Daten|Beschreibung|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|Der Standardname der Projekte dieses Typs.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Ressourcen-ID mit dem Namen aus der Satelliten-DLL abgerufen werden sollen, die unter Pakete registriert werden.|  
|`Package`|REG_SZ|`%CLSID_Package%`|Klassen-ID des VSPackage registriert unter "Pakete".|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Der Standardpfad der Projektvorlage für Dateien. Hierbei handelt es sich um die Dateien, die durch die neue Projektvorlage angezeigt.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Der Standardpfad der Projektelementvorlage Dateien. Hierbei handelt es sich um die Dateien, die von der neues Element hinzufügen-Vorlage angezeigt.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Aktiviert die IDE implementiert die **öffnen** (Dialogfeld).|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|Von der IDE verwendet, um zu bestimmen, ob das Projekt geöffnet, die von dieser Projekttyp (Projekt Factory) behandelt wird. Das Format für mehr als ein Eintrag ist eine durch Semikolons getrennte Liste. Z. B. "Vdproj; Vdp".|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|Von der IDE verwendet als die standardmäßige Dateinamenerweiterung für den Vorgang zum Speichern.|  
|`Filter Settings`|REG_DWORD|Verschiedene, finden Sie Anweisungen sowie Kommentare, die in der folgenden Tabelle.|Diese Einstellungen werden verwendet, um die verschiedenen Filter für die Anzeige von Dateien in den Dialogfeldern für die Benutzeroberfläche festgelegt.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Ressourcen-ID für Elementvorlagen hinzufügen.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Pfad der Projektelemente angezeigt, klicken Sie im Dialogfeld für die **neues Element hinzufügen** Vorlage.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Bestimmt die Sortierreihenfolge in der Strukturknoten der Dateien angezeigt, der **neues Element hinzufügen** (Dialogfeld).|  
  
 Die folgende Tabelle zeigt die Filter-Optionen, die in der vorherigen Codesegment verfügbar.  
  
|Filteroption|Beschreibung|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|Gibt an, dass der Filter eine häufig verwendete Filter in ist der **in Dateien suchen** (Dialogfeld). Häufig verwendete Filter werden in der Filterliste vor den Filtern, die nicht markiert als allgemeiner aufgeführt.|  
|`CommonOpenFilesFilter`|Gibt an, dass der Filter eine häufig verwendete Filter in ist der **Dateiöffnungsmodus** (Dialogfeld). Häufig verwendete Filter werden in der Filterliste vor den Filtern, die nicht markiert als allgemeiner aufgeführt.|  
|`FindInFilesFilter`|Gibt an, dass der Filter einen Filter in werden die **in Dateien suchen** Dialogfeld Feld und wird nach der allgemeinen Filter aufgeführt.|  
|`NotOpenFileFilter`|Gibt an, dass in der Filter nicht verwendet werden, wird die **Dateiöffnungsmodus** (Dialogfeld).|  
|`NotAddExistingItemFilter`|Gibt an, dass der Filter hinzufügen nicht verwendet wird **vorhandenes Element** (Dialogfeld).|  
  
 Standardmäßig, wenn Sie ein Filter verfügt nicht über eine oder mehrere der folgenden flags festgelegt ist, der Filter wird verwendet der **vorhandenes Element hinzufügen** Dialogfeld und der **geöffnete Datei** (Dialogfeld), nachdem die allgemeinen Filter aufgeführt sind. Der Filter wird nicht verwendet, der **in Dateien suchen** (Dialogfeld).  
  
 Die folgenden Beispiele befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Beispiel  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|name|Typ|Daten|Beschreibung|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Ressourcen-ID für die neue Projektvorlagen.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Der Standardpfad für die registrierten Projekttyp-Projekte.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Legt die Sortierreihenfolge von Projekten, die im Dialogfeld-Assistent für neue Projekte angezeigt.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 gibt an, dass Projekte dieses Typs nur im Dialogfeld Neues Projekt angezeigt werden.|  
  
 Die folgenden Beispiele befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Beispiel  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|name|Typ|Daten|Beschreibung|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|Keiner|Der Standardwert, der angibt, dass die folgenden Einträge für die sonstigen Dateien Projekte Einträge sind.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Ressourcen-ID-Wert für die Vorlagendateien neue Elemente hinzufügen.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Standardpfad der Elemente, die in angezeigt werden, wird die **neues Element hinzufügen** (Dialogfeld).|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Sortierreihenfolge für die Anzeige in der Strukturknoten der richtet die **neues Element hinzufügen** (Dialogfeld).|  
  
 Im folgende Beispiel befindet sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].  
  
## <a name="example"></a>Beispiel  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 Der Menüeintrag zeigt die IDE auf die Ressource verwendet, um die Informationen abzurufen. Wenn diese Daten in die Datenbank im Menü zusammengeführt wurde, wird der gleiche Schlüssel im Abschnitt MenusMerged der Registrierung hinzugefügt werden. Das VSPackage dürfen nicht alle Elemente unter dem Abschnitt MenusMerged direkt ändern. Das Feld "Daten" in der folgenden Tabelle sind drei Komma-getrennt-Felder vorhanden. Das erste Feld identifiziert, einen vollständigen Pfad einer Ressourcendatei Menü:  
  
-   Wenn das erste Feld ausgelassen wird, wird die Menüressource aus der Satelliten-DLL, die durch die VSPackage-GUID identifiziert wird geladen.  
  
 Das zweite Feld identifiziert eine Menü-Ressourcen-ID des Typs CTMENU:  
  
-   Wenn die Ressourcen-ID angegeben ist, und der Dateipfad durch den ersten Parameter angegeben wird, wird eine Menüressource aus den vollständigen Dateipfad geladen.  
  
-   Wenn die Ressourcen-ID bereitgestellt wird, aber der Dateipfad ist, wird die Menüressource aus der Satelliten-DLL geladen.  
  
-   Wenn der vollständige Pfad angegeben wird, und die Ressourcen-ID angegeben, muss die Datei geladen werden soll einer CTO-Datei sein.  
  
 Das letzte Feld gibt die Versionsnummer für die Ressource CTMENU. Sie können das Menü erneut zusammenführen, durch die Änderung der Versionsnummer.  
  
|name|Typ|Daten|Beschreibung|  
|----------|----------|----------|-----------------|  
|"% CLSID_Package"|REG_SZ|`,1000,1`|Die Ressource, die Informationen abzurufen.|  
  
 Die folgenden Beispiele befinden sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|name|Typ|Daten|Beschreibung|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Ressourcen-ID-Wert für die Abbildungen Projekt neue Projektvorlagen.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Der Standardpfad des Verzeichnisses neue Projekte. Elemente in diesem Verzeichnis angezeigt werden die **Assistent für neue Projekte** (Dialogfeld).|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Die Reihenfolge, in der Projekte in der der Strukturknoten angezeigt, wird der **neues Projekt** (Dialogfeld).|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 gibt an, dass Projekte dieses Typs nur in angezeigt werden die **neues Projekt** (Dialogfeld).|  
  
 Im folgende Beispiel befindet sich in der Registrierung unter dem Schlüssel [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|name|Typ|Daten|Beschreibung|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|Klassen Sie-ID des registrierten VSPackage.|  
|`UseInterface`|REG_DWORD|`1`|1 gibt an, dass die Benutzeroberfläche für die Interaktion mit diesem Projekt verwendet werden. 0 gibt an, dass keine Benutzeroberfläche vorhanden ist.|  
  
 Assistentenversion-Dateien, die häufig neue Projekttypen steuern enthalten einen RELATIVE_PATH-Eintrag. Dieser Pfad ist relativ zum Pfad unter \ProductDir Eintrag des Project-Typs in den folgenden Setupschlüssel angegeben:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Die Projektvorlagen für Enterprise-Frameworks wird z. B. die folgenden Registrierungseinträge hinzufügen:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 Bedeutet Folgendes: Wenn Sie eine PROJECT_TYPE einschließen = EF Eintrag in der VSZ-Datei, die Umgebung findet der VSZ-im Verzeichnis \ProductDir zuvor angegeben Dateien.  
  
## <a name="see-also"></a>Siehe auch  
 [Prüfliste: Erstellen neuen Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Elemente eines Projekt-Modells](../../extensibility/internals/elements-of-a-project-model.md)   
 [Erstellen von Projektinstanzen mithilfe von Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)