---
title: "Registrieren einen Projekttyp | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekte [Visual Studio SDK] neue Projekt Registrierungseinträge"
  - "Neue Projekttypen-Registrierung"
  - "Neue Projekttypen-Registrierung"
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrieren einen Projekttyp
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn Sie ein neuer Projekttyp erstellen, müssen Sie die Registrierungseinträge erstellen, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aktivieren, um mit dem Projekttyp zu erkennen und zu bearbeiten.  Normalerweise erstellen Sie diese Registrierungseinträge, indem Sie eine Registrierung \(.rgs\) \- skripts verwenden.  
  
 Im folgenden Beispiel stellen die Anweisungen aus der Registrierung Standardpfade und Daten soweit zutreffend, gefolgt von einer Tabelle, die Einträge in der Registrierung von Skripts für jede Anweisung enthält.  Die Tabellen stellen die Einträge für Skripts und zusätzliche Informationen über die Anweisungen.  
  
> [!NOTE]
>  Die folgenden Registrierungsinformationen sollen, ein Beispiel für Typen und Zwecken der Einträge in den Skripts Registrierungsdaten, die Sie schreiben, um den Projekttyp zu registrieren.  Die tatsächlich Einträge und ihre Verwendung schwankten möglicherweise auf der Grundlage der jeweiligen Anforderungen des Projekttyps.  Sie sollten die Beispiele, die zum Überprüfen eines zu suchenden verfügbar sind, das eng dem Projekttyp ähnelt, das Sie entwickeln, und die Registrierung von Skripts für dieses Beispiel wird anschließend erneut auszuführen.  
  
 In den folgenden Beispielen sind in HKEY\_CLASSES\_ROOT.  
  
## Beispiel  
  
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
  
|Name|Typ|Daten|Beschreibung|  
|----------|---------|-----------|------------------|  
|`@`|REG\_SZ|`FigPrjFile`|Name und Beschreibung der Projekttyp von Dateien mit der Erweiterung .figp haben.|  
|`Content Type`|REG\_SZ|`Text/plain`|Inhaltstyp für die Projektdateien.|  
|`NullFile`|REG\_SZ|`Null`||  
|`@`|REG\_SZ|`%MODULE%,-206`|Standardsymbol für Projekt dieses Typs.  Die %MODULE% Anweisung wird in der Registrierung zum Standardspeicherort des Projekttyps DLL abgeschlossen.|  
|`@`|REG\_SZ|`&Open in Visual Studio`|standardmäßigen Anwendung, in der dieser Projekttyp geöffnet ist.|  
|`@`|REG\_SZ|`devenv.exe "%1"`|Standardbefehl, der ausgeführt wird, wenn ein Projekt dieses Typs geöffnet ist.|  
  
 In den folgenden Beispielen werden von HKEY\_LOCAL\_MACHINE und werden in der Registrierung unter dem Schlüssel \[HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ Packages \\ 99.0Exp.\]  
  
## Beispiel  
  
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
  
|Name|Typ|Daten|Beschreibung|  
|----------|---------|-----------|------------------|  
|`@`\(Standard\)|REG\_SZ|`FigPrj Project VSPackage`|Lokalisierbarer Name dieser registrierte VSPackage \(Projekttyp\).|  
|`InprocServer32`|REG\_SZ|`%MODULE%`|Der Pfad des Projekttyps DLL.  Die IDE lädt diese DLL und führt das VSPackage\-CLSID zu `DllGetClassObject` , um <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> abzurufen, um das <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>\-Objekt zu erstellen.|  
|`CompanyName`|REG\_SZ|`Microsoft`|Name des Unternehmens, das den Projekttyp entwickelt hat.|  
|`ProductName`|REG\_SZ|`Figure Project Sample`|Name für den Projekttyp.|  
|`ProductVersion`|REG\_SZ|`9.0`|Versionsnummer der Projekttyp Version.|  
|`MinEdition`|REG\_SZ|`professional`|VSPackages Edition, das gerade registriert wird.|  
|`ID`|REG\_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Der Paketladeschlüssel für das Projekt VSPackage.  Die Schlüssel werden überprüft, wenn ein Projekt geladen wird, nachdem die Umgebung gestartet wurde.|  
|`DllName`|REG\_SZ|`%RESOURCE_DLL%`|Dateiname der Satelliten\-DLL, der die lokalisierten Ressourcen für den Projekttyp enthält.|  
|`Path`|REG\_SZ|`%RESOURCE_PATH%`|Der Pfad der Satelliten\-DLL.|  
|`FigProjectsEvents`|REG\_SZ|\- Anweisung finden Sie für Wert.|Bestimmt die Textzeichenfolge, die für dieses Automatisierungsereignis zurückgegeben wurde.|  
|`FigProjectItemsEvents`|REG\_SZ|\- Anweisung finden Sie für Wert.|Bestimmt die Textzeichenfolge, die für dieses Automatisierungsereignis zurückgegeben wurde.|  
  
 Alle nachfolgenden Beispiele sind in der Registrierung unter dem Schlüssel \[HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ Projects \\ 9.0Exp.\]  
  
