---
title: Beschreibung der Vorlage Verzeichnis (. VSDIR)-Dateien | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0bcd3855b5dd2fc701b78c5745a9053d19dc7fcf
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658252"
---
# <a name="template-directory-description-vsdir-files"></a>Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)
Eine Vorlage Directory-Beschreibungsdatei (VSDIR) ist eine Textdatei, die es ermöglicht die integrierte Entwicklungsumgebung (IDE) zum Anzeigen von Ordnern, Assistenten VSZ-Dateien und Vorlagendateien, die dem Projekt in Dialogfeldern zugeordnet sind. Der Inhalt enthalten einen Datensatz pro Datei oder eines Ordners. Obwohl nur eine VSDIR-Datei in der Regel bereitgestellt wird, um mehrere Ordner, Assistenten oder Vorlagendateien zu beschreiben werden, alle VSDIR-Dateien an einem Ort auf die verwiesen wird zusammengeführt.

 Ordner (Unterverzeichnisse), Dateien, die in der VSDIR-Datei, und der VSDIR-Datei selbst verwiesen wird im gleichen Verzeichnis befinden. Wenn die IDE führt einen Assistenten, oder zeigt einen Ordner oder eine Datei in die **neues Projekt** oder **neues Element hinzufügen** Dialogfelder, die IDE untersucht das Verzeichnis mit den ausgeführten Dateien aus, um zu bestimmen, ob eine VSDIR-Datei ist vorhanden. Wenn eine VSDIR-Datei gefunden wird, liest die IDE, um zu ermitteln, ob es sich um einen Eintrag für die ausgeführte oder angezeigten Ordner oder die Datei enthält. Wenn ein Eintrag gefunden wird, verwendet die IDE die Informationen in die Ausführung des Assistenten oder Anzeige des Inhalts an.

 Im folgenden Codebeispiel wird aus der Datei SourceFiles.vsdir ist in der \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems\Source_Files-Registrierungsschlüssel:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 In diesem Fall sind zwei Datensätze in einer Datei ein. Eine neue Zeile (Wagenrücklaufzeichen) trennt jeden Datensatz. Jede Zeile steht für ein anderes Dateiformat. Eine Pipe (&#124;)-Zeichen als Trennzeichen für Felder in jedem Datensatz. Ein einzelnes Verzeichnis kann mehrere VSDIR-Dateien, die unterschiedliche Dateinamen enthalten können, Sie auch eine VSDIR-Datei für jeden Dateityp.

## <a name="fields"></a>Felder
 Die folgende Tabelle enthält die Felder, die für jeden Datensatz angegeben.

| Feld | Beschreibung |
| - | - |
| Relativer Pfadname (RelPathName) | Der Name des der Ordner, einer Vorlage oder VSZ-Datei, z. B. HeaderFile.h oder MyWizard.vsz. Dieses Feld kann auch einen Namen, die zum Darstellen von eines Ordners sein. |
| {clsidPackage} | Die GUID des VSPackage, die Zugriff auf die lokalisierten Zeichenfolgen, z. B. LocalizedName, Beschreibung, Symbolressourcen Kennung und SuggestedBaseName, in die VSPackage Satelliten-dynamic Link Library (DLL) Ressourcen ermöglicht. Symbolressourcen Kennung gilt, wenn DLL-Pfad nicht angegeben ist. **Hinweis**:  Dieses Feld ist optional, es sei denn, eine oder mehrere dieser vorherigen Felder eine Ressourcen-ID ist. Dieses Feld ist in der Regel für VSDIR-Dateien, die mit Drittanbieter-Assistenten entsprechen, die nicht den Text lokalisieren ist leer. |
| LocalizedName | Der lokalisierte Name der Vorlagendatei oder des Assistenten. Dieses Feld kann es sich um eine Zeichenfolge oder eine ressourcenkennung in der Form "#ResID" sein. Dieser Name wird angezeigt, der **neues Element hinzufügen** Dialogfeld. **Hinweis**:  Wenn LocalizedName eine Ressourcen-ID ist {CLSID-Paket} erforderlich ist. |
| SortPriority | Eine ganze Zahl, die die relative Priorität dieser Vorlagendatei oder Assistenten darstellt. Z. B. Wenn dieses Element den Wert 1 aufweist, klicken Sie dann dieses Element neben anderen Elementen mit einem Wert von 1 und vor alle Elemente mit einem Wert für die Sortierreihenfolge 2 oder größer wird.<br /><br /> Sortierpriorität ist relativ zu den Elementen im selben Verzeichnis. Es gibt möglicherweise mehr als eine VSDIR-Datei im selben Verzeichnis. In diesem Fall die Elemente aus allen <em>.</em> VSDIR-Dateien in diesem Verzeichnis werden zusammengeführt. Elemente mit derselben Priorität werden in der Groß-/Kleinschreibung lexikografischen Reihenfolge der angezeigten Namen aufgeführt. Die `_wcsicmp` Funktion wird verwendet, um die Elemente anzuordnen.<br /><br /> Elemente, die nicht in der VSDIR-Dateien beschrieben enthalten eine Priorität größere Zahl als die höchste Priorität Anzahl, die in der VSDIR-Dateien aufgeführt. Das Ergebnis ist, dass diese Elemente am Ende der angezeigten Liste aus, unabhängig von deren Namen. |
| Beschreibung | Die lokalisierte Beschreibung der Vorlagendatei oder des Assistenten. Dieses Feld kann es sich um eine Zeichenfolge oder eine ressourcenkennung in der Form "#ResID" sein. Diese Zeichenfolge wird in der **neues Projekt** oder **neues Element hinzufügen** Dialogfeld, wenn das Element ausgewählt ist. |
| DLL-Pfad oder {CLSID-Paket} | Wird verwendet, um ein Symbol für die Vorlagendatei oder den Assistenten zu laden. Das Symbol wird als Ressource aus einer .dll oder .exe-Datei mithilfe der Symbolressourcen Kennung geladen. Diese .dll oder .exe-Datei kann entweder mithilfe eines vollständigen Pfads oder mithilfe einer GUID eines VSPackage identifiziert werden. Die DLL des VSPackage-Implementierung wird verwendet, um das Symbol "(nicht Satelliten-DLL) zu laden. |
| Symbolressourcenkennung | Der Ressourcenbezeichner in der DLL-Datei oder VSPackage-Implementierung von DLL, die das anzuzeigende Symbol bestimmt. |
| Flags (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>) | Zum Aktivieren oder deaktivieren Sie die **Namen** und **Speicherort** Felder der **neues Element hinzufügen** Dialogfeld. Der Wert des der **Flags** Feld ist die dezimale Entsprechung der Kombination von Bitflags erforderlich.<br /><br /> Wenn ein Benutzer ein Element auswählt, auf die **neu** Registerkarte des Projekts bestimmt, ob das Feld Name und das Feld "Speicherort" beim angezeigt werden die **neues Element hinzufügen** wird zuerst das Dialogfeld angezeigt. Ein Element kann nur über eine VSDIR-Datei steuern, ob die Felder im Vergleich zu deaktiviert aktiviert sind, wenn das Element ausgewählt ist. |
| SuggestedBaseName | Stellt den Standardnamen für die Datei, den Assistenten oder die Vorlage an. Dieses Feld ist entweder eine Zeichenfolge oder ein Ressourcenbezeichner, der Form "#ResID". Die IDE verwendet diesen Wert, um einen Standardnamen für das Element bereitzustellen. Basiswert ist ein ganzzahliger Wert und den Namen eindeutig sind, z. B. MyFile21.asp macht angefügt.<br /><br /> Wenden in der vorherigen Liste Beschreibung, DLL-Pfad, Symbolressourcen Kennung, Flags und SuggestedBaseNumber nur für die Vorlagen-und Assistenten. Diese Felder gelten nicht für Ordner. Dies wird im Code in der Datei BscPrjProjectItems veranschaulicht die \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems-Registrierungsschlüssel. Diese Datei enthält drei Datensätze (eine für jeden Ordner) mit vier Feldern für die einzelnen Datensätze: RelPathName, {CLSID-Paket}, LocalizedName und SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Wenn Sie eine Datei des Assistenten zum Erstellen, sollten Sie auch die folgenden Probleme.

-   Ein optionales Feld, für das es keine sinnvollen Daten gibt, sollte als Platzhalter 0 (null) enthalten.

-   Wenn kein lokalisierter Name angegeben ist, wird der relativen Pfadnamen in der Assistentendatei verwendet.

-   DLLPath überschreibt CLSID-Paket für den Symbolspeicherort.

-   Wenn kein Symbol definiert ist, ersetzt die IDE das Standardsymbol einer Datei, die diese Erweiterung hat.

-   Wenn kein vorgeschlagener Basisname angegeben wird, wird "Project" verwendet.

-   Wenn Sie die VSZ-Dateien, Ordner oder Vorlagendateien löschen, müssen Sie auch die zugehörigen Datensätze aus der VSDIR-Datei entfernen.

## <a name="see-also"></a>Siehe auch
- [Assistenten](../../extensibility/internals/wizards.md)
- [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)