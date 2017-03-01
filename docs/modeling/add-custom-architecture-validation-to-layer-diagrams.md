---
title: "Hinzufügen von benutzerdefinierten architekturvalidierung Abhängigkeitsdiagramme | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, adding custom validation
ms.assetid: fed7bc08-295a-46d6-9fd8-fb537f1f75f1
caps.latest.revision: 42
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 16702d78769037b693ddfc0a36ac62453e9b7115
ms.lasthandoff: 02/22/2017

---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Hinzufügen von benutzerdefinierten architekturvalidierung Abhängigkeitsdiagramme
In Visual Studio können Benutzer den Quellcode in einem Projekt anhand eines Ebenenmodells überprüfen, sodass sie überprüfen können, dass der Quellcode den Abhängigkeiten in einem Abhängigkeitsdiagramm entspricht. Es gibt zwar einen Standardvalidierungsalgorithmus, Sie können aber auch eigene Validierungserweiterungen definieren.  
  
 Wenn der Benutzer wählt die **Architektur überprüfen** Befehl in einem Abhängigkeitsdiagramm die Standardvalidierungsmethode aufgerufen, anschließend folgen alle, die installiert wurden.  
  
> [!NOTE]
>  Der Hauptzweck der Überprüfung werden in einem Abhängigkeitsdiagramm das Diagramm mit dem Programmcode in anderen Teilen der Projektmappe zu vergleichen.  
  
 Sie können die Ebenenvalidierungserweiterung in eine Visual Studio-Integrationserweiterung (VSIX) verpacken, die Sie an andere Visual Studio-Benutzer verteilen können. Sie können entweder das Validierungssteuerelement allein in eine VSIX einfügen, oder Sie können es in der gleichen VSIX mit anderen Erweiterungen kombinieren. Schreiben Sie den Code für das Validierungssteuerelement in einem eigenen Visual Studio-Projekt und nicht im gleichen Projekt wie andere Erweiterungen.  
  
