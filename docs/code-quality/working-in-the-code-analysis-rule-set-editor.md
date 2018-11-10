---
title: Verwenden Sie die Codeanalyse-Regelsätze-Editor festgelegt.
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: bdd80031530049b204c0befc445c1416aa08b43e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000815"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Verwenden Sie den Code Analysis Regelsatz-editor

Legen Sie die Codeanalyse-Regelsätze Editor können, die Sie die Regeln angeben, die in einer benutzerdefinierten Regel festgelegt, und legen Sie den Schweregrad von Regelverstößen enthalten sind.

Die folgende Tabelle zeigt die Schweregrad-Optionen:

|Aktion (Schweregrad)|Beschreibung|
|-|-|
|Warnung|Generiert eine Warnung in der **Fehlerliste** und auch zum Zeitpunkt der Erstellung.|
|Fehler|Generiert einen Fehler in der **Fehlerliste** und auch zum Zeitpunkt der Erstellung.|
|Info|Generiert eine Nachricht in die **Fehlerliste**.|
|Hidden|Die Verletzung ist nicht für den Benutzer sichtbar. Die IDE wird die Verletzung jedoch informiert.|
|Keiner|Die Regel unterdrückt wird. Das Verhalten ist dasselbe, als ob die Regel aus dem Regelsatz entfernt wurde.|

Der Editor zeigt die Regeln in einer Baumstruktur, die Gruppen, die Regeln durch eine Regel Feld festlegen, die Sie angeben. Führen Sie zum Hinzufügen oder Entfernen von Regeln in einem Regelsatz, eine oder mehrere der folgenden Schritte aus:

- Aktivieren Sie oder deaktivieren Sie das Kontrollkästchen für den Gruppenknoten hinzufügen oder entfernen alle Regeln in der Gruppe. Wenn Sie eine Gruppe auswählen, werden alle Regeln festgelegt, um die **Warnung** Aktion.

   > [!TIP]
   > Sie können ändern, wie Regeln gruppiert werden, in der **Group by-** Dropdown-Liste.

- Klicken Sie auf die **Aktion** Feld eine Gruppe, und geben Sie dann die Aktion, die für alle Regeln in der Gruppe gelten.

- Aktivieren Sie oder deaktivieren Sie das Kontrollkästchen für eine einzelne Regel. Wenn Sie das Kontrollkästchen für eine Regel auswählen, wird die Regel auf die Warnaktion festgelegt.

## <a name="toolbar"></a>Symbolleiste

Sie können die Symbolleiste des Regelsatz-Editor verwenden, zu gruppieren, Filtern und suchen die angezeigten Daten in der Regel Set-Raster.

In der folgende Tabelle werden die Steuerelemente auf der Symbolleiste des Regelsatz-Editor beschrieben.

|ToolBar-Steuerelement|Beschreibung|
|---------------------|-----------------|
|**Alle erweitern**|Die Regeln in allen Gruppen angezeigt.|
|**Alle reduzieren**|Blendet die Regeln in allen Gruppen an.|
|**Group By**|Gibt das Feld, nach dem Regeln gruppiert werden. Klicken Sie auf  **\<None >** ohne Gruppen angezeigt.|
|**Spaltenoptionen**|Gibt die Regelfelder angezeigt werden sollen.|
|**Ausblenden von Regeln, die nicht für die aktuelle Projektmappe gelten**|Anzeigen oder Ausblenden von Regeln, die nicht von den gleichen Zieltyp wie die Lösung sind.|
|**Regeln anzeigen, die Codeanalysefehler generieren können**|Anzeigen oder Ausblenden von Regeln, die die Fehleraktion zugewiesen sind.|
|**Regeln anzeigen, die codeanalysewarnungen generieren können**|Anzeigen oder Ausblenden von Regeln, die die Warnaktion zugewiesen ist.|
|**Regeln anzeigen, die nicht aktiviert sind**|Anzeigen oder Ausblenden von Regeln, die die keine zugewiesen sind Aktion.|
|**Fügen Sie hinzu oder entfernen Sie untergeordnete Regelsätze**|Fügt oder die Regeln in den Sätzen für die ausgewählte Regel entfernt.|
|**Suchregeln**|Sucht alle Feldwerte für die Zeichenfolge, die Sie angeben.|

## <a name="rule-set-fields"></a>Regelsatz-Felder

Regel Satz Felder anzeigen von Informationen zu einem Regelsatz und können zu sortieren und gruppieren Sie die Regelliste verwendet werden. Wählen Sie zum Anzeigen oder Ausblenden von Feldern, **Spaltenoptionen** in der Regel legen Sie die Symbolleiste des Editors, und klicken Sie dann überprüfen, oder deaktivieren Sie die Kontrollkästchen für die Felder angezeigt oder ausgeblendet.

Die folgende Tabelle beschreibt die Felder des einen Regelsatzes an:

|Feld|Beschreibung|
|-----------|-----------------|
|**ID**|Der Bezeichner der Regel.|
|**Kategorie**|Zusätzlich zu ihrer Mitgliedschaft in Regelsätzen werden die Regeln für die Codeanalyse auch nach Kategorien gruppiert. Weitere Informationen finden Sie unter [Codeanalysewarnungen](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Name**|Der Titel der Regel.|
|**Namespace**|Der Namespace der Regel.|
|**Zieltyp**|Gibt an, ob die Regel für Native ist, verwaltet oder die Datenbank-Code.|
|**Aktion**|Die Aktion ausgeführt, wenn gegen diese Regel in der Ausführung einer Codeanalyse verstoßen wird. Sie können Bearbeiten der **Aktion** Feld.|
|**Quellregelsätze**|Der Regelsatz, der die Regel enthält.|

## <a name="sort-and-filter-rule-sets"></a>Sortieren und Filtern von Regelsätzen

Über die Spaltenüberschriften des Rasters Satz Regel können Sie sortieren und die Regeln filtern, indem Sie die Werte des Felds.

- Um die Listen der Regel-Satz zu sortieren, klicken Sie auf die Spaltenüberschrift des Felds, nach der sortiert werden sollen. Wenn die Regelsätze gruppiert werden, wird jede Gruppe einzeln sortiert.

- Um die Regelsätze durch den Wert eines Felds zu filtern, klicken Sie auf die Schaltfläche "Filter" auf die Spaltenüberschrift des Felds mit dem Sie filtern möchten. Wählen Sie die Kontrollkästchen für die Werte, die Sie anzeigen möchten, und deaktivieren Sie die Kontrollkästchen für die Werte, die Sie ausblenden möchten.

## <a name="see-also"></a>Siehe auch

- [Erstellen eines benutzerdefinierten Regelsatzes](../code-quality/how-to-create-a-custom-rule-set.md)