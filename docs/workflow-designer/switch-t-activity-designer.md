---
title: "Switch&lt;T&gt; Aktivitäts-Designer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: "3"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 69e69ca7453801d6ccc3b5f323035475413721c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="switchlttgt-activity-designer"></a>Switch&lt;T&gt; Aktivitäts-Designer
Die <xref:System.Activities.Statements.Switch%601>-Aktivität wertet einen angegebenen Ausdruck aus und führt diejenige Aktivität aus einer Auflistung von Aktivitäten aus, deren zugeordneter Schlüssel dem Wert entspricht, der aus der Auswertung hervorging.  
  
 Die **Switch < T\>**  Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Switch%601> Aktivität in der [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
## <a name="the-switchtactivity"></a>Der Schalter\<T >-Aktivität  
 Eine <xref:System.Activities.Statements.Switch%601>-Aktivität enthält einen <xref:System.Activities.Statements.Switch%601.Expression%2A>-Ausdruck und ein Wörterbuch von <xref:System.Activities.Statements.Switch%601.Cases%2A>-Fällen. Jeder Fall im Wörterbuch besteht aus einem Paar, enthält eine *Schlüssel* und eine Aktivität, die als das entsprechende dient *Wert*. Die <xref:System.Activities.Statements.Switch%601>-Aktivität wertet den <xref:System.Activities.Statements.Switch%601.Expression%2A>-Ausdruck aus und vergleicht ihn mit jedem Schlüssel. Wenn eine Übereinstimmung gefunden wird, wird die entsprechende Aktivität ausgeführt. Nur eine Übereinstimmung ist möglich, da die Wörterbuchschlüssel entsprechend der vom Gleichheitsvergleich des Wörterbuchs definierten Gleichheit eindeutig sein müssen. Wenn keine Übereinstimmung gefunden wird, wird die <xref:System.Activities.Statements.Switch%601.Default%2A>-Aktivität ausgeführt.  
  
## <a name="how-to-use-the-switcht-activity-designer"></a>Gewusst wie: Verwenden Sie den Switch\<T >-Aktivitätsdesigners  
 Die **Switch\<T >** Aktivitäts-Designer finden Sie in der **Control Flow** Kategorie von der **Toolbox**, indem Sie auf die zugegriffenwird**Toolbox** Registerkarte der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.) Nach dem löschen ihn in die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], zeigt der **Typen auswählen** Dialogfeld ermöglichen den Benutzer den generischen Typ angeben *T* verwendet <xref:System.Activities.Statements.Switch%601> Aktivität. Der Standardwert ist **Int32**. Sobald der generische Typ *T* ausgewählt wurde, eine **Switch < T\>**  -Designer in den Workflowdesigner hinzugefügt wird.  
  
 Nachfolgend werden die Eigenschaften des **Switch < T\>**  Designer. Alle diese Eigenschaften können im Eigenschaftenraster bearbeitet werden. Einige von ihnen können auch in der Designeroberfläche bearbeitet werden.  
  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.Switch%601>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen des <xref:System.Activities.Statements.Switch%601>-Aktivitätsdesigners an. Der Standardwert ist Switch < Int32\>. Der Wert kann bearbeitet werden, der **Eigenschaften** Fenster oder direkt im Header Designers.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|Gibt den Ausdruck an, mit dem die Schlüssel in der Auflistung der Fälle verglichen wurden, um zu bestimmen, welcher Fall auszuführen ist.|  
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Gibt die Aktivität an, die ausgeführt werden soll, wenn keine Übereinstimmung gefunden wird. Klicken Sie auf die **Hinzufügen einer Aktivität** Designer auf die Schaltfläche zum Öffnen der **Standard** Feld, in dem die Aktivität abgelegt werden kann.|  
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Gibt die Fälle an, die ausgewertet werden sollen. Um einen Fall hinzuzufügen, klicken Sie auf die **Hinzufügen von neuen Fall** Schaltfläche am unteren Rand **Switch\<T >** Designer. Die Schaltfläche ändert sich in ein Textfeld (Kombinationsfeld, wenn der generische Typ ausgewählt, wenn Sie den Switch hinzufügen\<T > String oder Enum ist). Nach dem Hinzufügen eines Schlüssels in der **Case-Wert** Box der Case-Bereich erweitert und eine Aktivität abgelegt werden kann, wo der Hinweistext "Aktivität hier ablegen", um die Ausführungslogik für den Fall zu definieren.|  
  
 Solange keine doppelten Fallschlüssel vorkommen, können mehrere Fälle hinzugefügt werden. Andernfalls wird ein Fehlerdialogfeld mit der Meldung angezeigt, dass der angegebene Fallschlüssel bereits vorhanden ist und dass Sie einen anderen Schlüssel auswählen müssen. In der **Switch\<T >** -Designer mehrere Case-Bereiche kann in der erweiterten Ansicht zu einem Zeitpunkt werden. Wenn ein case-Bereich reduziert angezeigt wird, klicken Sie auf den case-Bereich, um ihn zu erweitern. Beachten Sie, dass der Designer bei einem reduzierten case-Bereich den Anzeigenamen der Aktivität rechts neben dem Bereich anzeigt, sofern eine Aktivität vorhanden ist. Andernfalls zeigt der **Hinzufügen einer Aktivität** Schaltfläche, die die Groß-/Kleinschreibung wird erweitert, wenn Sie darauf klicken und Sie können eine Aktivität hinzuzufügen.  
  
 Wenn Sie auf den Schlüssel eines vorhandenen Falls klicken, wird der Schlüssel von einer Bezeichnung in ein Textfeld geändert, damit Sie den Fallschlüssel bearbeiten können.  
  
 Es gibt zwei Möglichkeiten, einen Fall zu löschen:  
  
1.  Wählen Sie den Fall aus, und löschen Sie ihn.  
  
2.  Wählen Sie die Groß-/Kleinschreibung, mit der rechten Maustaste auf das Kontextmenü anzuzeigen, und wählen Sie **löschen**.  
  
 Beachten Sie, dass Sie den Fall selbst markieren müssen, um ihn zu löschen. Wenn Sie die Aktivität in einem Fall markieren und löschen, wird nur Aktivität, nicht der Fall gelöscht.  
  
## <a name="see-also"></a>Siehe auch  
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)