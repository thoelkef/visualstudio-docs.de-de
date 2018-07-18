---
title: 'Gewusst wie: Zugreifen auf die und Einschränken der aktuellen Auswahl'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5d8fb0a2e5d218b76e972fc97a53afcd2f8ef3e6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31952361"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Gewusst wie: Zugreifen auf die und Einschränken der aktuellen Auswahl

Wenn Sie einen Menübefehl oder Gestenhandler-Handler für Ihre einer domänenspezifischen Sprache schreiben, können Sie bestimmen, welches Element der Benutzer geklickt wird. Sie können auch einige Formen oder Felder verhindern ausgewählt werden. Sie können z. B. anordnen, dass klickt der Benutzer auf ein Symbol Decorator-Element, das Shape, das sie enthält stattdessen ausgewählt ist. Beschränken die Auswahl auf diese Weise reduziert die Anzahl der Handler, die Sie schreiben müssen. Dies erleichtert auch für die Benutzer an einer beliebigen Stelle in der Form klicken kann, ohne die Decorator-Element zu vermeiden.

## <a name="access-the-current-selection-from-a-command-handler"></a>Zugriff auf die aktuelle Auswahl aus Befehlshandler

Der Befehl Set-Klasse für eine domänenspezifische Sprache enthält die Befehlshandler für Ihre benutzerdefinierte Befehle. Die <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasse, von dem Befehl Set-Klasse für eine domänenspezifische Sprache abgeleitet ist, stellt einige Member, für den Zugriff auf die aktuelle Auswahl.

Je nach den Befehl möglicherweise Befehlshandler die Auswahl im Modell-Designer, Modell-Explorer oder des aktiven Fensters.

### <a name="to-access-selection-information"></a>Zugriff auf Auswahlinformationen

1.  Die <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasse definiert die folgenden Elemente, die auf die aktuelle Auswahl verwendet werden können.

    |Member|Beschreibung|
    |------------|-----------------|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>-Methode|Gibt `true` ist eines der Elemente im Modell-Designer ausgewählte Depot-Form; anderenfalls `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>-Methode|Gibt `true` ist das Diagramm im Modell-Designer ausgewählt ist, andernfalls `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>-Methode|Gibt `true` ist genau ein Element im Modell-Designer ausgewählt ist, andernfalls `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>-Methode|Gibt `true` ist genau ein Element im aktiven Fenster ausgewählt ist, andernfalls `false`.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>-Eigenschaft|Ruft eine schreibgeschützte Auflistung der Elemente im Modell-Designer ausgewählt.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>-Eigenschaft|Ruft eine schreibgeschützte Auflistung der Elemente im aktiven Fenster ausgewählt.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>-Eigenschaft|Ruft das primäre Element der Auswahl im Modell-Designer ab.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>-Eigenschaft|Ruft das primäre Element der Auswahl im aktiven Fenster ab.|

2.  Die <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> Eigenschaft von der <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasse ermöglicht den Zugriff auf die <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> -Objekt, das Modell-Designer-Fenster darstellt, und bietet zusätzliche Zugriff die ausgewählten Elemente im Modell-Designer.

3.  Darüber hinaus der generierte Code definiert eine Explorer-Tool-Fenster-Eigenschaft und eine auswahleigenschaft Explorer in den Befehl set-Klasse für die domänenspezifischen Sprache.

    -   Die Explorer-Tool-Fenster-Eigenschaft gibt eine Instanz der Fensterklasse Explorer-Tool für die domänenspezifischen Sprache. Die Explorer-Tool-Fensterklasse leitet sich von der <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> -Klasse und der Modell-Explorer für die domänenspezifischen Sprache darstellt.

    -   Die `ExplorerSelection` Eigenschaft gibt das ausgewählte Element im Modell-Explorer-Fenster für die domänenspezifischen Sprache.

## <a name="determine-which-window-is-active"></a>Bestimmen Sie, welches Fenster aktiv ist.

Die <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Schnittstelle enthält definiert Member, die Zugriff auf den aktuellen Status der Auswahl in der Shell zu ermöglichen. Sie erhalten ein <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Objekt aus der Paketklasse oder den Befehl Set-Klasse für die domänenspezifischen Sprache über die `MonitorSelection` in der Basisklasse der einzelnen definierte Eigenschaft. Paketklasse leitet sich von der <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> Klasse und den Befehl Set-Klasse leitet sich von der <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasse.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Um von einem Befehlshandler zu bestimmen, ist welche Art von Fenster aktiv

1.  Die <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> Eigenschaft von der <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> -Klasse zurückgegeben wird ein <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Objekt, das Zugriff auf den aktuellen Status der Auswahl in der Shell bereitstellt.

2.  Die <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> Eigenschaft von der <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Schnittstelle ruft die aktive Auswahl-Container aus dem aktiven Fenster unterschiedlich sein kann.

3.  Fügen Sie die folgenden Eigenschaften auf den Befehl "Class" für Sie festgelegt domänenspezifische Sprache, um zu bestimmen, welche Art von Fenster aktiv ist.

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

## <a name="constrain-the-selection"></a>Beschränken Sie die Auswahl

Durch Auswahlregeln hinzufügen, können Sie steuern, welche Elemente ausgewählt sind, wenn der Benutzer ein Element im Modell auswählt. Damit wird den Benutzer, eine Anzahl von Elementen als einzelne Einheit behandelt werden sollen, können Sie z. B. eine Auswahlregel verwenden.

### <a name="to-create-a-selection-rule"></a>Zum Erstellen einer Auswahlregel

1.  Erstellen Sie eine benutzerdefinierte Codedatei im Projekt DSL

2.  Definieren Sie eine Auswahl Regel-Klasse, die abgeleitet ist die <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> Klasse.

3.  Überschreiben Sie die <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> -Methode der Klasse Regel Auswahl anzuwendende die Auswahlkriterien festzulegen.

4.  Der benutzerdefinierte Codedatei eine partielle Klassendefinition für die ClassDiagram-Klasse hinzufügen.

     Die `ClassDiagram` Klasse leitet sich von der <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> -Klasse und in der generierten Codedatei Diagram.cs, in der DSL-Projekt definiert ist.

5.  Überschreiben der <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> Eigenschaft von der `ClassDiagram` Klasse, um die Regel für die benutzerdefinierte Auswahl zurück.

     Die standardmäßige Implementierung des der <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> Eigenschaft ruft eine Auswahl Rule-Objekt, das die Auswahl nicht ändert.

### <a name="example"></a>Beispiel

Die folgende Codedatei erstellt eine Auswahlregel, die erweitert die Auswahl, um alle Instanzen der einzelnen Domäne Formen, die ursprünglich ausgewählt wurde.

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