> [!WARNING]
>  Nachdem Sie ein Überprüfungsprojekt erstellt haben, kopieren Sie den [Beispielcode](#example) am Ende dieses Themas und bearbeiten diesen dann Ihren Anforderungen entsprechend.  
  
## <a name="requirements"></a>Anforderungen  
 Finden Sie unter [Anforderungen](../modeling/extend-layer-diagrams.md#prereqs).  
  
## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Definieren eines Ebenenvalidierungssteuerelements in einer neuen VSIX  
 Projektvorlagen stellen die schnellste Methode dar, eine Validierungssteuerelement zu erstellen. Dabei werden der Code und die VSIX im selben Projekt platziert.  
  
#### <a name="to-define-an-extension-by-using-a-project-template"></a>So definieren Sie mithilfe einer Projektvorlage eine Erweiterung  
  
1.  Erstellen Sie in einer neuen Projektmappe ein Projekt. Verwenden Sie dazu den Befehl **Neues Projekt** im Menü **Datei** .  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt** unter **Modellierungsprojekte**auf **Layer Designer Validation Extension**(Ebenen-Designer - Validierungserweiterung).  
  
     Mit dieser Vorlage wird ein Projekt mit einem kleinen Beispiel erstellt.  
  
    > [!WARNING]
    >  Makethe Vorlage ordnungsgemäß arbeiten:  
    >   
    >  -   Bearbeiten Sie Aufrufe zu `LogValidationError` , um die optionalen Argumente `errorSourceNodes` und `errorTargetNodes`zu entfernen.  
    > -   Wenn Sie benutzerdefinierte Eigenschaften verwenden, wenden Sie das Update gemäß [Hinzufügen benutzerdefinierter Eigenschaften zu Abhängigkeitsdiagramme](../modeling/add-custom-properties-to-layer-diagrams.md).  
  
3.  Bearbeiten Sie den Code, um die Validierung zu definieren. Weitere Informationen finden Sie unter [Programmieren einer Validierung](#programming).  
  
4.  Weitere Informationen zum Testen der Erweiterung finden Sie unter [Debuggen der Ebenenvalidierung](#debugging).  
  
    > [!NOTE]
    >  Die Methode wird nur unter bestimmten Umständen aufgerufen, und Haltepunkte funktionieren nicht automatisch. Weitere Informationen finden Sie unter [Debuggen der Ebenenvalidierung](#debugging).  
  
5.  So installieren Sie die Erweiterung in der Hauptinstanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], oder auf einem anderen Computer die **VSIX** in der Datei **Bin\\\***. Kopieren Sie die Datei auf den Computer, auf dem Sie sie installieren möchten, und doppelklicken Sie dann darauf. Verwenden Sie zum Deinstallieren der Datei die Option **Erweiterungen und Updates** im Menü **Extras** .  
  
## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Hinzufügen eines Ebenenvalidierungssteuerelements zu einer separaten VSIX  
 Wenn Sie eine VSIX erstellen möchten, die Ebenenvalidierungssteuerelemente, Befehle und andere Erweiterungen enthält, empfiehlt es sich, ein Projekt zum Definieren der VSIX und getrennte Projekte für die Handler zu erstellen. 
  
#### <a name="to-add-layer-validation-to-a-separate-vsix"></a>So fügen Sie einer separaten VSIX eine Ebenenvalidierung hinzu  
  
1.  Erstellen Sie in einer neuen oder vorhandenen Visual Studio-Projektmappe ein Klassenbibliotheksprojekt. Klicken Sie im Dialogfeld **Neues Projekt** auf **Visual C#** , und klicken Sie dann auf **Klassenbibliothek**. Dieses Projekt enthält die Ebenenvalidierungsklasse.  
  
2.  Identifizieren oder erstellen Sie ein VSIX-Projekt in der Projektmappe. Ein VSIX-Projekt enthält eine Datei mit dem Namen **source.extension.vsixmanifest**. Wenn Sie ein VSIX-Projekt hinzufügen müssen, führen Sie die folgenden Schritte aus:  
  
    1.  Wählen Sie im Dialogfeld **Neues Projekt** die Optionen **Visual C#Erweiterungen**, **Erweiterungen**und **VSIX-Projekt**aus.  
  
    2.  Wählen Sie im **Projektmappen-Explorer**im Kontextmenü des VSIX-Projekts die Option **Als Startprojekt festlegen**aus.  
  
3.  Fügen Sie in **source.extension.vsixmanifest**unter **Objekte**das Ebenenvalidierungsprojekt als MEF-Komponente hinzu:  
  
    1.  Wählen Sie **Neu**aus.  
  
    2.  Legen Sie im Dialogfeld **Neues Objekt hinzufügen** Folgendes fest:  
  
         **Typ** = **Microsoft.VisualStudio.MefComponent**  
  
         **Quelle** = **Ein Projekt in der aktuellen Projektmappe**  
  
         **Projekt** = *Ihr Validierungssteuerelement-Projekt*  
  
4.  Außerdem müssen Sie das Projekt als Ebenenvalidierung hinzufügen:  
  
    1.  Wählen Sie **Neu**aus.  
  
    2.  Legen Sie im Dialogfeld **Neues Objekt hinzufügen** Folgendes fest:  
  
         **Typ** = **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. Dies ist keine der Optionen in der Dropdownliste. Sie müssen den Typ über die Tastatur eingeben.  
  
         **Quelle** = **Ein Projekt in der aktuellen Projektmappe**  
  
         **Projekt** = *Ihr Validierungssteuerelement-Projekt*  
  
5.  Kehren Sie zum Ebenenvalidierungsprojekt zurück, und fügen Sie die folgenden Projektverweise hinzu:  
  
    |**Referenz**|**Was können Sie tun**|  
    |-------------------|------------------------------------|  
    |Microsoft.VisualStudio.GraphModel.dll|Lesen des Architekturdiagramms|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Lesen des Ebenen zugeordneten Code-DOMs|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Lesen des Ebenenmodells|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Lesen und Aktualisieren von Formen und Diagrammen.|  
    |System.ComponentModel.Composition|Definieren der Validierungskomponente mithilfe von Managed Extensibility Framework (MEF)|  
    |Microsoft.VisualStudio.Modeling.Sdk.[Version]|Definieren von Modellierungserweiterungen|  
  
6.  Kopieren Sie den Beispielcode am Ende dieses Themas in die Klassendatei im Bestätigungsbibliotheksprojekt, damit sie den Code für die Überprüfung enthält. Weitere Informationen finden Sie unter [Programmieren einer Validierung](#programming).  
  
7.  Weitere Informationen zum Testen der Erweiterung finden Sie unter [Debuggen der Ebenenvalidierung](#debugging).  
  
    > [!NOTE]
    >  Die Methode wird nur unter bestimmten Umständen aufgerufen, und Haltepunkte funktionieren nicht automatisch. Weitere Informationen finden Sie unter [Debuggen der Ebenenvalidierung](#debugging).  
  
8.  So installieren Sie die VSIX-Projekt in der Hauptinstanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], oder auf einem anderen Computer die **VSIX** in der Datei der **Bin** Verzeichnis des VSIX-Projekts. Kopieren Sie die Datei auf den Computer, auf dem Sie die VSIX installieren möchten. Doppelklicken Sie in Windows-Explorer auf die VSIX-Datei. (Datei-Explorer in Windows 8.)  
  
     Verwenden Sie zum Deinstallieren der Datei die Option **Erweiterungen und Updates** im Menü **Extras** .  
  
##  <a name="a-nameprogramminga-programming-validation"></a><a name="programming"></a>Programmieren einer Validierung  
 Zum Definieren einer Ebenenvalidierungserweiterung definieren Sie eine Klasse, die über die folgenden Eigenschaften verfügt:  
  
-   Die allgemeine Form der Deklaration lautet wie folgt:  
  
    ```  
  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;  
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
    using Microsoft.VisualStudio.GraphModel;  
    ...  
     [Export(typeof(IValidateArchitectureExtension))]  
      public partial class Validator1Extension :  
                      IValidateArchitectureExtension  
      {  
        public void ValidateArchitecture(Graph graph)  
        {  
           GraphSchema schema = graph.DocumentSchema;  
          ...  
      } }  
    ```  
  
-   Wenn Sie einen Fehler entdecken, können Sie ihn mit `LogValidationError()`melden.  
  
    > [!WARNING]
    >  Verwenden Sie nicht die optionalen Parameter von `LogValidationError`.  
  
 Wenn der Benutzer den Menübefehl **Architektur überprüfen** aufruft, werden die Ebenen und ihre Artefakte vom Ebenenlaufzeitsystem analysiert, und es wird ein Diagramm erstellt. Das Diagramm besteht aus vier Teilen:  
  
-   Den Ebenenmodellen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe, die als Knoten und Links im Diagramm dargestellt werden.  
  
-   Dem Code, Projektelementen und anderen Artefakte, die in der Projektmappe definiert und als Knoten dargestellt werden, sowie den Links, die die vom Analyseprozess ermittelten Abhängigkeiten vertreten.  
  
-   Links von den Ebenenknoten zu den Codeartefaktknoten.  
  
-   Knoten, die die vom Validierungssteuerelement ermittelten Fehler darstellen.  
  
 Wenn das Diagramm erstellt wurde, wird die Standardvalidierungsmethode aufgerufen. Nachdem diese abgeschlossen ist, werden alle installierten Erweiterungsvalidierungsmethoden ohne spezifische Reihenfolge aufgerufen. Das Diagramm wird an jede `ValidateArchitecture` -Methode übergeben, die das Diagramm überprüfen und gefundene Fehler melden kann.  
  
> [!NOTE]
>  Dies ist nicht identisch mit dem Validierungsprozess, der bei domänenspezifischen Sprachen verwendet werden kann.  
  
 Validierungsmethoden sollten das zu überprüfende Ebenenmodell oder den Code nicht ändern.  
  
 Das Diagrammmodell wird definiert, in <xref:Microsoft.VisualStudio.GraphModel>.</xref:Microsoft.VisualStudio.GraphModel> Seine Prinzipalklassen sind <xref:Microsoft.VisualStudio.GraphModel.GraphNode>und <xref:Microsoft.VisualStudio.GraphModel.GraphLink>.</xref:Microsoft.VisualStudio.GraphModel.GraphLink> </xref:Microsoft.VisualStudio.GraphModel.GraphNode>  
  
 Jeder Knoten und jeder Link verfügt über mindestens eine Kategorie, die den Typ des Elements oder der Beziehung angibt, die von ihr dargestellt wird. Die Knoten eines typischen Diagramms verfügen über die folgenden Kategorien:  
  
-   Dsl.LayerModel  
  
-   Dsl.Layer  
  
-   Dsl.Reference  
  
-   CodeSchema_Type  
  
-   CodeSchema_Namespace  
  
-   CodeSchema_Type  
  
-   CodeSchema_Method  
  
-   CodeSchema_Field  
  
-   CodeSchema_Property  
  
 Links von Ebenen zu Elementen im Code haben die Kategorie "Represents".  
  
##  <a name="a-namedebugginga-debugging-validation"></a><a name="debugging"></a>Debuggen der Validierung  
 Drücken Sie STRG+F5, um die Ebenenvalidierungserweiterung zu debuggen. Eine experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird geöffnet. Öffnen oder erstellen Sie ein Ebenenmodell in dieser Instanz. Dieses Modell muss Code zugeordnet sein und muss mindestens eine Abhängigkeit besitzen.  
  
### <a name="test-with-a-solution-that-contains-dependencies"></a>Test mit einer Projektmappe, die Abhängigkeiten enthält  
 Die Validierung wird erst ausgeführt, wenn die folgenden Eigenschaften vorhanden sind:  
  
-   Es ist mindestens einen Abhängigkeitslink im Diagramm Abhängigkeit.  
  
-   Es gibt Ebenen im Modell, die Codeelementen zugeordnet sind.  
  
 Öffnen oder erstellen Sie eine Projektmappe mit diesen Eigenschaften, wenn Sie eine experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zum ersten Mal zum Testen der Validierungserweiterung starten.  
  
### <a name="run-clean-solution-before-validate-architecture"></a>Ausführen einer Projektmappenbereinigung vor dem Überprüfen der Architektur  
 Verwenden Sie bei jeder Aktualisierung des Validierungscodes im Menü **Erstellen** der experimentellen Instanz den Befehl **Projektmappe bereinigen** , bevor Sie den Befehl "Überprüfen" testen. Dies ist notwendig, da die Ergebnisse der Validierung zwischengespeichert werden. Wenn Sie den Test Abhängigkeitsdiagramm oder den Code nicht aktualisiert haben, werden die Validierungsmethoden nicht ausgeführt werden.  
  
### <a name="launch-the-debugger-explicitly"></a>Explizites Starten des Debuggers  
 Die Validierung wird in einem separaten Prozess ausgeführt. Daher werden die Haltepunkte in der Überprüfungsmethode nicht ausgelöst. Sie müssen den Debugger explizit dem Prozess anfügen, wenn die Validierung gestartet wurde.  
  
 Fügen Sie am Anfang der Validierungsmethode einen Aufruf von `System.Diagnostics.Debugger.Launch()` ein, um den Debugger dem Validierungsprozess anzufügen. Wenn das Debugdialogfeld angezeigt wird, wählen Sie die Hauptinstanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aus.  
  
 Alternativ können Sie einen Aufruf von `System.Windows.Forms.MessageBox.Show()`einfügen. Wenn das Meldungsfeld angezeigt wird, wechseln Sie zur Hauptinstanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und auf die **Debuggen** auf **an den Prozess anhängen**. Wählen Sie den Prozess mit dem Namen **Graphcmd.exe**aus.  
  
 Starten Sie die experimentelle Instanz immer mit STRG+F5 (**Starten ohne Debugging**).  
  
### <a name="deploying-a-validation-extension"></a>Bereitstellen einer Validierungserweiterung  
 Um die Validierungserweiterung auf einem Computer zu installieren, auf dem eine geeignete Version von Visual Studio installiert ist, öffnen Sie die VSIX-Datei auf dem Zielcomputer. Um die Installation auf einem Computer mit [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] auszuführen, müssen Sie den VSIX-Inhalt manuell in einen Ordner "Extensions" extrahieren. Weitere Informationen finden Sie unter [bereitstellen eine Ebene Model-Erweiterung](../modeling/deploy-a-layer-model-extension.md).  
  
##  <a name="a-nameexamplea-example-code"></a><a name="example"></a>Beispielcode  
  
```c#  
using System;  
using System.ComponentModel.Composition;  
using System.Globalization;  
using System.Linq;  
using System.Text.RegularExpressions;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.GraphModel;  
  
namespace Validator3  
{  
    [Export(typeof(IValidateArchitectureExtension))]  
    public partial class Validator3Extension : IValidateArchitectureExtension  
    {  
        /// <summary>  
        /// Validate the architecture  
        /// </summary>  
        /// <param name="graph">The graph</param>  
        public void ValidateArchitecture(Graph graph)  
        {  
            if (graph == null) throw new ArgumentNullException("graph");  
  
            // Uncomment the line below to debug this extension during validation  
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);  
  
            // Get all layers on the diagram  
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))  
            {  
                System.Threading.Thread.Sleep(100);  
                // Get the required regex property from the layer node  
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;  
                if (!string.IsNullOrEmpty(regexPattern))  
                {  
                    Regex regEx = new Regex(regexPattern);  
  
                    // Get all referenced types in this layer including those from nested layers so each  
                    // type is validated against all containing layer constraints.  
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))  
                    {  
                        // Check the type name against the required regex                          
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);  
                        string typeName = builder.Type.Name;  
                        if (!regEx.IsMatch(typeName))  
                        {  
                            // Log an error  
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);  
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);  
                        }  
                    }  
                }  
  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern Sie Abhängigkeitsdiagramme](../modeling/extend-layer-diagrams.md)

