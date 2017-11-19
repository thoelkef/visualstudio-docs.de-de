---
title: Mithilfe von Visual Studio-ModelBus in einer Textvorlage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: "13"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: c496aaa7db6f2260764b413bfdf09f766be87384
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Verwenden von Visual Studio-ModelBus in einer Textvorlage
Wenn Sie Textvorlagen, der ein Modell zu lesen schreiben, enthält [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus verweist, möglicherweise möchten Sie die Verweise für den Zugriff auf die Ziel-Modelle zu beheben. In diesem Fall müssen Sie die Textvorlagen und die referenzierten domänenspezifische Sprachen (konzentriert) anpassen:  
  
-   Der DSL, die das Ziel der Verweise ist nur eine ModelBus-Adapter verfügt, die für den Zugriff von Textvorlagen konfiguriert ist. Wenn Sie auch die DSL aus anderem Code zugreifen, ist der neu konfigurierten Adapter zusätzlich zu den standardmäßigen ModelBus-Adapter.  
  
     Der Adapter-Manager muss von erben <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> und muss das Attribut `[HostSpecific(HostName)]`.  
  
-   Die Vorlage muss Vererben <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
> [!NOTE]
>  Wenn DSL-Modelle zu lesen, die keine ModelBus Verweise enthalten sein sollen, können Sie Direktivenprozessoren, die in Ihren Projekten DSL generiert werden. Weitere Informationen finden Sie unter [Zugriff auf Modelle über Textvorlagen](../modeling/accessing-models-from-text-templates.md).  
  
 Weitere Informationen zu den Textvorlagen finden Sie unter [Design-Time Code Generation mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>Erstellen ein Modell Hostbusadapter für den Zugriff von Textvorlagen  
 Um einen Verweis ModelBus in einer Textvorlage zu beheben, muss das Ziel DSL einen kompatiblen Adapter verfügen. Führen Sie den Textvorlagen in einer separaten AppDomain aus der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editoren dokumentieren: Entwicklungs- und der Adapter hat daher beim Laden des Modells anstelle der Zugriff über DTE.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>So erstellen Sie eine ModelBus-Adapter, die mithilfe von Textvorlagen kompatibel ist  
  
1.  Wenn das Ziel DSL-Lösung keine **ModelBusAdapter** Projekt, erstellen Sie mithilfe des Assistenten Modelbus-Erweiterung:  
  
    1.  Herunterladen und Installieren der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus-Erweiterung, wenn Sie nicht bereits geschehen. Weitere Informationen finden Sie unter [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
    2.  Öffnen Sie die DSL-Definitionsdatei. Mit der rechten Maustaste in der Entwurfsoberfläche, und klicken Sie dann auf **aktivieren Modelbus**.  
  
    3.  Wählen Sie im Dialogfeld **ich diese DSL, die ModelBus verfügbar machen möchten**. Wenn Sie diese DSL, damit ihre Modelle verfügbar zu machen und Verweise auf andere konzentriert nutzen möchten, können Sie beide Optionen auswählen.  
  
    4.  Klicken Sie auf **OK**. Der DSL-Projektmappe wird ein neues ModelBusAdapter-Projekt hinzugefügt.  
  
    5.  Klicken Sie auf **Transformieren aller Vorlagen**.  
  
    6.  Generieren Sie die Projektmappe neu.  
  
2.  Duplizieren Sie gegebenenfalls die DSL aus einer Textvorlage sowohl aus anderem Code, z. B. den Befehl, den Zugriff auf die **ModelBusAdapter** Projekt:  
  
    1.  Kopieren Sie im Windows-Explorer, und fügen Sie den Ordner mit **ModelBusAdapter.csproj**.  
  
    2.  Benennen Sie die Projektdatei (z. B. zum **T4ModelBusAdapter.csproj**).  
  
    3.  In **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektmappenknoten, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **vorhandenes Projekt**. Suchen Sie das neue adapterprojekt **T4ModelBusAdapter.csproj**.  
  
    4.  In den einzelnen `*.tt` Datei ändern Sie den Namespace, der das neue Projekt.  
  
    5.  Mit der rechten Maustaste in des neuen Projekts im Projektmappen-Explorer, und klicken Sie dann auf Eigenschaften. Ändern Sie im Eigenschaften-Editor die Namen der generierten Assembly und der Standardnamespace.  
  
    6.  Fügen Sie DslPackage im Projekt einen Verweis auf das neue adapterprojekt, sodass sie Verweise auf beide Adapter verfügt.  
  
    7.  Fügen Sie in DslPackage\source.extension.tt eine Zeile, die das neue adapterprojekt verweist auf ein.  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **Transformieren aller Vorlagen** und die Projektmappe neu erstellen. Es sollten keine Buildfehler auftreten.  
  
3.  Fügen Sie in der neuen adapterprojekt Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  In AdapterManager.tt:  
  
    -   Ändern Sie die Deklaration von AdapterManagerBase, sodass es erbt <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   Ersetzen Sie am Ende der Datei der HostSpecific-Attribut, bevor Sie die AdapterManager-Klasse. Entfernen Sie die folgende Zeile:  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         Fügen Sie die folgende Zeile ein:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Dieses Attribut filtert den Satz der Adapter, der verfügbar ist, wenn ein Consumer Modelbus für einen Adapter sucht.  
  
5.  **Transformieren aller Vorlagen** und die Projektmappe neu erstellen. Es sollten keine Buildfehler auftreten.  
  
## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>Schreiben einer Textvorlage, die ModelBus Verweise aufgelöst werden können  
 In der Regel beginnen Sie mit einer Vorlage, die liest und Dateien aus einer "Quelle" DSL generiert. Diese Vorlage verwendet, die Richtlinie, die generiert wird, in der DSL-Quellprojekt Modell Quelldateien in der Art und Weise zu lesen, die in beschriebenen [Zugriff auf Modelle über Textvorlagen](../modeling/accessing-models-from-text-templates.md). Allerdings enthält die Quelle DSL ModelBus Verweise auf einen DSL "Target". Daher möchten den Vorlagencode zum Auflösen der Verweise und Zugriff auf das Ziel DSL zu aktivieren. Sie müssen daher die Vorlage anpassen, indem Sie die folgenden Schritte:  
  
-   Ändern Sie die Basisklasse der Vorlage auf <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
-   Umfassen `hostspecific="true"` in der Template-Direktive.  
  
-   Fügen Sie Assemblyverweise hinzu, das Ziel DSL und die Adapter und ModelBus zu aktivieren.  
  
-   Sie brauchen nicht der Richtlinie, die als Teil der DSL-Ziel generiert wird.  
  
```  
<#@ template debug="true" hostspecific="true" language="C#"  
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
<#@ output extension=".txt" #>  
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>  
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>  
<#@ assembly name = "System.Core" #>  
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
<#@ import namespace="Company.TargetDsl" #>  
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>  
<#@ import namespace="System.Linq" #>  
<#  
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.  
  // In the source DSL Definition, the root element has a model reference:  
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)   
  {if (adapter != null)  
   {  
      // Get the root of the target model:  
      TargetRoot target = adapter.ModelRoot;  
    // The source DSL Definition has a class "SourceElement" embedded under the root.  
    // (Let's assume they're all in the same model file):  
    foreach (SourceElement sourceElement in source.Elements)  
    {  
      // In the source DSL Definition, each SourceElement has a MBR property:  
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;  
      // Resolve the target model element:   
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);   
#>  
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.  
<#  
    }  
  }}  
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename   
  // from a path that is relative to the text template.  
#>  
  
```  
  
 Wenn diese Vorlage "Text" ausgeführt wird, die `SourceDsl` Richtlinie lädt die Datei `Sample.source`. Die Elemente eines Modells, beginnend mit kann auf die Vorlage zugreifen `this.ModelRoot`. Der Code können Domänenklassen und Eigenschaften für diese DSL.  
  
 Darüber hinaus kann die Vorlage ModelBus-Verweise aufzulösen. Wobei die Verweise auf das Zielmodell zeigen, können die Assemblyanweisungen im Code verwenden Sie die Domänenklassen und Eigenschaften des Modells DSL.  
  
-   Wenn Sie keine Richtlinie verwenden, die von einem DSL-Projekt generiert wird, sollten Sie auch Folgendes einschließen.  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   Verwendung `this.ModelBus` zum Zugriff auf die ModelBus abrufen.  
  
## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Exemplarische Vorgehensweise: Testen einer Textvorlage, die ModelBus verwendet.  
 In dieser exemplarischen Vorgehensweise führen Sie folgende Schritte aus:  
  
1.  Erstellen Sie zwei konzentriert. Eine DSL der *Consumer*, verfügt über eine `ModelBusReference` -Eigenschaft, die auf die anderen DSL verweisen kann, die *Anbieter*.  
  
2.  Erstellen Sie zwei ModelBus-Adapter im Anbieter: eine für den Zugriff von Textvorlagen, die andere für normalen Code.  
  
3.  Erstellen Sie Instanz-Modelle von der konzentriert in einem einzelnen experimentellen Projekt.  
  
4.  Festlegen einer Eigenschaft "Domain" in einem Modell, um auf das andere Modell verweisen.  
  
5.  Schreiben Sie einen Doppelklickhandler, der das Modell wird geöffnet, auf das ein.  
  
6.  Schreiben einer Textvorlage, die das erste Modell laden, folgen Sie den Verweis auf das andere Modell und Lesen des anderen Modells kann.  
  
#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Erstellen Sie eine DSL, die für ModelBus zugänglich ist  
  
1.  Erstellen Sie eine neue DSL-Projektmappe. Wählen Sie in diesem Beispiel die Projektmappenvorlage Datenflusstask aus. Legen Sie den Sprachnamen auf `MBProvider` und der Dateierweiterung ".provide".  
  
2.  DSL-Definitionsdiagramm Maustaste auf einen leeren Bereich des Diagramms, die nicht im oberen Bereich ist, und klicken Sie dann auf **aktivieren Modelbus**.  
  
    -   Wenn Sie nicht sehen **aktivieren Modelbus**, müssen Sie herunterladen und installieren Sie die Erweiterung VMSDK ModelBus. Suchen sie auf der Website VMSDK: [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
3.  In der **aktivieren Modelbus** wählen Sie im Dialogfeld **verfügbar zu machen diese DSL, die ModelBus**, und klicken Sie dann auf **OK**.  
  
     Ein neues Projekt `ModelBusAdapter`, wird der Projektmappe hinzugefügt.  
  
 Sie haben jetzt eine DSL, die von Textvorlagen über ModelBus zugegriffen werden kann. Verweise darauf können behoben werden, in den Code für Befehle, Ereignishandler oder Regeln, die in der AppDomain des Modell-Editor-Datei ausgeführt werden. Textvorlagen, jedoch in einer separaten AppDomain ausgeführt und ein Modell können nicht zugegriffen werden, wenn er bearbeitet wird. Wenn Sie in einer Textvorlage ModelBus Verweise auf diese DSL zugreifen möchten, müssen Sie einen separaten ModelBusAdapter verfügen.  
  
#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>So erstellen Sie eine ModelBus-Adapter, die für Textvorlagen konfiguriert ist  
  
1.  Kopieren Sie in Windows Explorer den Ordner, der ModelBusAdapter.csproj enthält.  
  
     Benennen Sie den Ordner T4ModelBusAdapter.  
  
     Benennen Sie die Projektdatei T4ModelBusAdapter.csproj.  
  
2.  Fügen Sie im Projektmappen-Explorer zur Projektmappe MBProvider T4ModelBusAdapter hinzu. Mit der rechten Maustaste des Knotens Projektmappe, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **vorhandenes Projekt**.  
  
3.  Mit der rechten Maustaste des T4ModelBusAdapter-Projektknoten, und klicken Sie dann auf Eigenschaften. Ändern Sie im Fenster mit Projekteigenschaften, die **Assemblyname** und **Default Namespace** auf `Company.MBProvider.T4ModelBusAdapters`.  
  
4.  Fügen Sie in jeder Datei *.tt in T4ModelBusAdapter "T4" in den letzten Teil des Namespaces, damit die Zeile der folgenden ähnelt.  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  In der `DslPackage` Projekt, fügen Sie einen Projektverweis auf `T4ModelBusAdapter`.  
  
6.  In DslPackage\source.extension.tt, fügen Sie die folgende Zeile unter `<Content>`.  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  In der `T4ModelBusAdapter` Projekt, fügen einen Verweis hinzu: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  Öffnen Sie T4ModelBusAdapter\AdapterManager.tt:  
  
    1.  Ändern Sie die Basisklasse von AdapterManagerBase in <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>. In diesem Teil der Datei sieht nun etwa folgendermaßen Folgendes.  
  
        ```  
        namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters  
        {  
            /// <summary>  
            /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer  
            /// </summary>  
            public partial class <#= dslName #>AdapterManagerBase   
            : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager  
            {  
  
        ```  
  
    2.  Fügen Sie am Ende der Datei das folgende Attribut vor AdapterManager-Klasse.  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Das Ergebnis sieht ungefähr so aus.  
  
        ```  
        /// <summary>  
        /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter  
        /// </summary>  
        [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]  
        [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]  
        [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]  
        [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]  
        public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase  
        {  
        }  
  
        ```  
  
9. Klicken Sie auf **alle Vorlagen transformieren** in der Titelleiste des Projektmappen-Explorers.  
  
10. Generieren Sie die Projektmappe neu. Klicken Sie auf F5.  
  
11. Stellen Sie sicher, dass der DSL funktioniert durch Drücken von F5. Öffnen Sie im experimentellen Projekt `Sample.provider`. Schließen Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 ModelBus Verweise auf diese DSL können jetzt in Textvorlagen und auch in gewöhnlichen Code behoben werden.  
  
#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Erstellen Sie eine DSL mit einer Eigenschaft "Domain" ModelBus-Verweis  
  
1.  Erstellen Sie eine neue DSL mit der minimalen Sprache Projektmappenvorlage. Benennen Sie die Sprache MBConsumer, und legen Sie die Dateierweiterung ".consume".  
  
2.  Fügen Sie im DSL-Projekt einen Verweis auf die MBProvider DSL-Assembly. Mit der rechten Maustaste `MBConsumer\Dsl\References` , und klicken Sie dann auf **Verweis hinzufügen**. In der **Durchsuchen** Registerkarte`MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     Dadurch können Sie Code erstellen, die andere DSL verwendet. Wenn Sie Verweise auf mehrere konzentriert erstellen möchten, fügen Sie sie auch hinzu.  
  
3.  Klicken Sie in der DSL-Definitionsdiagramm mit der rechten Maustaste in des Diagramms, und klicken Sie dann auf **aktivieren ModelBus**. Wählen Sie im Dialogfeld **Aktivieren dieser DSL Nutzen der ModelBus**.  
  
4.  In der Klasse `ExampleElement`, fügen Sie die Eigenschaft "Domain" eine neue `MBR`, und legen Sie im Eigenschaftenfenster, deren Typ auf `ModelBusReference`.  
  
5.  Mit der rechten Maustaste in die Eigenschaft "Domain" für das Diagramm, und klicken Sie dann auf **bestimmte Eigenschaften bearbeiten ModelBusReference**. Wählen Sie im Dialogfeld **ein Modellelement**.  
  
     Legen Sie den Dateifilter für das Dialogfeld wie folgt.  
  
     `Provider File|*.provide`  
  
     Die Teilzeichenfolge, nach "&#124;" ist ein Filter für die Datei Auswahl (Dialogfeld). Konnten Sie festlegen, dass alle Dateien mit zulassen *.\*  
  
     In der **Modell Elementtyp** aus, geben Sie die Namen der eine oder mehrere Domänen Klassen im Anbieter DSL (z. B. Company.MBProvider.Task). Sie können abstrakte Klassen sein. Wenn Sie die Liste leer lassen, kann der Benutzer den Verweis auf ein Element festlegen.  
  
6.  Das Dialogfeld zu schließen und **alle Vorlagen transformieren**.  
  
 Sie haben eine DSL erstellt, die Verweise auf Elemente in einem anderen DSL enthalten kann.  
  
#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Erstellen Sie einen ModelBus-Verweis auf eine andere Datei, in der Projektmappe  
  
1.  Drücken Sie in der Projektmappe MBConsumer STRG + F5. Eine experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird geöffnet, der **MBConsumer\Debugging** Projekt.  
  
2.  Fügen Sie eine Kopie der Sample.provide auf die **MBConsumer\Debugging** Projekt. Dies ist notwendig, da ein ModelBus-Verweis auf eine Datei in der gleichen Projektmappe verweisen muss.  
  
    1.  Mit der rechten Maustaste des Debugging-Projekts, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **vorhandenes Element**.  
  
    2.  In der **Element hinzufügen** Dialogfeld legen Sie den Filter auf **alle Dateien (\*.\*)** .  
  
    3.  Navigieren Sie zu `MBProvider\Debugging\Sample.provide` , und klicken Sie dann auf **hinzufügen**.  
  
3.  Öffnen Sie `Sample.consume`.  
  
4.  Klicken Sie auf eine Form "Beispiel", und klicken Sie im Fenster Eigenschaften auf **[...]**  in der MBR-Eigenschaft. Klicken Sie im Dialogfeld auf **Durchsuchen** , und wählen Sie `Sample.provide`. Klicken Sie im Fenster Elemente erweitern Sie den Task-Typ, und wählen Sie eines der Elemente.  
  
5.  Speichern Sie die Datei.  
  
     (Schließen nicht noch die experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].)  
  
 Sie haben ein Modell erstellt, die einen ModelBus Verweis auf ein Element in einem anderen Modell enthält.  
  
#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Lösen Sie einen Verweis ModelBus in einer Textvorlage  
  
1.  In der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], öffnen Sie eine Beispiel-Textvorlagendatei. Legen Sie deren Inhalt wie folgt.  
  
    ```  
    <#@ template debug="true" hostspecific="true" language="C#"  
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="Company.MBProvider" #>  
    <#  
      // Property provided by the Consumer directive processor:  
      ExampleModel consumerModel = this.ExampleModel;   
      // Iterate through Consumer model, listing the elements:  
      foreach (ExampleElement element in consumerModel.Elements)  
      {  
    #>  
       <#= element.Name #>   
    <#  
        if (element.MBR != null)  
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))  
      {   
              // If we allowed multiple types or DSLs in the MBR, discover type here.  
        Task task = adapter.ResolveElementReference<Task>(element.MBR);  
    #>  
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>  
    <#  
          }  
      }  
    #>  
  
    ```  
  
     Beachten Sie die folgenden Punkte:  
  
    1.  Die `hostSpecific` und `inherits` Attribute der `template` Richtlinie muss festgelegt werden.  
  
    2.  Der consumermodell wird auf die übliche Weise über den Direktivenprozessor zugegriffen, die in dieser DSL generiert wurde.  
  
    3.  Die Assembly und Import-Anweisungen müssen ModelBus und die Typen des Anbieters DSL zugreifen können.  
  
    4.  Wenn Sie wissen, dass viele MBR auf das gleiche Modell verknüpft sind, ist es besser, CreateAdapter nur einmal aufgerufen.  
  
2.  Sie speichern die Vorlage. Stellen Sie sicher, dass die resultierende Textdatei der folgenden ähnelt.  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Einen Verweis ModelBus in einen Gestenhandler zu beheben  
  
1.  Schließen Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], falls er ausgeführt wird.  
  
2.  Fügen Sie eine Datei, die mit dem Namen MBConsumer\Dsl\Custom.cs und legen Sie deren Inhalt wie folgt.  
  
    ```  
  
    namespace Company.MB2Consume  
    {  
      using Microsoft.VisualStudio.Modeling.Integration;  
      using Company.MB3Provider;  
  
      public partial class ExampleShape  
      {  
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)  
        {  
          base.OnDoubleClick(e);  
          ExampleElement element = this.ModelElement as ExampleElement;  
          if (element.MBR != null)  
          {  
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;  
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))  
            {  
              Task task = adapter.ResolveElementReference<Task>(element.MBR);  
              // Open a window on this model:  
              ModelBusView view = adapter.GetDefaultView();  
              view.Show();  
              view.SetSelection(element.MBR);  
            }  
          }  
        }  
      }  
    }  
  
    ```  
  
3.  Drücken Sie STRG+F5.  
  
4.  In der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]öffnen `Debugging\Sample.consume`.  
  
5.  Doppelklicken Sie auf eine Form.  
  
     Wenn Sie die MBR für dieses Element festgelegt haben, wird das referenzierte Modell wird geöffnet, und das Verweiselement ausgewählt ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration von Modellen mithilfe von Visual Studio-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
