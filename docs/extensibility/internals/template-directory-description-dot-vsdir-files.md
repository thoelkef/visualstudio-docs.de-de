---
title: Beschreibung des Vorlagenverzeichnisses (. Vsdir) Dateien | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16ba609d5b05d565a12b38bd19e9a777851ced5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704688"
---
# <a name="template-directory-description-vsdir-files"></a>Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)
Eine Vorlagenverzeichnisbeschreibungsdatei (.vsdir) ist eine Textdatei, mit der die integrierte Entwicklungsumgebung (IDE) Ordner, .vsz-Dateien und Vorlagendateien anzeigen kann, die Ihrem Projekt in Dialogfeldern zugeordnet sind. Der Inhalt umfasst einen Datensatz pro Datei oder Ordner. Alle .vsdir-Dateien an einem referenzierten Speicherort werden zusammengeführt, obwohl im Allgemeinen nur eine .vsdir-Datei bereitgestellt wird, um mehrere Ordner, Assistenten oder Vorlagendateien zu beschreiben.

 Ordner (Unterverzeichnisse), Dateien, auf die in der .vsdir-Datei verwiesen wird, und die .vsdir-Datei selbst befinden sich alle im selben Verzeichnis. Wenn die IDE einen Assistenten ausführt oder einen Ordner oder eine Datei in den Dialogfeldern **Neues Projekt** oder Neues **Element hinzufügen** anzeigt, untersucht die IDE das Verzeichnis, das die ausgeführten Dateien enthält, um festzustellen, ob eine .vsdir-Datei vorhanden ist. Wenn eine .vsdir-Datei gefunden wird, liest die IDE sie, um festzustellen, ob sie einen Eintrag für den ausgeführten oder angezeigten Ordner oder die Datei enthält. Wenn ein Eintrag gefunden wird, verwendet die IDE die Informationen bei der Ausführung des Assistenten oder der Anzeige des Inhalts.

 Das folgende Codebeispiel stammt aus der Datei \<SourceFiles.vsdir im Registrierungsschlüssel EnvSDK>-BscPrj-BscPrj-BscPrj-BscPrj-Source_Files-Registrierungsschlüssel:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 In diesem Fall befinden sich zwei Datensätze in einer Datei. Eine neue Zeile (Wagenrücklaufzeichen) trennt jeden Datensatz. Jede Zeile stellt einen anderen Dateityp dar. Ein Pipe-Zeichen (&#124;) trennt Felder in jedem Datensatz. Ein einzelnes Verzeichnis kann mehrere .vsdir-Dateien mit unterschiedlichen Dateinamen enthalten, oder Sie können eine .vsdir-Datei für jeden Dateityp haben.

## <a name="fields"></a>Felder
 In der folgenden Tabelle sind die für jeden Datensatz angegebenen Felder aufgeführt.

| Feld | BESCHREIBUNG |
| - | - |
| Relativer Pfadname (RelPathName) | Der Name des Ordners, der Vorlage oder der .vsz-Datei, z. B. HeaderFile.h oder MyWizard.vsz. Bei diesem Feld kann es sich auch um einen Namen handeln, der zur Darstellung eines Ordners verwendet wird. |
| {clsidPackage} | Die GUID des VSPackage, die den Zugriff auf lokalisierte Zeichenfolgen wie LocalizedName, Description, IconResourceId und SuggestedBaseName in den DLL-Ressourcen (Satellite Dynamic Link Library) des VSPackage ermöglicht. IconResourceId gilt, wenn DLLPath nicht angegeben wird. **Hinweis:**  Dieses Feld ist optional, es sei denn, eines oder mehrere der vorherigen Felder ist ein Ressourcenbezeichner. Dieses Feld ist in der Regel für .vsdir-Dateien leer, die mit Assistenten von Drittanbietern korrespondieren, die ihren Text nicht lokalisieren. |
| LocalizedName | Der lokalisierte Name der Vorlagendatei oder des Assistenten. Bei diesem Feld kann es sich um eine Zeichenfolge oder einen Ressourcenbezeichner des Formulars "#ResID" ergehen. Dieser Name wird im Dialogfeld **Neues Element hinzufügen** angezeigt. **Hinweis:**  Wenn LocalizedName ein Ressourcenbezeichner ist, ist die Option "clsidPackage" erforderlich. |
| SortPriority | Eine ganze Zahl, die die relative Priorität dieser Vorlagendatei oder des Assistenten darstellt. Wenn dieses Element beispielsweise den Wert 1 hat, wird dieses Element neben anderen Elementen mit dem Wert 1 und vor allen Elementen mit einem Sortierwert von 2 oder größer angezeigt.<br /><br /> Die Sortierpriorität ist relativ zu den Elementen im gleichen Verzeichnis. Möglicherweise befinden sich mehr als eine .vsdir-Datei im selben Verzeichnis. In diesem Fall werden die Elemente aus allen <em>.</em> vsdir-Dateien in diesem Verzeichnis werden zusammengeführt. Elemente mit der gleichen Priorität werden in der lexikographischen Reihenfolge des angezeigten Namens in der nicht beachteten lexikographischen Reihenfolge aufgeführt. Die `_wcsicmp` Funktion wird verwendet, um die Artikel zu bestellen.<br /><br /> Elemente, die nicht in .vsdir-Dateien beschrieben werden, enthalten eine Prioritätsnummer, die größer ist als die in den .vsdir-Dateien aufgeführte Nummer mit der höchsten Priorität. Das Ergebnis ist, dass sich diese Elemente unabhängig von ihrem Namen am Ende der angezeigten Liste befinden. |
| BESCHREIBUNG | Die lokalisierte Beschreibung der Vorlagendatei oder des Assistenten. Bei diesem Feld kann es sich um eine Zeichenfolge oder einen Ressourcenbezeichner des Formulars "#ResID" ergehen. Diese Zeichenfolge wird im Dialogfeld **Neues Projekt** oder Neues **Element hinzufügen** angezeigt, wenn das Element ausgewählt ist. |
| DLL-Pfad oder {CLSID-Paket} | Wird verwendet, um ein Symbol für die Vorlagendatei oder den Assistenten zu laden. Das Symbol wird als Ressource aus einer .dll- oder EXE-Datei geladen, indem die IconResourceId verwendet wird. Diese .dll- oder EXe-Datei kann entweder mithilfe eines vollständigen Pfads oder mithilfe einer GUID eines VSPackage identifiziert werden. Die Implementierungs-DLL des VSPackage wird verwendet, um das Symbol (nicht die Satelliten-DLL) zu laden. |
| Symbolressourcenkennung | Der Ressourcenbezeichner in der DLL- oder VSPackage-Implementierungs-DLL, die das anzuzeigende Symbol bestimmt. |
| Flaggen<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>( ) | Wird verwendet, um die Felder **Name** und **Speicherort** im Dialogfeld **Neues Element hinzufügen** zu deaktivieren oder zu aktivieren. Der Wert des **Felds Flags** ist das Dezimaläquivalent der Kombination der erforderlichen Bitflags.<br /><br /> Wenn ein Benutzer ein Element auf der Registerkarte **Neu** auswählt, bestimmt das Projekt, ob das Feld Name und das Feld Lagerort angezeigt werden, wenn das Dialogfeld **Neues Element hinzufügen** zum ersten Mal angezeigt wird. Ein Element kann über eine .vsdir-Datei nur steuern, ob die Felder aktiviert oder deaktiviert sind, wenn das Element ausgewählt ist. |
| SuggestedBaseName | Stellt den Standardnamen für die Datei, den Assistenten oder die Vorlage dar. Dieses Feld ist entweder eine Zeichenfolge oder ein Ressourcenbezeichner des Formulars "#ResID". Die IDE verwendet diesen Wert, um einen Standardnamen für das Element bereitzustellen. Dieser Basiswert wird mit einem ganzzahligen Wert angehängt, um den Namen eindeutig zu machen, z. B. MyFile21.asp.<br /><br /> In der vorherigen Liste gelten Beschreibung, DLLPath, IconResourceId, Flags und SuggestedBaseNumber nur für Vorlagen- und Assistentendateien. Diese Felder gelten nicht für Ordner. Diese Tatsache wird im Code in der Datei BscPrjProjectItems im \<Registrierungsschlüssel EnvSDK>-BscPrj-BscPrj-BscPrj-BscPrj-ProjectItems veranschaulicht. Diese Datei enthält drei Datensätze (einen für jeden Ordner) mit vier Feldern für jeden Datensatz: RelPathName, .clsidPackage, LocalizedName und SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Wenn Sie eine Assistentendatei erstellen, sollten Sie auch die folgenden Probleme berücksichtigen.

- Ein optionales Feld, für das es keine sinnvollen Daten gibt, sollte als Platzhalter 0 (null) enthalten.

- Wenn kein lokalisierter Name angegeben wird, wird der relative Pfadname in der Assistentendatei verwendet.

- DLLPath überschreibt clsidPackage für den Speicherort des Symbols.

- Wenn kein Symbol definiert ist, ersetzt die IDE das Standardsymbol für eine Datei mit dieser Erweiterung.

- Wenn kein vorgeschlagener Basisname angegeben wird, wird 'Projekt' verwendet.

- Wenn Sie die .vsz-Dateien, Ordner oder Vorlagendateien löschen, müssen Sie auch die zugehörigen Datensätze aus der .vsdir-Datei entfernen.

## <a name="see-also"></a>Weitere Informationen
- [Assistenten](../../extensibility/internals/wizards.md)
- [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
