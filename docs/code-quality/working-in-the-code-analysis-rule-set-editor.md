---
title: In der Regel zur Codeanalyse Workingsets Editor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c832b29512bfd7339ab60044ece81f1626be9bc7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Arbeiten mit dem Regelsatz-Editor für die Codeanalyse
Die Codeanalyse Regelsatz-Editor können Sie die Regeln an, die in einem benutzerdefinierten Regelsatz enthalten sind und die Aktion an. Sie können auch angeben, dass die Aktion an, bei der Codeanalyse einen Verstoß gegen diese Regel erkennt.  
  
|Aktion|Beschreibung|  
|------------|-----------------|  
|**Warnung**|Generiert eine Warnung in der **Fehlerliste** Fenster.|  
|**Fehler**|Generiert einen Fehler in der **Fehlerliste** Fenster.|  
|**Keine**|Deaktiviert die Regel.|  
  
 Der Editor zeigt die Regeln in einer Baumstruktur, die Gruppen der Regeln nach Feld festlegen, die Sie angeben. Zum Hinzufügen oder Entfernen von Regeln aus einem Regelsatz, können führen Sie eine oder mehrere der folgenden Schritte aus:  
  
-   Aktivieren Sie oder deaktivieren Sie das Kontrollkästchen für den Gruppenknoten hinzufügen oder entfernen alle Regeln in der Gruppe. Wenn Sie eine Gruppe auswählen, werden alle Regeln festgelegt, dass Sie die **Warnung** Aktion.  
  
-   Klicken Sie auf die **Aktion** Feld einer Gruppe, und geben Sie dann die Aktion für alle Regeln in der Gruppe angewendet.  
  
-   Aktivieren Sie oder deaktivieren Sie das Kontrollkästchen für eine einzelne Regel. Wenn Sie das Kontrollkästchen für eine Regel auswählen, wird die Regel auf die Warnaktion festgelegt.  
  
## <a name="rule-set-editor-toolbar"></a>Regelsatz-Editor-Symbolleiste  
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
  
## <a name="rule-set-fields"></a>Regel-Set-Felder  
 Regelsatz Felder Anzeigeinformationen zu einer Regel festlegen und zu sortieren und Gruppieren der Regelliste verwendet werden kann. Klicken Sie zum Anzeigen oder Ausblenden von Feldern, die auf **Spaltenoptionen** für die Regel-Editor-Symbolleiste, und überprüfen Sie dann aktivieren bzw. deaktivieren die Kontrollkästchen der Felder, die ein- oder auszublenden.  
  
 Die folgende Tabelle beschreibt die Felder des einen Regelsatzes.  
  
|Feld|Beschreibung|  
|-----------|-----------------|  
|**ID**|Der Bezeichner der Regel.|  
|**Kategorie**|Zusätzlich zu ihrer Zugehörigkeit zu Regelsätzen werden Codeanalyseregeln auch nach Kategorien gruppiert. Weitere Informationen finden Sie unter [Codeanalyse für verwalteten Code (Warnungen)](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Name**|Der Titel der Regel.|  
|**Namespace**|Der Namespace der Regel.|  
|**Zieltyp**|Gibt an, ob die Regel für systemeigenen ist, verwaltet oder Datenbankcode.|  
|**Aktion**|Die Aktion ausgeführt, wenn gegen diese Regel in der Ausführung einer Codeanalyse verstoßen wird.<br /><br /> **Warnung** -wird eine Warnung generiert.<br /><br /> **Fehler beim** -generiert einen Fehler.<br /><br /> **Keine** -deaktiviert die Regel.<br /><br /> Sie können das Aktionsfeld bearbeiten. Festlegen des Werts auf None entspricht dem Deaktivieren des Kontrollkästchens für die Regel.|  
|**Source-Regelsätze**|Der Regelsatz, der die Regel enthält.|  
  
## <a name="sorting-and-filtering-rule-sets"></a>Sortieren und Filtern von Regelsätzen  
 Über die Spaltenheader des Rasters Regel festlegen können Sie sortiert und die Regeln filtern, indem Sie die Werte des Felds.  
  
-   Um die Regel Set-Listen zu sortieren, klicken Sie auf die Spaltenüberschrift des Felds, nach dem sortiert werden soll. Wenn die Regelsätze gruppiert werden, wird jede Gruppe einzeln sortiert.  
  
-   Um die Regelsätze durch den Wert eines Felds zu filtern, klicken Sie auf die Filterschaltfläche auf die Spaltenüberschrift des Felds, nach denen Sie filtern möchten. Wählen Sie die Kontrollkästchen für die Werte, die Sie anzeigen möchten, und deaktivieren Sie die Kontrollkästchen für die Werte, die Sie ausblenden möchten.