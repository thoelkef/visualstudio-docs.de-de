---
title: Beschreibung der Vorlage Verzeichnis (. VSDIR)-Dateien | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 739dd0d41fb63c4993dad0d66737aaada1cf01c4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="template-directory-description-vsdir-files"></a>Beschreibung der Vorlage Verzeichnis (. VSDIR)-Dateien
Eine Vorlage Directory Beschreibungsdatei (VSDIR) ist eine Textdatei, mit der integrierten Entwicklungsumgebung (IDE) für die Anzeige Ordnern, Assistenten .vsz-Dateien und Dateien, die Ihr Projekt in Dialogfeldern zugeordnet sind. Den Inhalt enthalten einen Datensatz pro Datei oder eines Ordners. Alle VSDIR-Dateien in einer referenzierten Speicherorts werden zusammengeführt, obwohl nur eine VSDIR-Datei in der Regel bereitgestellt wird, um mehrere Ordner, Assistenten oder Vorlagendateien zu beschreiben.  
  
 Ordner (in Unterverzeichnissen), Dateien, die in der VSDIR-Datei und der VSDIR-Datei selbst verwiesen wird, werden im selben Verzeichnis befinden. Wenn die IDE führt einen Assistenten, oder zeigt einen Ordner oder eine Datei in die **neues Projekt** oder **neues Element hinzufügen** Dialogfelder von, die IDE überprüft das Verzeichnis, um festzustellen, ob eine VSDIR-Datei ist die ausgeführten Dateien enthält, vorhanden. Wenn eine VSDIR-Datei gefunden wird, liest die IDE, um zu ermitteln, ob es sich um einen Eintrag für die ausgeführte oder angezeigten Ordner oder die Datei enthält. Wenn ein Eintrag gefunden wird, verwendet die IDE die Informationen in der Ausführung des Assistenten oder die Anzeige des Inhalts an.  
  
 Im folgenden Codebeispiel wird aus der Datei SourceFiles.vsdir ist in der \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems\Source_Files-Registrierungsschlüssel:  
  
