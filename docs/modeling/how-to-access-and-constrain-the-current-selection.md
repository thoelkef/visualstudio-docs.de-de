---
title: 'Vorgehensweise: Zugreifen auf die und Einschränken der aktuellen Auswahl'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb3ef158bafa172736f53898ea60b860c44dd77a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945325"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Vorgehensweise: Zugreifen auf die und Einschränken der aktuellen Auswahl

Wenn Sie einen Menübefehl oder Gestenhandler-Handler für die domänenspezifische Sprache schreiben, können Sie bestimmen, welches Element der Benutzer mit der rechten Maustaste. Sie können auch einige Formen oder Felder verhindern ausgewählt werden. Sie können z. B. anordnen, dass klickt der Benutzer ein Symbol für Decorator-Element, Form, die es enthält stattdessen ausgewählt ist. Die Auswahl auf diese Weise einschränken, reduziert die Anzahl von Handlern, die Sie schreiben müssen. Es erleichtert auch für den Benutzer, die an einer beliebigen Stelle in der Form klicken kann, ohne das Decorator-Element zu vermeiden.

## <a name="access-the-current-selection-from-a-command-handler"></a>Zugriff auf die aktuelle Auswahl aus einem Befehlshandler

Befehl Set-Klasse für eine domänenspezifische Sprache enthält, die Befehlshandler für Ihre benutzerdefinierten Befehle. Die <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> -Klasse, von dem Befehl Set-Klasse für eine domänenspezifische Sprache abgeleitet wird, stellt einige Member, für den Zugriff auf die aktuelle Auswahl.

Je nach den Befehl ein möglicherweise der Befehlshandler die Auswahl im Modell-Designer, Modell-Explorer oder des aktiven Fensters.

### <a name="to-access-selection-information"></a>Zugriff auf Auswahlinformationen

1.  Die <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> -Klasse definiert die folgenden Elemente, die auf die aktuelle Auswahl verwendet werden können.

    |Member|Beschreibung|
    |-|-|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>-Methode|Gibt `true` Wenn einer der ausgewählten Elemente in den Modell-Designer eine Depot-Form; anderenfalls `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>-Methode|Gibt `true` ist das Diagramm im Modell-Designer; andernfalls `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>-Methode|Gibt `true` ist genau ein Element im Modell-Designer; andernfalls `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>-Methode|Gibt `true` ist genau ein Element im aktiven Fenster; andernfalls `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> -Eigenschaft|Ruft eine schreibgeschützte Auflistung der im Modell-Designer ausgewählten Elemente ab.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> -Eigenschaft|Ruft eine schreibgeschützte Auflistung der ausgewählten Elemente in das aktive Fenster ab.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> -Eigenschaft|Ruft das primäre Element der Auswahl im Modell-Designer ab.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> -Eigenschaft|Ruft das primäre Element der Auswahl in das aktive Fenster ab.|

2.  Die <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> Eigenschaft der <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasse ermöglicht den Zugriff auf die <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> Objekt, das das Modell-Designer-Fenster, und bietet zusätzlichen Zugriff die ausgewählten Elemente im Modell-Designer.

3.  Darüber hinaus der generierte Code definiert eine Explorer-Tool-Fenster-Eigenschaft und eine Explorer-Auswahl-Eigenschaft im Befehl set-Klasse für die domänenspezifischen Sprache.

    -   Die Explorer-Tool Window-Eigenschaft gibt eine Instanz der Explorer-Tool Window-Klasse für die domänenspezifischen Sprache zurück. Explorer-Tool Window-Klasse leitet sich von der <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> Klasse und den Modell-Explorer für die domänenspezifischen Sprache darstellt.

    -   Die `ExplorerSelection` Eigenschaft gibt das ausgewählte Element im Modell-Explorer-Fenster für die domänenspezifischen Sprache zurück.

## <a name="determine-which-window-is-active"></a>Bestimmen Sie, welches Fenster aktiv ist.

Die <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> enthält Schnittstelle definiert Member, die Zugriff auf den aktuellen Auswahlzustand in der Shell ermöglichen. Erhalten Sie eine <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Objekt von der Paketklasse oder der festgelegten Klasse des Befehls für die domänenspezifischen Sprache über die `MonitorSelection` -Eigenschaft in der Basisklasse aller definiert. Die Paketklasse leitet sich von der <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> Klasse und den Befehl Set-Klasse leitet sich von der <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasse.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Um aus einem Befehlshandler zu bestimmen, welche Art von Fenster aktiv ist

1.  Die <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> Eigenschaft der <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> -Klasse zurückgegeben wird ein <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Objekt, das Zugriff auf den aktuellen Auswahlzustand in der Shell bereitstellt.

2.  Die <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> Eigenschaft der <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Schnittstelle ruft aktive Auswahl Containers, in dem aus dem aktiven Fenster unterschiedlich sein kann.

3.  Fügen Sie, dass die folgenden Eigenschaften an den Befehl Klasse für Sie festgelegt einer domänenspezifischen Sprache, um zu bestimmen, welche Art von Fenster aktiv ist.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>Einschränken der Auswahl

Durch Auswahlregeln hinzufügen, können Sie steuern, welche Elemente ausgewählt sind, wenn der Benutzer ein Element im Modell auswählt. Damit wird den Benutzer, eine Anzahl von Elementen als einzelne Einheit behandelt werden sollen, können Sie z. B. eine Auswahlregel verwenden.

### <a name="to-create-a-selection-rule"></a>Zum Erstellen einer Auswahlregel

1.  Erstellen einer benutzerdefinierten Codedatei im DSL-Projekt

2.  Definieren Sie eine Auswahl Regel abgeleitete Klasse, aus der <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> Klasse.

3.  Überschreiben der <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> -Methode der Klasse Regel Auswahl die Auswahlkriterien anwenden.

4.  Fügen Sie eine partielle Klassendefinition für die ClassDiagram-Klasse in die benutzerdefinierte Codedatei hinzu.

     Die `ClassDiagram` Klasse leitet sich von der <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> Klasse, und klicken Sie in der generierten Codedatei Diagram.cs, im DSL-Projekt definiert ist.

5.  Überschreiben der <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> Eigenschaft der `ClassDiagram` Klasse, um die Regel für die benutzerdefinierte Auswahl zurück.

     Die standardmäßige Implementierung der <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> -Eigenschaft ruft ein Auswahlobjekt für die Regel, die nicht über die Auswahl ändert.

### <a name="example"></a>Beispiel

Die folgende Codedatei erstellt eine Auswahlregel, die erweitert die Auswahl enthält alle Instanzen der einzelnen Domäne Formen, die ursprünglich ausgewählt wurde.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>