## Beispiel  
  
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
  
|Name|Typ|Daten|Beschreibung|  
|----------|---------|-----------|------------------|  
|`@`|REG\_SZ|`FigPrj Project`|Standardname von Projekten aus diesem Typ.|  
|`DisplayName`|REG\_SZ|`#%IDS_PROJECT_TYPE%`|Ressourcen\-ID des vom Satelliten\-DLL abzurufenden Namen, registriert unter Paketen.|  
|`Package`|REG\_SZ|`%CLSID_Package%`|Klassenbezeichner VSPackages mit registrierten Pakete.|  
|`ProjectTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Standardpfad von Projektvorlagen werden.  Dies sind die Dateien, auf die die neue Projektvorlage angezeigt werden.|  
|`ItemTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Standardpfad von Projektelement\-Vorlagendateien.  Dies sind die Dateien, auf die die Vorlage Neues Element hinzufügen angezeigt werden.|  
|`DisplayProjectFileExtensions`|REG\_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Aktiviert die IDE, um das Dialogfeld **Öffnen** zu implementieren.|  
|`PossibleProjectExtensions`|REG\_SZ|`figp`|Wird von der IDE, um zu bestimmen, ob das Projekt, das geöffnet wird, durch diesen Projekttyp geändert wird \(Projekt factory\).  Das Format für mehr als einen Eintrag ist eine durch Semikolon getrennte Liste.  Beispiel: „vdproj. vdp“.|  
|`DefaultProjectExtension`|REG\_SZ|`.figp`|Wird von der IDE als die Standarddateinamenerweiterung für das Vorgang.|  
|`Filter Settings`|REG\_DWORD|Verschieden, finden Sie unter Statements und Kommentare nach Tabelle.|Diese Einstellungen werden verwendet, um die verschiedenen Filter für das Anzeigen von Dateien in Benutzeroberfläche\-Dialogfeldern festzulegen.|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Ressourcen\-ID für fügen Elementvorlagen hinzu.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Der Pfad der Projektelemente angezeigt im Dialogfeld für die **Neues Element hinzufügen** Vorlage.|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|Bestimmt die Sortierreihenfolge im Strukturknoten aus den Dateien, die im Dialogfeld **Neues Element hinzufügen** angezeigt werden.|  
  
 In der folgenden Tabelle sind die Filteroptionen an, die im vorherigen Codesegment verfügbar sind.  
  
|Filtern Sie die Option|Beschreibung|  
|----------------------------|------------------|  
|`CommonFindFilesFilter`|Gibt an, dass der Filter einer der allgemeinen Filter im Dialogfeld **In Dateien suchen** ist.  Die allgemeinen Filter werden in der Liste Filter vor den Filtern angezeigt, die nicht als Common gekennzeichnet sind.|  
|`CommonOpenFilesFilter`|Gibt an, dass der Filter einer der allgemeinen Filter im Dialogfeld **Datei öffnen** ist.  Die allgemeinen Filter werden in der Liste Filter vor den Filtern angezeigt, die nicht als Common gekennzeichnet sind.|  
|`FindInFilesFilter`|Gibt an, dass der Filter im Dialogfeld Filter **In Dateien suchen** eine der aufgeführten und ist nach dem Common filtert.|  
|`NotOpenFileFilter`|Gibt an, dass der Filter nicht im **Datei öffnen** Dialogfeld verwendet wird.|  
|`NotAddExistingItemFilter`|Gibt an, dass der Filter nicht im Hinzufügens\- **Vorhandenes Element** Dialogfeld verwendet wird.|  
  
 Wenn ein Filter keine oder mehrere dieser festgelegten Flags festgelegt ist, wird der Filter **Datei öffnen** und im Dialogfeld **Vorhandenes Element hinzufügen** im Dialogfeld nachdem die allgemeinen Filter aufgelistet sind.  Der Filter ist nicht im Dialogfeld **In Dateien suchen** verwendet.  
  
 Alle nachfolgenden Beispiele sind in der Registrierung unter dem Schlüssel \[HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ Projects \\ 9.0Exp.\]  
  
## Beispiel  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Name|Typ|Daten|Beschreibung|  
|----------|---------|-----------|------------------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Ressourcen\-ID für neue Projektvorlagen.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Standardpfad für Projekte des registrierten Projekttyps.|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|Legt die Sortierreihenfolge von Projekten fest, die im Assistenten Neues Projekt hinzufügen angezeigt werden.|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 gibt an, dass Projekte dieses Typs nur im Dialogfeld Neues Projekt angezeigt werden.|  
  
 Alle nachfolgenden Beispiele sind in der Registrierung unter dem Schlüssel \[HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ Projects \\ 9.0Exp.\]  
  