```  
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127  
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124  
```  
  
 In diesem Fall sind zwei Datensätze in einer Datei ein. Eine neue Zeile (Wagenrücklaufzeichen) trennt jeder Datensatz. Jede Zeile entspricht ein anderen Dateiformat. Eine Pipe (&#124;) trennt Felder in jedem Datensatz. Ein einzelnes Verzeichnis kann mehrere VSDIR Dateien mit unterschiedlichen Dateinamen enthalten können, oder Sie eine VSDIR-Datei für jeden Dateityp.  
  
## <a name="fields"></a>Felder  
 Die folgende Tabelle enthält die Felder, die für jeden Datensatz angegeben.  
  
|Feld|Beschreibung|  
|-----------|-----------------|  
|Relativer Pfadname (RelPathName)|Der Name des Ordners, einer Vorlage oder VSZ-Datei z. B. HeaderFile.h oder MyWizard.vsz. Dieses Feld kann auch einen Namen, die zur Darstellung von eines Ordners sein.|  
|{clsidPackage}|Die GUID des VSPackage, das Zugriff auf die lokalisierten Zeichenfolgen, z. B. LocalizedName, Beschreibung, Symbolressourcen Kennung und SuggestedBaseName, in die VSPackage Satelliten-dynamic Link Library (DLL) Ressourcen ermöglicht. Symbolressourcen Kennung gilt, wenn DLLPath nicht angegeben wird. **Hinweis:** dieses Feld ist optional, es sei denn, eine oder mehrere der vorherigen Felder ein Ressourcenbezeichner ist. Dieses Feld ist in der Regel bei VSDIR-Dateien, die mit Drittanbieter-Assistenten entsprechen, die nicht ihrem Text lokalisiert ist leer.|  
|LocalizedName|Der lokalisierte Name der Vorlagendatei oder des Assistenten. Dieses Feld kann es sich um eine Zeichenfolge oder ein Ressourcenbezeichner des Formulars "#ResID" sein. Dieser Name wird angezeigt, der **neues Element hinzufügen** (Dialogfeld). **Hinweis:** Wenn LocalizedName ist ein Resource Identifier, {CLSID-Paket} ist erforderlich.|  
|SortPriority|Eine ganze Zahl, die die relative Priorität dieser Vorlagendatei oder Assistenten darstellt. Z. B. Wenn dieses Element den Wert 1 aufweist, wird dann dieses Element neben anderen Elementen mit einem Wert von 1 und vor alle Elemente mit einem Wert für die Sortierung von 2 oder größer angezeigt.<br /><br /> Sortierpriorität ist relativ zu die Elemente im selben Verzeichnis. Es gibt möglicherweise mehr als eine VSDIR-Datei im selben Verzeichnis. In diesem Fall die Elemente aus allen *.* VSDIR-Dateien in diesem Verzeichnis werden zusammengeführt. Elemente mit der gleichen Priorität werden in der Groß-/Kleinschreibung lexikografische Reihenfolge dem angezeigten Namen aufgeführt. Die `_wcsicmp` Funktion wird verwendet, um die Elemente anzuordnen.<br /><br /> Elemente, die nicht in der VSDIR-Dateien beschrieben enthalten eine Priorität Zahl größer als die höchste Priorität Anzahl in der VSDIR-Dateien aufgeführt. Das Ergebnis ist, dass diese Elemente am Ende der angezeigten Liste unabhängig von deren Namen befinden.|  
|Beschreibung|Die lokalisierte Beschreibung der Vorlagendatei oder des Assistenten. Dieses Feld kann es sich um eine Zeichenfolge oder ein Ressourcenbezeichner des Formulars "#ResID" sein. Diese Zeichenfolge wird der **neues Projekt** oder **neues Element hinzufügen** (Dialogfeld), wenn das Element ausgewählt ist.|  
|DLL-Pfad oder {CLSID-Paket}|Wird verwendet, um ein Symbol für die Datei für Prozessvorlagen oder den Assistenten zu laden. Das Symbol wird als eine Ressource aus einer .dll oder .exe-Datei mithilfe der Symbolressourcen Kennung geladen. Diese .dll oder .exe-Datei kann entweder über einen vollständigen Pfad oder mithilfe einer GUID eines VSPackage identifiziert werden. Die DLL des VSPackage-Implementierung wird verwendet, um das Symbol "(nicht die Satelliten-DLL) zu laden.|  
|Symbolressourcenkennung|Der Ressourcenbezeichner in der DLL oder VSPackage-Implementierung DLL, die bestimmt, welches Symbol angezeigt.|  
|Flags (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>)|Zum Aktivieren oder deaktivieren Sie die **Namen** und **Speicherort** Felder auf der **neues Element hinzufügen** (Dialogfeld). Der Wert, der die **Flags** Feld ist die Dezimalzahl der Kombination von Bitflags erforderlich.<br /><br /> Wenn ein Benutzer ein Element auswählt, auf die **neu** Registerkarte des Projekts bestimmt, ob das Feld Name und das Feld "Speicherort" angezeigt werden die **neues Element hinzufügen** wird zuerst das Dialogfeld angezeigt. Ein Element kann nur über eine VSDIR-Datei steuern, ob die Felder im Vergleich zu deaktiviert aktiviert sind, wenn das Element ausgewählt ist.|  
|SuggestedBaseName|Stellt den Standardnamen für die Datei, einem Assistenten oder einer Vorlage dar. Dieses Feld ist eine Zeichenfolge oder ein Ressourcenbezeichner des Formulars "#ResID". Die IDE verwendet diesen Wert einen Standardnamen für das Element bereitstellen. Dieser Preis ist mit einem ganzzahligen Wert um den Namen eindeutig sind, z. B. MyFile21.asp machen angefügt.<br /><br /> Wenden Sie in der vorstehenden Liste Beschreibung, DLLPath, Symbolressourcen Kennung, Flags und SuggestedBaseNumber nur für Vorlagen-und Assistenten. Diese Felder gelten nicht für Ordner. Dies wird im Code in der Datei BscPrjProjectItems veranschaulicht die \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems-Registrierungsschlüssel. Diese Datei enthält drei Datensätze (eine für jeden Ordner) mit vier Feldern für jeden Datensatz: RelPathName {CLSID-Paket} LocalizedName und SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120`|  
  
 Wenn Sie eine Assistentendatei erstellen, sollten Sie auch die folgenden Probleme.  
  
-   Ein optionales Feld, für das es keine sinnvollen Daten gibt, sollte als Platzhalter 0 (null) enthalten.  
  
-   Wenn kein lokalisierter Name angegeben ist, wird der relativen Pfadnamen in der Assistentendatei verwendet.  
  
-   DLLPath überschreibt ClsidPackage für symbolplatzierung.  
  
-   Wenn kein Symbol definiert ist, ersetzt die IDE das Standardsymbol für eine Datei, die diese Erweiterung hat.  
  
-   Wenn keine empfohlene Basisname angegeben wird, wird "Projekt" verwendet.  
  
-   Wenn Sie die .vsz-Dateien, Ordner oder Dateien löschen, müssen Sie auch die zugehörigen Datensätze aus der VSDIR-Datei entfernen.  
  
## <a name="see-also"></a>Siehe auch  
 [Assistenten](../../extensibility/internals/wizards.md)   
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)