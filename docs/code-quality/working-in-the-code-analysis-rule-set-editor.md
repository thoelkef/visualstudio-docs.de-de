---
title: Verwenden der Code Analysis-Editor in Visual Studio Regelsatz | Microsoft Docs
ms.date: 04/-4/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab1a49cd8f0376a8a144f1a6f889bac0c5963b6e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Verwenden Sie den Code Analysis Regelsatz-editor

Der Code Analysis Regelsatz-Editor können Sie die Regeln angeben, die in einem benutzerdefinierten Regelsatz und den Schweregrad der Verletzungen von Schwellenwertregeln enthalten sind.

|Aktion (Schweregrad)|Beschreibung|
|-|-|
|Warnung|Generiert eine Warnung in der **Fehlerliste** und auch während des Buildvorgangs.|
|Fehler|Generiert einen Fehler in der **Fehlerliste** und auch während des Buildvorgangs.|
|Info|Generiert eine Nachricht in die **Fehlerliste**.|
|Hidden|Die Verletzung ist nicht für den Benutzer sichtbar. Die IDE wird jedoch von die Überschreitung benachrichtigt.|
|Keiner|Die Regel unterdrückt wird. Das Verhalten entspricht dem, als ob die Regel aus dem Regelsatz entfernt wurde.|

Der Editor zeigt die Regeln in einer Baumstruktur, die Gruppen der Regeln nach Feld festlegen, die Sie angeben. Zum Hinzufügen oder Entfernen von Regeln aus einem Regelsatz, können führen Sie eine oder mehrere der folgenden Schritte aus:

- Aktivieren Sie oder deaktivieren Sie das Kontrollkästchen für den Gruppenknoten hinzufügen oder entfernen alle Regeln in der Gruppe. Wenn Sie eine Gruppe auswählen, werden alle Regeln festgelegt, dass Sie die **Warnung** Aktion.

   > [!TIP]
   > Sie können ändern, wie Regeln gruppiert werden, in der **Gruppieren nach** Dropdown-Menü.

- Klicken Sie auf die **Aktion** Feld einer Gruppe, und geben Sie dann die Aktion für alle Regeln in der Gruppe angewendet.

- Aktivieren Sie oder deaktivieren Sie das Kontrollkästchen für eine einzelne Regel. Wenn Sie das Kontrollkästchen für eine Regel auswählen, wird die Regel auf die Warnaktion festgelegt.

## <a name="toolbar"></a>Symbolleiste

Sie können die Symbolleiste des Regelsatz-Editor verwenden, zu gruppieren, Filtern und suchen die angezeigten Daten im Raster Gruppe "Regel".

Die folgende Tabelle beschreibt die Steuerelemente auf der Symbolleiste des Regelsatz-Editor.

|ToolBar-Steuerelement|Beschreibung|
|---------------------|-----------------|
|**Alle Ebenen erweitern**|Zeigt die Regeln in allen Gruppen an.|
|**Alle Ebenen reduzieren**|Blendet die Regeln in allen Gruppen an.|
|**Group By**|Gibt das Feld mit dem Regeln gruppiert werden. Klicken Sie auf  **\<None >** die Regeln ohne Gruppen anzuzeigen.|
|**Spaltenoptionen**|Gibt die Regelfelder angezeigt.|
|**Regeln ausblenden, die nicht für die aktuelle Projektmappe gelten**|Anzeigen oder ausblenden Regeln, die nicht von den gleichen Zieltyp wie die Lösung enthalten sind.|
|**Regeln anzeigen, die Codeanalysefehler generieren können**|Anzeigen oder ausblenden Regeln, die die Fehleraktion zugewiesen sind.|
|**Regeln anzeigen, die codeanalysewarnungen generieren können**|Anzeigen oder ausblenden Regeln, die die Warnaktion zugewiesen sind.|
|**Regeln anzeigen, die nicht aktiviert sind**|Blendet oder Regeln, die keine zugewiesen sind Aktion.|
|**Hinzufügen oder Entfernen von untergeordnete Regelsätze**|Fügt oder die Regeln in der ausgewählten Regelsätze entfernt.|
|**Search-Regeln**|Sucht alle Feldwerte für die Zeichenfolge, die Sie angeben.|

## <a name="rule-set-fields"></a>Regelsatz-Felder

Regel Satz Felder zeigen Informationen über einen Regelsatz und zu sortieren und Gruppieren der Regelliste verwendet werden können. Wählen Sie zum Anzeigen oder Ausblenden von Feldern, **Spaltenoptionen** für die Regel-Editor-Symbolleiste, und überprüfen Sie dann aktivieren bzw. deaktivieren die Kontrollkästchen der Felder, die ein- oder auszublenden.

Die folgende Tabelle beschreibt die Felder des einen Regelsatzes an:

|Feld|Beschreibung|
|-----------|-----------------|
|**ID**|Der Bezeichner der Regel.|
|**Kategorie**|Zusätzlich zu ihrer Zugehörigkeit zu Regelsätzen werden Codeanalyseregeln auch nach Kategorien gruppiert. Weitere Informationen finden Sie unter [Codeanalysewarnungen](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Name**|Der Titel der Regel.|
|**Namespace**|Der Namespace der Regel.|
|**Zieltyp**|Gibt an, ob die Regel für systemeigenen ist, verwaltet oder Datenbankcode.|
|**Aktion**|Die Aktion ausgeführt, wenn gegen diese Regel in der Ausführung einer Codeanalyse verstoßen wird. Sie können Bearbeiten der **Aktion** Feld.|
|**Source-Regelsätze**|Der Regelsatz, der die Regel enthält.|

## <a name="sort-and-filter-rule-sets"></a>Sortieren und Filtern von Regelsätzen

Über die Spaltenheader des Rasters Regel festlegen können Sie sortiert und die Regeln filtern, indem Sie die Werte des Felds.

- Um die Regel Set-Listen zu sortieren, klicken Sie auf die Spaltenüberschrift des Felds, nach dem sortiert werden soll. Wenn die Regelsätze gruppiert werden, wird jede Gruppe einzeln sortiert.

- Um die Regelsätze durch den Wert eines Felds zu filtern, klicken Sie auf die Filterschaltfläche auf die Spaltenüberschrift des Felds, nach denen Sie filtern möchten. Wählen Sie die Kontrollkästchen für die Werte, die Sie anzeigen möchten, und deaktivieren Sie die Kontrollkästchen für die Werte, die Sie ausblenden möchten.

## <a name="see-also"></a>Siehe auch

- [Erstellen eines benutzerdefinierten Regelsatzes](../code-quality/how-to-create-a-custom-rule-set.md)