## Beispiel  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Name|Typ|Daten|Beschreibung|  
|----------|---------|-----------|------------------|  
|`@`|REG\_SZ|None|Standardwert, der angibt, dass die folgenden Einträge für die verschiedenen Dateien, Projekten Einträge.|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Ressourcen\-IDen\-Wert für die Vorlagendateien Neues Element.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Standardpfad der Elemente, die im Dialogfeld **Neues Element hinzufügen** angezeigt werden.|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|Richtet die Sortierreihenfolge für die Anzeige im Strukturknoten des Dialogfelds **Neues Element hinzufügen** ein.|  
  
 Im folgenden Beispiel wurde in der Registrierung unter dem Schlüssel \[HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ 9.0Exp \\ Menüs\].  
  
## Beispiel  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 Das Menü einstiegspunkte die IDE auf die Ressource verwendet, um das Menü Informationen abzurufen.  Wenn diese Daten in die Zieldatenbank Menüs zusammengeführt wurde, wird die gleiche Schlüssel im MenusMerged\-Abschnitt der Registrierung hinzugefügt.  VSPackage sollte keine mit dem MenusMerged\-Abschnitt direkt ändern.  Im Datenfeld in der folgenden Tabelle gibt es drei Komma\-trennen FIELDS.  Das erste Feld identifiziert einen vollständigen Pfad einer Datei Menüressourcen:  
  
-   Wenn das erste Feld ausgelassen wird, wird die Menüressource des Satelliten geladenen DLLs, der vom VSPackage GUID gekennzeichnet ist.  
  
 Das zweite Feld identifiziert eine Menüressource ID des Typs CTMENU:  
  
-   Wenn die Ressourcen\-ID angegeben werden, und der Dateipfad durch den ersten Parameter angegeben wird, wird eine Menüressource vom vollständigen Dateipfad geladen.  
  
-   Wenn die Ressourcen\-ID bereitgestellt werden, aber der Dateipfad nicht der Fall ist, wird die Menüressource der Satelliten\-DLL geladen.  
  
-   Wenn der vollständige Dateipfad zur Verfügung gestellt wird und die Ressourcen\-ID ausgelassen, ist die zu ladende Datei erwartet, eine CTO\-Datei sein.  
  
 Das letzte Feld identifiziert die Versionsnummer für die CTMENU\-Ressource.  Sie können das Menü erneut zusammenführen, indem Sie die Versionsnummer ändern.  
  
|Name|Typ|Daten|Beschreibung|  
|----------|---------|-----------|------------------|  
|%CLSID\_Package%|REG\_SZ|`,1000,1`|Die Ressource, die die Menü Informationen abzurufen.|  
  
 Alle nachfolgenden Beispiele sind in der Registrierung unter dem Schlüssel \[HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ 9.0Exp \\ NewProjectTemplates\].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Name|Typ|Daten|Beschreibung|  
|----------|---------|-----------|------------------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Ressourcen\-IDen\-Wert für die Abbildungs\-Projekt\-neuen Project Templates.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Standardpfad des Verzeichnisses Neues Projekt.  Elemente in diesem Verzeichnis **Assistent für neue Projekte** werden im Dialogfeld angezeigt.|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|Richtet die Reihenfolge ein, in der Projekte im Strukturknoten **Neues Projekt** des Dialogfelds angezeigt werden.|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 gibt an, dass Projekte dieses Typs nur im **Neues Projekt** Dialogfelds angezeigt werden.|  
  
 Im folgenden Beispiel wurde in der Registrierung unter dem Schlüssel \[HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ 9.0Exp \\ InstalledProducts\].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Name|Typ|Daten|Beschreibung|  
|----------|---------|-----------|------------------|  
|`Package`|REG\_SZ|`%CLSID_Package%`|Klassenbezeichner registrierten VSPackages.|  
|`UseInterface`|REG\_DWORD|`1`|1 gibt an, dass die Benutzeroberfläche verwendet wird, um mit diesem Projekt zu interagieren.  0 gibt an, dass keine Benutzeroberfläche\-Schnittstelle vorhanden ist.|  
  
 The.vsz\-Dateien, die neue Projekttypen häufig steuern, enthalten einen RELATIVE\_PATH\-Eintrag.  Dieser Pfad ist relativ zum Pfad, der unter \\ ProductDir\-Eintrag des Projekttyps der nächsten Tastatureingabe Setup angegeben wird:  
  
 HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ Setup \\ 7.0Exp  
  
 Zum Beispiel fügen die Enterprise\-Framework Registrierungseinträge die folgenden projektvorlagen hinzu:  
  
 HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ 7.0Exp \\ Setup \\ E\-F\- C:\\Program Files\\Microsoft \= ProductDir \\ Visual Studio \\ \\ EnterpriseFrameworks  
  
 Das heißt, wenn Sie einen PROJECT\_TYPE\=EF\-Eintrag in der VSZ\-Datei einschließen, die Umgebung durchsucht die .vsz\-Dateien im ProductDir\-Verzeichnis, das zuvor angegeben wird.  
  
## Siehe auch  
 [Prüfliste: Erstellen von neuen Typen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)   
 [Erstellen von Instanzen von Project mithilfe von Project\-Factorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)