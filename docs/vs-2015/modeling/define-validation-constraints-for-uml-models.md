---
title: Definieren von validierungseinschränkungen für UML-Modellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, validation constraints
ms.assetid: 87b3b0da-122d-4121-9318-200c38ff49d0
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6647d37636ed0e79d817113e388ae5df23a88a29
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782413"
---
# <a name="define-validation-constraints-for-uml-models"></a>Definieren von Validierungseinschränkungen für UML-Modelle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Validierungseinschränkungen definieren, die testen, ob das Modell eine von Ihnen angegebene Bedingung erfüllt. Sie können z. B. eine Einschränkung definieren, um sicherzustellen, dass ein Benutzer keine Schleife mit Vererbungsbeziehungen erstellt. Die Einschränkung wird aufgerufen, wenn der Benutzer versucht, das Modell zu öffnen oder zu speichern. Sie kann auch manuell aufgerufen werden. Wenn die Einschränkung fehlschlägt, wird dem Fehlerfenster eine von Ihnen definierte Fehlermeldung hinzugefügt. Sie können diese Einschränkungen in einer Visual Studio-Integrationserweiterung ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) verpacken, die Sie an andere Visual Studio-Benutzer verteilen können.  
  
 Sie können auch Einschränkungen definieren, mit denen das Modell anhand externer Ressourcen (z. B. Datenbanken) überprüft wird. Wenn Sie Programmcode anhand eines Ebenendiagramms überprüfen möchten, finden Sie unter [Hinzufügen einer benutzerdefinierten architekturvalidierung zu Ebenendiagrammen](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
 Welche Versionen von Visual Studio UML-Modelle unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="requirements"></a>Anforderungen  
 Siehe [Anforderungen](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="applying-validation-constraints"></a>Anwenden von Validierungseinschränkungen  
 Validierungseinschränkungen werden in drei Situationen angewendet: wenn Sie ein Modell speichern, wenn Sie ein Modell öffnen, und wenn Sie im Menü **Architektur** auf **UML-Modell überprüfen** klicken. In jedem Fall werden nur die Einschränkungen angewendet, die für die jeweiligen Situation definiert wurden. In der Regel werden Einschränkungen jedoch für mehrere Situationen definiert.  
  
 Validierungsfehler werden in den Fehlerfenstern von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] angezeigt. Sie können auf einen Fehler doppelklicken, um die betroffenen Modellelemente auszuwählen.  
  
 Weitere Informationen zum Anwenden der Validierung finden Sie unter [Überprüfen des UML-Modells](../modeling/validate-your-uml-model.md).  
  
## <a name="defining-a-validation-extension"></a>Definieren einer Validierungserweiterung  
 Um eine Validierungserweiterung für einen UML-Designer zu erstellen, müssen Sie eine Klasse erstellen, welche die Validierungseinschränkungen definiert, und diese Klasse in eine Visual Studio-Integrationserweiterung (VSIX, Visual Studio Integration Extension) einbetten. Die VSIX fungiert als Container zum Installieren der Einschränkung. Es gibt zwei alternative Methoden zur Definition einer Validierungserweiterung:  
  
-   **Erstellen einer validierungserweiterung innerhalb der eigenen VSIX mithilfe einer Projektvorlage.** Dies ist die schnellere Methode. Verwenden Sie diese Methode, wenn Sie die Validierungseinschränkungen nicht mit anderen Erweiterungstypen, z. B. Menübefehlen, benutzerdefinierten Toolboxelementen oder Gestenhandlern, kombinieren möchten. Sie können mehrere Einschränkungen in einer Klasse definieren.  
  
-   **Erstellen Sie separater Validierungsklassen und VSIX-Projekte.** Verwenden Sie diese Methode, wenn Sie mehrere Erweiterungstypen in dieselbe VSIX kombinieren möchten. Wenn beispielsweise der Menübefehl erwartet, dass das Modell bestimmte Einschränkungen berücksichtigt, können Sie es in dieselbe VSIX wie eine Validierungsmethode einbetten.  
  
#### <a name="to-create-a-validation-extension-in-its-own-vsix"></a>So erstellen Sie eine Validierungserweiterung in der eigenen VSIX  
  
1. Klicken Sie im Dialogfeld **Neues Projekt** unter **Modellierungsprojekte**auf **Validierungserweiterung**.  
  
2. Öffnen Sie im neuen Projekt die **.cs** -Datei, und ändern Sie die Klasse, um die Validierungseinschränkung zu implementieren.  
  
    Weitere Informationen finden Sie unter [Auswerten der Validierungseinschränkung](#Implementing).  
  
   > [!IMPORTANT]
   >  Stellen Sie sicher, dass die **.cs** -Dateien die folgende `using` -Anweisung enthalten:  
   >   
   >  `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
3. Sie können weitere Einschränkungen hinzufügen, indem Sie neue Methoden definieren. Um eine Methode als Validierungsmethode zu kennzeichnen, muss sie auf die gleiche Weise mit den Attributen markiert werden, wie die ursprüngliche Validierungsmethode.  
  
4. Testen Sie die Einschränkungen, indem Sie F5 drücken. Weitere Informationen finden Sie unter [Ausführen einer Validierungseinschränkung](#Executing).  
  
5. Installieren Sie den Menübefehl auf einem anderen Computer durch Kopieren der Datei **Bin\\\*\\\*VSIX** , die vom Projekt erstellt wird. Weitere Informationen finden Sie unter [Installieren und Deinstallieren einer Erweiterung](#Installing).  
  
   Wenn Sie andere **.cs** -Dateien hinzuzufügen, benötigen Sie normalerweise die folgenden `using` -Anweisungen:  
  
```csharp  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.Validation;  
using Microsoft.VisualStudio.Uml.Classes;  
  
```  
  
 Es gibt ein alternatives Verfahren:  
  
#### <a name="to-create-a-separate-validation-constraint-in-a-class-library-project"></a>So erstellen Sie eine separate Validierungseinschränkung in einem Klassenbibliotheksprojekt  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt. Sie können dieses entweder zu einer vorhandenen VSIX-Projektmappe hinzufügen, oder Sie können eine neue Projektmappe erstellen.  
  
    1.  Wählen Sie im Menü **Datei** die Optionsfolge **Neu**, **Projekt**aus.  
  
    2.  Erweitern Sie unter **Installierte Vorlagen**entweder **Visual C#** oder **Visual Basic**, und wählen Sie anschließend in der mittleren Spalte **Klassenbibliothek**aus.  
  
2.  Erstellen Sie ein VSIX-Projekt, sofern die Projektmappe noch kein VSIX-Projekt enthält:  
  
    1.  Wählen Sie im **Projektmappen-Explorer**im Kontextmenü der Projektmappe die Option  **Hinzufügen**und dann **Neues Projekt**aus.  
  
    2.  Erweitern Sie unter **Installierte Vorlagen**den Knoten **Visual C#** oder **Visual Basic**, und wählen Sie anschließend **Erweiterungen**aus. Klicken Sie in der mittleren Spalte auf **VSIX Project**.  
  
3.  Legen Sie das VSIX-Projekt als Startprojekt der Projektmappe fest.  
  
    -   Wählen Sie im Projektmappen-Explorer im Kontextmenü des VSIX-Projekts die Option **Als Startprojekt festlegen**aus.  
  
4.  Fügen Sie in **source.extension.vsixmanifest**unter **Inhalt**das Klassenbibliotheksprojekt als MEF-Komponente hinzu:  
  
    1.  Legen Sie auf der Registerkarte **MetaData** einen Namen für VSIX fest.  
  
    2.  Legen Sie auf der Registerkarte **Ziele installieren** die Visual Studio-Versionen als Ziele fest.  
  
    3.  Wählen Sie auf der Registerkarte **Objekte** die Option **Neu**und wählen Sie im Dialogfeld:  
  
         **Typ** = **MEF-Komponente**  
  
         **Quelle** = **Ein Projekt in der aktuellen Projektmappe**  
  
         **Projekt** = *Ihr Klassenbibliotheksprojekt*  
  
#### <a name="to-define-the-validation-class"></a>So definieren Sie die Validierungsklasse  
  
1.  Dieses Verfahren ist nicht erforderlich, wenn Sie eine Validierungsklasse mit einer eigenen VSIX aus der Validierungsprojektvorlage erstellt haben.  
  
2.  Fügen Sie im Projekt der Validierungsklasse Verweise auf die folgenden [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] -Assemblys hinzu:  
  
     `Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
     `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`  
  
     `Microsoft.VisualStudio.Uml.Interfaces`  
  
     `System.ComponentModel.Composition`  
  
3.  Fügen Sie dem Klassenbibliotheksprojekt eine Datei hinzu, die einen ähnlichen Code enthält, wie das folgende Beispiel.  
  
    -   Jede Validierungseinschränkung ist in einer Methode enthalten, die mit einem bestimmten Attribut markiert ist. Die Methode akzeptiert einen Parameter eines Modellelementtyps. Wenn die Validierung aufgerufen wird, wendet das Validierungsframework die einzelnen Validierungsmethoden auf jedes Modellelement an, das ihrem Parametertyp entspricht.  
  
    -   Sie können diese Methoden in beliebige Klassen und Namespaces einfügen. Ändern Sie sie nach Bedarf.  
  
    ```  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Linq;  
    using Microsoft.VisualStudio.Modeling.Validation;  
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
    using Microsoft.VisualStudio.Uml.Classes;  
    // You might also need the other Microsoft.VisualStudio.Uml namespaces.  
  
    namespace Validation  
    {  
      public class MyValidationExtensions  
      {  
        // SAMPLE VALIDATION METHOD.  
        // All validation methods have the following attributes.  
        [Export(typeof(System.Action<ValidationContext, object>))]  
        [ValidationMethod(  
           ValidationCategories.Save  
         | ValidationCategories.Open  
         | ValidationCategories.Menu)]  
        public void ValidateClassNames  
          (ValidationContext context,   
           // This type determines what elements   
           // will be validated by this method:  
           IClass elementToValidate)  
        {  
          // A validation method should not change the model.  
  
          List<string> attributeNames = new List<string>();  
          foreach (IProperty attribute in elementToValidate.OwnedAttributes)  
          {  
            string name = attribute.Name;  
            if (!string.IsNullOrEmpty(name) && attributeNames.Contains(name))  
            {  
              context.LogError(  
                string.Format("Duplicate attribute name '{0}' in class {1}", name, elementToValidate.Name),  
                "001", elementToValidate);  
            }  
            attributeNames.Add(name);  
          }  
  
        }  
        // Add more validation methods for different element types.  
      }  
    }  
    ```  
  
##  <a name="Executing"></a> Ausführen einer Validierungseinschränkung  
 Führen Sie die Validierungsmethoden zu Testzwecken im Debugmodus aus.  
  
#### <a name="to-test-the-validation-constraint"></a>So testen Sie die Validierungseinschränkung  
  
1.  Drücken Sie **F5**oder wählen Sie im Menü **Debug** die Option **Debugging starten**.  
  
     Eine experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird gestartet.  
  
     **Problembehandlung**: Wenn ein neuer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nicht startet:  
  
    -   Wenn Sie mehr als ein Projekt haben, stellen Sie sicher, dass das VSIX-Projekt als Startprojekt der Projektmappe festgelegt wird.  
  
    -   Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das Start- oder einzelne Projekt und wählen Sie **Eigenschaften**aus. Wählen Sie im Projekteigenschaften-Editor die Registerkarte **Debuggen** . Stellen Sie sicher, dass die Zeichenfolge im Feld Externes Programm starten** der vollständige Pfadname von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ist. Dieser lautet in der Regel:  
  
         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  
  
2.  Öffnen oder erstellen Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ein Modellierungsprojekt, und öffnen oder erstellen Sie ein Modellierungsdiagramm.  
  
3.  So richten Sie einen Test für die Beispieleinschränkung aus dem vorherigen Abschnitt ein  
  
    1.  Öffnen Sie ein Klassendiagramm.  
  
    2.  Erstellen Sie eine Klasse, und fügen Sie zwei Attribute hinzu, die denselben Namen aufweisen.  
  
4.  Wählen Sie im Kontextmenü des Diagramms **Überprüfen**aus.  
  
5.  Alle Fehler im Modell werden im Fehlerfenster angezeigt.  
  
6.  Doppelklicken Sie auf den Fehlerbericht. Wenn die im Bericht erwähnten Elemente auf dem Bildschirm sichtbar sind, werden sie hervorgehoben.  
  
     **Problembehandlung**: Wenn der Befehl **Überprüfen** nicht im Menü angezeigt wird, stellen Sie Folgendes sicher:  
  
    -   Das Überprüfungsprojekt ist im VSIX-Projekt in **source.extensions.manifest** auf der Registerkarte **Objekte** als MEF-Komponente aufgeführt.  
  
    -   An die Validierungsmethoden sind das richtige `Export` -Attribut und das richtige `ValidationMethod` -Attribut angefügt.  
  
    -   `ValidationCategories.Menu` befindet sich auf das Argument für die `ValidationMethod` -Attribut, und es besteht aus mit anderen Werten, die mit logischen OR (&#124;).  
  
    -   Die Parameter aller `Import` -Attribute und `Export` -Attribute sind gültig.  
  
##  <a name="Implementing"></a> Auswerten der Einschränkung  
 Die Validierungsmethode sollte bestimmen, ob die anzuwendende Validierungseinschränkung den Wert true oder false hat. Bei "true" soll keine Aktion erfolgen. Bei "false" sollte ein Fehler gemeldet werden, indem die vom `ValidationContext` -Parameter bereitgestellten Methoden verwendet werden.  
  
> [!NOTE]
>  Validierungsmethoden sollten das Modell nicht ändern. Es gibt keine Garantie, wann oder in welcher Reihenfolge die Einschränkungen ausgeführt werden. Wenn Sie Informationen zwischen aufeinander folgenden Ausführungen einer Validierungsmethode innerhalb einer Validierungsausführung übergeben müssen, können Sie den unter [Koordinieren mehrerer Validierungen](#ContextCache)beschriebenen Kontextcache verwenden.  
  
 Wenn Sie z. B. sicherstellen möchten, dass der Name jedes Typs (Klasse, Schnittstelle oder Enumerator) mindestens drei Zeichen lang ist, können Sie die folgende Methode verwenden:  
  
```  
public void ValidateTypeName(ValidationContext context, IType type)  
{  
  if (!string.IsNullOrEmpty(type.Name) && type.Name.Length < 3)  
  {  
    context.LogError(  
      string.Format("Type name {0} is too short", type.Name),  
               "001", type);  
   }  
 }  
```  
  
 Weitere Informationen zu den Methoden und Typen zum Navigieren im Modell und Lesen des Modells finden Sie unter [Programming with the UML API](../modeling/programming-with-the-uml-api.md) .  
  
### <a name="about-validation-constraint-methods"></a>Informationen zu Validierungseinschränkungsmethoden  
 Jede Validierungseinschränkung wird von einer Methode der folgenden Form definiert:  
  
```  
[Export(typeof(System.Action<ValidationContext, object>))]  
 [ValidationMethod(ValidationCategories.Save   
  | ValidationCategories.Menu   
  | ValidationCategories.Open)]  
public void ValidateSomething  
  (ValidationContext context, IClassifier elementToValidate)  
{...}  
```  
  
 Die Attribute und Parameter jeder Validierungsmethode lauten wie folgt:  
  
|||  
|-|-|  
|`[Export(typeof(System.Action <ValidationContext, object>))]`|Definiert die Methode per Managed Extensibility Framework (MEF) als Validierungseinschränkung.|  
|`[ValidationMethod (ValidationCategories.Menu)]`|Gibt an, wann die Validierung ausgeführt wird. Verwenden Sie bitweises OR (&#124;) Wenn Sie mehr als eine Option kombinieren möchten.<br /><br /> `Menu` = aufgerufen über das Menü "Überprüfen".<br /><br /> `Save` = aufgerufen beim Speichern des Modells.<br /><br /> `Open` = aufgerufen beim Öffnen des Modells. `Load`: Wird beim Speichern des Modells aufgerufen, bei einem Verstoß gegen eine Einschränkung wird der Benutzer jedoch gewarnt, dass das Modell möglicherweise nicht wieder geöffnet werden kann. Wird zudem beim Laden aufgerufen, bevor das Modell analysiert wird.|  
|`public void ValidateSomething`<br /><br /> `(ValidationContext context,`<br /><br /> `IElement element)`|Ersetzen Sie den zweiten `IElement` -Parameter durch den Typ von Element, für den die Einschränkung gelten soll. Die Einschränkungsmethode wird für alle Elemente des angegebenen Typs aufgerufen.<br /><br /> Der Name der Methode ist irrelevant.|  
  
 Sie können beliebig viele Validierungsmethoden mit unterschiedlichen Typen im zweiten Parameter definieren. Wenn die Validierung aufgerufen wird, wird jede Validierungsmethode für jedes dem Parametertyp entsprechende Modellelement aufgerufen.  
  
### <a name="reporting-validation-errors"></a>Melden von Validierungsfehlern  
 Um einen Fehlerbericht zu erstellen, verwenden Sie die von `ValidationContext` bereitgestellten Methoden:  
  
 `context.LogError("error string", errorCode, elementsWithError);`  
  
- `"error string"` wird in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Fehlerliste angezeigt  
  
- `errorCode` ist eine Zeichenfolge, bei der es sich um einen eindeutigen Bezeichner des Fehlers handelt  
  
- `elementsWithError` identifiziert Elemente im Modell. Wenn Benutzer auf den Fehlerbericht doppelklicken, wird die Form ausgewählt, die dieses Element darstellt.  
  
  `LogError(),``LogWarning()` und `LogMessage()` platzieren Meldungen in den verschiedenen Abschnitten der Fehlerliste.  
  
## <a name="how-validation-methods-are-applied"></a>Anwenden von Validierungsmethoden  
 Die Validierung wird auf jedes Element im Modell angewendet, einschließlich Beziehungen und Teile größerer Elemente, z. B. Attribute einer Klasse und Parameter einer Operation.  
  
 Jede Validierungsmethode wird auf jedes Element angewendet, das dem Typ im zweiten Parameter entspricht. Wenn Sie z. B. eine Validierungsmethode mit einem zweiten Parameter `IUseCase` und eine weitere Methode mit dem übergeordneten Typ `IElement`definieren, werden folglich beide Methoden auf jeden Anwendungsfall im Modell angewendet.  
  
 Zusammenfassung der Typhierarchie finden Sie unter [UML-Modellelementtypen](../modeling/uml-model-element-types.md).  
  
 Sie können auch über Beziehungen auf Elemente zugreifen. Wenn Sie z. B. eine Validierungsmethode für `IClass`definieren möchten, könnten Sie die im Besitz befindlichen Eigenschaften in einer Schleife durchlaufen:  
  
```  
public void ValidateTypeName(ValidationContext context, IClass c)  
{  
   foreach (IProperty property in c.OwnedAttributes)  
   {  
       if (property.Name.Length < 3)  
       {  
            context.LogError(  
                 string.Format(  
                        "Property name {0} is too short",   
                        property.Name),   
                 "001", property);  
        }  
   }  
}  
```  
  
### <a name="creating-a-validation-method-on-the-model"></a>Erstellen einer Validierungsmethode für das Modell  
 Wenn Sie sicherstellen möchten, dass eine Validierungsmethode während jeder Validierungsausführung genau einmal aufgerufen wird, können Sie das `IModel`überprüfen:  
  
```  
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs; ...  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu)]  
public void ValidateModel(ValidationContext context, IModel model)  
{  foreach (IElement element in model.OwnedElements)  
   { ...  
```  
  
### <a name="validating-shapes-and-diagrams"></a>Überprüfen von Formen und Diagrammen  
 Validierungsmethoden werden nicht für Anzeigeelemente wie Diagramme und Formen aufgerufen, da der primäre Zweck von Validierungsmethoden die Überprüfung des Modells ist. Sie können jedoch mithilfe des Diagrammkontexts auf das aktuelle Diagramm zugreifen.  
  
 Deklarieren Sie in der Validierungsklasse `DiagramContext` als importierte Eigenschaft:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
...  
[Import]  
public IDiagramContext DiagramContext { get; set; }  
```  
  
 In einer Validierungsmethode können Sie mit `DiagramContext` auf das Diagramm zugreifen, das zurzeit den Fokus hat (sofern ein Diagramm den Fokus hat):  
  
```  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu)]  
public void ValidateModel(ValidationContext context, IModel model)  
{  
  IDiagram focusDiagram = DiagramContext.CurrentDiagram;  
  if (focusDiagram != null)  
  {  
    foreach (IShape<IUseCase> useCaseShape in  
              focusDiagram.GetChildShapes<IUseCase>())  
    { ...  
```  
  
 Um einen Fehler zu protokollieren, müssen Sie das von der Form dargestellte Modellelement abrufen, da es nicht möglich ist, eine Form an `LogError`zu übergeben:  
  
```  
IUseCase useCase = useCaseShape.Element;  
context.LogError(... , usecase);  
```  
  
###  <a name="ContextCache"></a> Koordinieren mehrerer Validierungen  
 Wenn die Validierung aufgerufen wird (z. B. vom Benutzer über ein Diagrammmenü), wird jede Validierungsmethode auf jedes Modellelement angewendet. Dies bedeutet, dass dieselbe Methode für einen einzelnen Aufruf des Validierungsframeworks viele Male auf verschiedene Elemente angewendet werden kann.  
  
 Dies stellt ein Problem für Validierungen dar, die sich mit den Beziehungen zwischen Elementen beschäftigen. Sie können z. B. eine Validierung schreiben, die von einem Anwendungsfall ausgeht und die **include** -Beziehungen durchläuft, um sicherzustellen, dass keine Schleifen vorhanden sind. Wenn die Methode jedoch auf jeden Anwendungsfall in einem Modell angewendet wird, das über viele **include** -Links verfügt, ist es wahrscheinlich, dass immer die gleichen Bereiche des Modells verarbeitet werden.  
  
 Um diese Situation zu vermeiden, gibt es einen Kontextcache, in dem Informationen während einer Validierungsausführung beibehalten werden. Sie können ihn verwenden, um Informationen zwischen verschiedenen Ausführungen der Validierungsmethoden zu übergeben. Beispielsweise können Sie eine Liste der Elemente speichern, die während einer Validierungsausführung bereits verarbeitet wurden. Der Cache wird zu Beginn jeder Validierungsausführung erstellt und kann nicht verwendet werden, um Informationen zwischen verschiedenen Validierungsausführungen zu übergeben.  
  
|||  
|-|-|  
|`context.SetCacheValue<T> (name, value)`|Speichern eines Werts|  
|`context.TryGetCacheValue<T> (name, out value)`|Abrufen eines Werts. Gibt "true" zurück, wenn der Vorgang erfolgreich ist.|  
|`context.GetValue<T>(name)`|Abrufen eines Werts.|  
|`Context.GetValue<T>()`|Abrufen eines Werts des angegebenen Typs|  
  
##  <a name="Installing"></a> Installieren und Deinstallieren einer Erweiterung  
 Sie können eine [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] -Erweiterung sowohl auf Ihrem eigenen Computer als auch auf anderen Computern installieren.  
  
#### <a name="to-install-an-extension"></a>So installieren Sie eine Erweiterung  
  
1.  Suchen Sie auf dem Computer nach der **.vsix** -Datei, die vom VSIX-Projekt erstellt wurde.  
  
    1.  Wählen Sie im **Projektmappen-Explorer**im Kontextmenü des VSIX-Projekts **Ordner in Windows Explorer öffnen**aus.  
  
    2.  Suchen Sie die Datei **Bin\\\*\\**_IhrProjekt_**VSIX**  
  
2.  Kopieren Sie die **.vsix** -Datei auf den Zielcomputer, auf dem Sie die Erweiterung installieren möchten. Dies kann Ihr eigener Computer oder ein anderer Computer sein.  
  
    -   Der Zielcomputer muss über eine der Editionen von [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] verfügen, die Sie in **source.extension.vsixmanifest**.  
  
3.  Öffnen Sie auf dem Zielcomputer die **.vsix** -Datei.  
  
     **Installer für Visual Studio-Erweiterungen** wird geöffnet, und die Erweiterung wird installiert.  
  
4.  Starten Sie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], bzw. starten Sie die Anwendung neu.  
  
#### <a name="to-uninstall-an-extension"></a>So deinstallieren Sie eine Erweiterung  
  
1. Wählen Sie im Menü **Tools** **Erweiterungen und Updates**aus.  
  
2. Erweitern Sie **Installierte Erweiterungen**.  
  
3. Wählen Sie die Erweiterung aus, und wählen Sie anschließend **Deinstallieren**.  
  
   In seltenen Fällen kann es vorkommen, dass eine fehlerhafte Erweiterung nicht geladen und ein Bericht im Fehlerfenster erstellt wird, aber im Erweiterungs-Manager keine Informationen angezeigt werden. In diesem Fall können Sie die Erweiterung entfernen, durch das Löschen der Datei von folgendem Speicherort, in denen *%LocalAppData%* ist in der Regel *DriveName*: \Users\\*Benutzername*\AppData\Local:  
  
   *%LocalAppData%* **\Microsoft\VisualStudio\\[Version] \Extensions**  
  
##  <a name="Example"></a> Beispiel  
 In diesem Beispiel wird nach Schleifen in der Abhängigkeitsbeziehung zwischen Elementen gesucht.  
  
 Die Validierung erfolgt für Speichervorgänge und für den Menübefehl zum Überprüfen.  
  
```  
/// <summary>  
/// Verify that there are no loops in the dependency relationsips.  
/// In our project, no element should be a dependent of itself.  
/// </summary>  
/// <param name="context">Validation context for logs.</param>  
/// <param name="element">Element to start validation from.</param>  
[Export(typeof(System.Action<ValidationContext, object>))]  
[ValidationMethod(ValidationCategories.Menu   
     | ValidationCategories.Save | ValidationCategories.Open)]  
public void NoDependencyLoops(ValidationContext context, INamedElement element)  
{  
    // The validation framework will call this method  
    // for every element in the model. But when we follow  
    // the dependencies from one element, we will validate others.  
    // So we keep a list of the elements that we don't need to validate again.   
    // The list is kept in the context cache so that it is passed  
    // from one execution of this method to another.  
    List<INamedElement> alreadySeen = null;  
    if (!context.TryGetCacheValue("No dependency loops", out alreadySeen))  
    {  
       alreadySeen = new List<INamedElement>();  
       context.SetCacheValue("No dependency loops", alreadySeen);  
    }  
  
    NoDependencyLoops(context, element,   
                new INamedElement[0], alreadySeen);      
}  
  
/// <summary>  
/// Log an error if there is any loop in the dependency relationship.  
/// </summary>  
/// <param name="context">Validation context for logs.</param>  
/// <param name="element">The element to be validated.</param>  
/// <param name="dependants">Elements we've followed in this recursion.</param>  
/// <param name="alreadySeen">Elements that have already been validated.</param>  
/// <returns>true if no error was detected</returns>  
private bool NoDependencyLoops(ValidationContext context,   
    INamedElement element, INamedElement[] dependants,   
    List<INamedElement> alreadySeen)  
{  
    if (dependants.Contains(element))  
    {  
        context.LogError(string.Format("{0} should not depend on itself", element.Name),   
        "Fabrikam.UML.NoGenLoops", // unique code for this error  
        dependants.SkipWhile(e => e != element).ToArray());   
            // highlight elements that are in the loop  
        return false;  
    }  
    INamedElement[] dependantsPlusElement =   
        new INamedElement[dependants.Length + 1];  
    dependants.CopyTo(dependantsPlusElement, 0);  
    dependantsPlusElement[dependantsPlusElement.Length - 1] = element;  
  
    if (alreadySeen.Contains(element))  
    {  
        // We have already validated this when we started   
        // from another element during this validation run.  
        return true;  
    }  
    alreadySeen.Add(element);  
  
    foreach (INamedElement supplier in element.GetDependencySuppliers())  
    {  
        if (!NoDependencyLoops(context, supplier,  
             dependantsPlusElement, alreadySeen))  
        return false;  
    }  
    return true;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren und Installieren einer modellierungserweiterung](../modeling/define-and-install-a-modeling-extension.md)   
 [Programmieren mit der UML-API](../modeling/programming-with-the-uml-api.md)



