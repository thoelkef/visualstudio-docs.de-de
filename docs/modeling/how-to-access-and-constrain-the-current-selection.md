---
title: "Gewusst wie: Zugreifen auf die und Einschr&#228;nken der aktuellen Auswahl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Zugreifen auf die aktuelle Auswahl"
ms.assetid: 2990981e-dfae-416f-b0d0-7197f1242dfa
caps.latest.revision: 14
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 14
---
# Gewusst wie: Zugreifen auf die und Einschr&#228;nken der aktuellen Auswahl
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie einen Menübefehl oder Gestenhandler\-Handler für Ihre domänenspezifische Sprache schreiben, können Sie bestimmen, welches Element der Benutzer mit der rechten Maustaste. Sie können auch einige Formen oder Felder verhindern ausgewählt werden. Sie können z. B. anordnen, klickt der Benutzer auf ein Symbol Decorator, Form, die es enthält stattdessen ausgewählt ist. Beschränken die Auswahl auf diese Weise reduziert die Anzahl der Handler, die Sie schreiben müssen. Es erleichtert auch für den Benutzer, die an einer beliebigen Stelle in der Form klicken kann, ohne Decorator\-Elements zu vermeiden.  
  
## Zugriff auf die aktuelle Auswahl aus einen Befehlshandler  
 Der Befehl Set\-Klasse für eine domänenspezifische Sprache enthält die Befehlshandler für Ihre benutzerdefinierte Befehle. Die <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> \-Klasse, von der festgelegten Klasse des Befehls für eine domänenspezifische Sprache abgeleitet wird, stellt einige Member für den Zugriff auf die aktuelle Auswahl.  
  
 Je nach dem Befehl möglicherweise Befehlshandler die Auswahl im Modell\-Designer, Modell\-Explorer oder das aktive Fenster.  
  
#### Zugriff auf Auswahlinformationen  
  
1.  Die <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> \-Klasse definiert die folgenden Elemente, die zum Zugriff auf die aktuelle Auswahl verwendet werden können.  
  
    |Member|Beschreibung|  
    |------------|------------------|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>\-Methode|Gibt `true` ist eines der Elemente im Modelldesigner aktiviert eine Depot\-Form; anderenfalls `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>\-Methode|Gibt `true` ist das Diagramm im Modell\-Designer ausgewählt ist, andernfalls `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>\-Methode|Gibt `true` ist genau ein Element im Modell\-Designer ausgewählt ist, andernfalls `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>\-Methode|Gibt `true` ist genau ein Element in das aktive Fenster ausgewählt ist, andernfalls `false`.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>\-Eigenschaft|Ruft eine schreibgeschützte Auflistung der Elemente im Modell\-Designer ausgewählt.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>\-Eigenschaft|Ruft eine schreibgeschützte Auflistung der Elemente im aktiven Fenster ausgewählt.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>\-Eigenschaft|Ruft das primäre Element der Auswahl im Modell\-Designer.|  
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>\-Eigenschaft|Ruft das primäre Element der Auswahl im aktiven Fenster ab.|  
  
2.  Die <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> Eigenschaft der <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> \-Klasse bietet Zugriff auf die <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> Objekt, das das Modell\-Designer\-Fenster und stellt zusätzliche Zugriffsberechtigungen die ausgewählten Elemente im Modell\-Designer.  
  
3.  Darüber hinaus der generierte Code definiert eine Explorer\-Tool\-Fenster\-Eigenschaft und eine Explorer\-Auswahl\-Eigenschaft im Befehl set\-Klasse für die domänenspezifischen Sprache.  
  
    -   Die Explorer\-Fenster\-Eigenschaft gibt eine Instanz der Explorer\-Tool Window\-Klasse für die domänenspezifischen Sprache. Explorer\-Tool Window\-Klasse leitet sich von der <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> \-Klasse und den Modell\-Explorer für die domänenspezifischen Sprache darstellt.  
  
    -   Die `ExplorerSelection` \-Eigenschaft gibt das ausgewählte Element im Modell\-Explorer\-Fenster für die domänenspezifischen Sprache zurück.  
  
## Bestimmen, welches Fenster aktiv ist.  
 Die <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> enthält Schnittstelle definiert Member, die Zugriff auf den aktuellen Status der Auswahl in der Shell ermöglichen. Erhalten Sie ein <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Objekt aus der Klasse oder den Befehl Set\-Klasse für die domänenspezifischen Sprache über die `MonitorSelection` \-Eigenschaft in der Basisklasse aller definiert. Die\-Klasse leitet sich von der <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> \-Klasse und den Befehl Set\-Klasse leitet sich von der <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasse.  
  
#### Um von einen Befehlshandler zu bestimmen, welche Art von Fenster aktiv ist.  
  
1.  Die <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> Eigenschaft der <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> \-Klasse zurückgegeben wird ein <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> \-Objekt, das Zugriff auf den aktuellen Status der Auswahl in der Shell.  
  
2.  Die <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> Eigenschaft der <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Schnittstelle ruft die aktive Auswahl\-Container, der aus dem aktiven Fenster unterschiedlich sein kann.  
  
3.  Fügen Sie die folgenden Eigenschaften für den Befehl Klasse für Sie festgelegt domänenspezifische Sprache zu bestimmen, welche Art von Fenster aktiv ist.  
  
    ```c#  
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
  
## Einschränken der Auswahl  
 Durch Auswahlregeln hinzufügen, können Sie steuern, welche Elemente ausgewählt sind, wenn der Benutzer ein Element im Modell auswählt. Wenn der Benutzer eine Anzahl von Elementen als eine Einheit behandeln kann, können Sie z. B. eine Auswahlregel verwenden.  
  
#### Erstellen eine Auswahlregel  
  
1.  Erstellen Sie eine benutzerdefinierte Codedatei im DSL\-Projekt  
  
2.  Definieren Sie eine Auswahl Regel\-Klasse, die von abgeleitet ist die <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> Klasse.  
  
3.  Überschreiben Sie die <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> \-Methode der Klasse Regel Auswahl der Kriterien für die Auswahl anwenden.  
  
4.  Fügen Sie eine partielle Klassendefinition für die ClassDiagram\-Klasse in die benutzerdefinierte Codedatei hinzu.  
  
     Die `ClassDiagram` Klasse leitet sich von der <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> \-Klasse und in der generierten Codedatei Diagram.cs, im DSL\-Projekt definiert ist.  
  
5.  Überschreiben der <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> Eigenschaft der `ClassDiagram` \-Klasse die benutzerdefinierten Auswahlregel zurückgegeben.  
  
     Die standardmäßige Implementierung der von der <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> Eigenschaft ruft ein Auswahlobjekt für die Regel, die nicht die Auswahl ändert.  
  
### Beispiel  
 Die folgende Codedatei erstellt eine Auswahlregel, die erweitert die Auswahl auf alle Instanzen der einzelnen Domäne Formen, die ursprünglich ausgewählt wurde.  
  
```c#  
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
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>