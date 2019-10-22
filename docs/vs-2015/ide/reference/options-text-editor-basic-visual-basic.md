---
title: Optionen, Text-Editor, Basic (Visual Basic) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1edb7ceae1ba187b01b92d64ca33d41d83364e72
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662373"
---
# <a name="options-text-editor-basic-visual-basic"></a>Optionen, Text-Editor, Standard (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Eigenschaftenseite **VB-spezifisch** im Ordner **Basic** im Ordner **Text-Editor** des Dialogfelds **Optionen** (Menü **Extras**) enthält die folgenden Eigenschaften.

 **Automatisches Einfügen von End-Konstruktionen:** Wenn Sie z.B. die erste Zeile einer Prozedurdeklaration, `Sub Main—`, eingeben und die EINGABETASTE drücken, wird im Text-Editor eine entsprechende `End Sub`-Zeile hinzugefügt. Ebenso wird beim Hinzufügen einer [For](https://msdn.microsoft.com/library/f5fc0d51-67ce-4c36-9f09-31c9a91c94e9)-Schleife im Text-Editor eine entsprechende `Next`-Anweisung hinzugefügt. Wenn diese Option ausgewählt ist, wird im Code-Editor automatisch das end-Konstrukt eingefügt.

 **Automatische Strukturierung und Einrückung des Programmcodes:** Der Text-Editor formatiert den Code entsprechend neu. Wenn diese Option aktiviert ist, führt der Code-Editor die folgenden Aufgaben durch:

- Ausrichten des Codes an der richtigen Tabulatorposition

- Ändern der Groß-/Kleinschreibung von Schlüsselwörtern, Variablen und Objekten in die richtige Schreibweise

- Hinzufügen eines fehlenden `Then` zu einer `If...Then`-Anweisung

- Hinzufügen von Klammern zu Funktionsaufrufen

- Hinzufügen fehlender Anführungszeichen am Ende von Zeichenfolgen

- Neuformatieren der exponentiellen Notation

- Neuformatieren von Datumsangaben

  Gliederungs **Modus aktivieren** Wenn Sie im Code-Editor eine Datei öffnen, können Sie das Dokument im Gliederungs Modus anzeigen. Weitere Informationen finden Sie unter [Gliedern](../../ide/outlining.md). Ist diese Option ausgewählt, wird die Gliederungsfunktion beim Öffnen einer Datei aktiviert.

  **Automatisches Einfügen von Schnittstellen-und MustOverride-** Membern Wenn Sie einen Commit für eine `Implements`-Anweisung oder eine `Inherits`-Anweisung für eine Klasse durchgeführt haben, fügt der Text-Editor Prototypen für die Member ein, die implementiert bzw. überschrieben werden müssen.

  **Zeilen Trennzeichen für Prozedur anzeigen** Der Text-Editor gibt den visuellen Bereich von Prozeduren an. In den VB-Quelldateien des Projekts werden an den in der folgenden Tabelle aufgeführten Positionen Linien gezeichnet:

|Position in der VB-Quelldatei|Beispiel für die Linienposition|
|---------------------------------|------------------------------|
|Nach dem Schließen eines Blockdeklarationskonstrukts|– Am Ende einer Klasse, einer Struktur, eines Moduls, einer Schnittstelle oder einer Enumeration<br />– Hinter einer Eigenschaft, Funktion oder Sub<br />– Nicht zwischen den get- und set-Klauseln in einer Eigenschaft|
|Nach mehreren Einzelzeilenkonstrukten|– Hinter Import-Anweisungen, vor einer Typdefinition in einer Klassendatei<br />– Hinter den in einer Klasse deklarierten Variablen, vor jeglichen Prozeduren|
|Nach Einzelzeilendeklarationen (Deklarationen, die nicht auf Blockebene erfolgen)|– Nach Import-Anweisungen, Inherits-Anweisungen, Variablendeklarationen, Ereignisdeklarationen, Delegatdeklarationen und Declare-Anweisungen für DLLs|

 **Vorschläge zur Fehlerkorrektur aktivieren** Der Text-Editor kann für häufige Fehler Lösungen vorschlagen und es Ihnen ermöglichen, die geeignete Korrektur auszuwählen, die dann auf den Code angewendet wird.

 **Hervorhebung von verweisen und Schlüsselwörtern aktivieren** Der Text-Editor kann alle Instanzen eines Symbols oder alle Schlüsselwörter in einer-Klausel, z. b. `If..Then`, `While...End While` oder `Try...Catch...Finally`, hervorheben. Sie können zwischen markierten Verweisen oder Schlüsselwörtern durch Drücken von STRG+UMSCHALT+NACH-UNTEN oder STRG+UMSCHALT+NACH-OBEN navigieren.

## <a name="see-also"></a>Siehe auch
 [Allgemein, Umgebung, Optionen (Dialog Feld](../../ide/reference/general-environment-options-dialog-box.md) ) [, Text-Editor, alle Sprachen, Registerkarten](../../ide/reference/options-text-editor-all-languages-tabs.md)
