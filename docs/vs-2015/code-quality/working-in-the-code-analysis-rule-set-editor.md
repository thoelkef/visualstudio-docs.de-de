---
title: Legen Sie die Codeanalyse-Regelsätze arbeiten-Editor | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0dd83a2b2d613d6d9ef73097bca4d2f9f1c6cd39
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946757"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Arbeiten mit dem Regelsatz-Editor für die Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Codeanalyse Regelsatz-Editor können Sie zum Festlegen von Regeln, die in einem benutzerdefinierten Regelsätzen enthalten sind und die Aktion an. Sie können auch angeben, dass die Aktion an, bei der Codeanalyse einen Verstoß gegen die Regel auftritt.  
  
|Aktion|Beschreibung|  
|------------|-----------------|  
|**Warnung**|Generiert eine Warnung in der **Fehlerliste** Fenster.|  
|**Fehler**|Generiert einen Fehler in der **Fehlerliste** Fenster.|  
|**Keine**|Deaktiviert die Regel.|  
  
 Der Editor zeigt die Regeln in einer Baumstruktur, die Gruppen, die Regeln durch eine Regel Feld festlegen, die Sie angeben. Führen Sie zum Hinzufügen oder Entfernen von Regeln in einem Regelsatz, eine oder mehrere der folgenden Schritte aus:  
  
-   Aktivieren Sie oder deaktivieren Sie das Kontrollkästchen für den Gruppenknoten hinzufügen oder entfernen alle Regeln in der Gruppe. Wenn Sie eine Gruppe auswählen, werden alle Regeln festgelegt, um die **Warnung** Aktion.  
  
-   Klicken Sie auf die **Aktion** Feld eine Gruppe, und geben Sie dann die Aktion, die für alle Regeln in der Gruppe gelten.  
  
-   Aktivieren Sie oder deaktivieren Sie das Kontrollkästchen für eine einzelne Regel. Wenn Sie das Kontrollkästchen für eine Regel auswählen, wird die Regel auf die Warnaktion festgelegt.  
  
## <a name="rule-set-editor-toolbar"></a>Regelsatz-Editor-Symbolleiste  
 Sie können die Symbolleiste des Regelsatz-Editor verwenden, zu gruppieren, Filtern und suchen die angezeigten Daten in der Regel Set-Raster.  
  
 In der folgende Tabelle werden die Steuerelemente auf der Symbolleiste des Regelsatz-Editor beschrieben.  
  
|ToolBar-Steuerelement|Beschreibung|  
|---------------------|-----------------|  
|**Alle aufklappen**|Die Regeln in allen Gruppen angezeigt.|  
|**Alle reduzieren**|Blendet die Regeln in allen Gruppen an.|  
|**Group By**|Gibt das Feld, nach dem Regeln gruppiert werden. Klicken Sie auf  **\<None >** ohne Gruppen angezeigt.|  
|**Spaltenoptionen**|Gibt die Regelfelder angezeigt werden sollen.|  
|**Ausblenden von Regeln, die nicht für die aktuelle Projektmappe gelten**|Anzeigen oder Ausblenden von Regeln, die nicht von den gleichen Zieltyp wie die Lösung sind.|  
|**Regeln anzeigen, die Codeanalysefehler generieren können**|Anzeigen oder Ausblenden von Regeln, die die Fehleraktion zugewiesen sind.|  
|**Regeln anzeigen, die codeanalysewarnungen generieren können**|Anzeigen oder Ausblenden von Regeln, die die Warnaktion zugewiesen ist.|  
|**Regeln anzeigen, die nicht aktiviert sind**|Anzeigen oder Ausblenden von Regeln, die die keine zugewiesen sind Aktion.|  
|**Fügen Sie hinzu oder entfernen Sie untergeordnete Regelsätze**|Fügt oder die Regeln in den Sätzen für die ausgewählte Regel entfernt.|  
|**Suchregeln**|Sucht alle Feldwerte für die Zeichenfolge, die Sie angeben.|  
  
## <a name="rule-set-fields"></a>Set-Felder  
 Regelsatz-Felder, die von Anzeigeinformationen zu einer Regel festgelegt und kann zu sortieren und gruppieren Sie die Regelliste verwendet werden. Klicken Sie zum Anzeigen oder Ausblenden von Feldern, die auf **Spaltenoptionen** in der Regel legen Sie die Symbolleiste des Editors, und klicken Sie dann überprüfen, oder deaktivieren Sie die Kontrollkästchen für die Felder angezeigt oder ausgeblendet.  
  
 Die folgende Tabelle beschreibt die Felder eines Regelsatzes.  
  
|Feld|Beschreibung|  
|-----------|-----------------|  
|**ID**|Der Bezeichner der Regel.|  
|**Kategorie**|Zusätzlich zu ihrer Mitgliedschaft in Regelsätzen werden die Regeln für die Codeanalyse auch nach Kategorien gruppiert. Weitere Informationen finden Sie unter [Codeanalyse für verwalteten Code (Warnungen)](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Name**|Der Titel der Regel.|  
|**Namespace**|Der Namespace der Regel.|  
|**Zieltyp**|Gibt an, ob die Regel für Native ist, verwaltet oder die Datenbank-Code.|  
|**Aktion**|Die Aktion ausgeführt, wenn gegen diese Regel in der Ausführung einer Codeanalyse verstoßen wird.<br /><br /> **Warnung** – wird eine Warnung generiert.<br /><br /> **Fehler** -generiert einen Fehler.<br /><br /> **Keine** -deaktiviert die Regel.<br /><br /> Sie können das Aktionsfeld bearbeiten. Festlegen des Werts auf "None" ist identisch mit der Sie das Kontrollkästchen für die Regel deaktivieren.|  
|**Quellregelsätze**|Der Regelsatz, der die Regel enthält.|  
  
## <a name="sorting-and-filtering-rule-sets"></a>Sortieren und Filtern von Regelsätzen  
 Über die Spaltenüberschriften des Rasters Satz Regel können Sie sortieren und die Regeln filtern, indem Sie die Werte des Felds.  
  
-   Um die Listen der Regel-Satz zu sortieren, klicken Sie auf die Spaltenüberschrift des Felds, nach der sortiert werden sollen. Wenn die Regelsätze gruppiert werden, wird jede Gruppe einzeln sortiert.  
  
-   Um die Regelsätze durch den Wert eines Felds zu filtern, klicken Sie auf die Schaltfläche "Filter" auf die Spaltenüberschrift des Felds mit dem Sie filtern möchten. Wählen Sie die Kontrollkästchen für die Werte, die Sie anzeigen möchten, und deaktivieren Sie die Kontrollkästchen für die Werte, die Sie ausblenden möchten.
