---
title: "Verwenden von Visual Studio-ModelBus in einer Textvorlage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 13
---
# Verwenden von Visual Studio-ModelBus in einer Textvorlage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie Textvorlagen schreiben, die ein Modell gelesen wird, das Verweise [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus enthält, müssen Sie die Verweise aufgelöst werden, um das Zielmodell zu.  In diesem Fall müssen Sie die Textvorlagen und domänenspezifischen Sprache \(DSL, auf die verwiesen wird\) anpassen:  
  
-   Das DSL, das das Ziel der Verweise ist, muss einen ModelBus\-Adapter für den Vollzugriff verfügen, der von Textvorlagen konfiguriert ist.  Wenn Sie auch das DSL von anderem Code zugreifen, ist der umkonfigurierte neben dem Adapter Standard\-ModelBus\-Adapter erforderlich.  
  
     Der Adapter Manager muss von <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> erben und muss das Attribut `[HostSpecific(HostName)]`haben.  
  
-   Die Vorlage muss von <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>erben.  
  
> [!NOTE]
>  Wenn Sie DSL\-Modelle lesen möchten, die nicht ModelBus\-Verweise enthalten, können Sie die Direktivenprozessoren verwenden, die in den DSL\-Projekten generiert werden.  Weitere Informationen finden Sie unter [Zugreifen auf Modelle aus Textvorlagen](../modeling/accessing-models-from-text-templates.md).  
  
 Weitere Informationen zu Textvorlagen finden Sie unter [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
## Ein Modell Bus\-Adapter für den Zugriff von Textvorlagen erstellen  
 Um ein ModelBus\-Verweis in einer Textvorlage zu beheben, muss das Ziel DSL kompatiblen einen Adapter verfügen.  Textvorlagen werden in einer separaten Anwendungsdomäne aus den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editoren Dokumente aus. Daher muss der Adapter das Modell laden, anstatt sie zugreifen durch Design Time Extensibility, DTE.  
  
#### So erstellen Sie einen ModelBus\-Adapter für Textvorlagen kompatibel ist  
  
1.  Wenn die Lösung des Ziels DSL kein **ModelBusAdapter** Projekt vorhanden ist, erstellen Sie einen, indem Sie den Assistenten ModelBus\-Erweiterungs verwenden:  
  
    1.  Herunterladen und Installieren der Erweiterung [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus, wenn Sie dies nicht bereits getan haben.  Weitere Informationen finden Sie unter [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579)unter.  
  
    2.  Öffnen Sie die Datei DSL\-Definitions.  Klicken Sie mit der rechten Maustaste auf die Entwurfsoberfläche, und klicken Sie dann auf **ModelBus aktivieren**.  
  
    3.  Wählen Sie im Dialogfeld **Ich möchte diese DSL für den ModelBus verfügbar machen**.  Sie können beide Optionen auswählen, wenn Sie dieses DSL ihre Modelle verfügbar machen und Verweise auf andere DSL nutzen sollen.  
  
    4.  Klicken Sie auf **OK**.  Ein neues Projekt „ModelBusAdapter“ wird zur DSL\-Projektmappe hinzugefügt.  
  
    5.  Klicken Sie auf **Alle Vorlagen transformieren**.  
  
    6.  Generieren Sie die Projektmappe neu.  
  
2.  Wenn Sie das DSL in einer Textvorlage und von anderem Code, z. B. Befehl zugreifen möchten, identische Kopie der **ModelBusAdapter** Projekt:  
  
    1.  Kopieren und Einfügen in Windows\-Explorer den Ordner, der **ModelBusAdapter.csproj**enthält.  
  
    2.  Benennen Sie die Projektdatei \(z. B. **T4ModelBusAdapter.csproj**\).  
  
    3.  In **Projektmappen\-Explorer**mit der rechten Maustaste auf den Projektmappenknoten, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Vorhandenes Projekt**.  Suchen Sie das neue Adapter, **T4ModelBusAdapter.csproj**.  
  
    4.  In jeder `*.tt` neuen Datei des Projekts ändern Sie den Namespace.  
  
    5.  Klicken Sie mit der rechten Maustaste auf das neue Projekt im Projektmappen\-Explorer, und klicken Sie dann auf Eigenschaften.  Im Eigenschaften\-Editor ändern Sie die Namen der generierten Assembly und des Standardnamespace.  
  
    6.  Im DslPackage\-Projekt fügen Sie einen Verweis auf das neue Projekt Adapter hinzu, damit Verweise auf beide Adapter hat.  
  
    7.  In DslPackage \\ source.extension.tt, fügen Sie eine Linie hinzu, die den neuen Adapter Projekt verweist.  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **Alle Vorlagen transformieren** und die Projektmappe neu erstellen.  Keine Buildfehler auftreten können.  
  
3.  Im neuen Adapter, fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  In AdapterManager.tt:  
  
    -   Ändern Sie die Deklaration von AdapterManagerBase, dass sie von <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>erbt.  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   Wählen am Ende der Datei ersetzen Sie das HostSpecific\-Attribut vor der AdapterManager\-Klasse.  Entfernen Sie die folgende Zeile:  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         Fügen Sie die folgende Zeile ein:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Dieses Attribut filtert die Gruppe von Adaptern, der verfügbar ist, wenn ein modelbus Consumer für einen Adapter gefunden wird.  
  
5.  **Alle Vorlagen transformieren** und die Projektmappe neu erstellen.  Keine Buildfehler auftreten können.  
  
## Eine Textvorlage schreiben, die aufgelöst werden kann ModelBus\-Verweise  
 Normalerweise beginnen Sie mit einer Vorlage, die Dateien „aus einer Quelle gelesen und DSL“ generiert.  Diese Vorlage wird mit der Direktive, das im Projekt der Quelle DSL, Quelle von Dateien in der Weise zu lesen [Zugreifen auf Modelle aus Textvorlagen](../modeling/accessing-models-from-text-templates.md)in die generierte beschrieben wird.  Es enthält die Quelle ModelBus\-Verweise DSL mit einem „Ziel“ DSL.  Sie möchten daher den Vorlagencode ermöglichen, die Verweise aufzulösen und das Ziel DSL zuzugreifen.  Sie müssen daher die Vorlage anpassen, indem Sie folgende Schritte ausführen:  
  
-   Ändern Sie die Basisklasse der Vorlage zu <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.  
  
-   Einschließen `hostspecific="true"` in den Vorlagen direktiven.  
  
-   Fügen Sie Assemblyverweise für das Ziel DSL und den Adapter und ModelBus zu aktivieren.  
  
-   Sie benötigen keine Direktiven, die als Teil des Ziels DSL generiert wird.  
  
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
    // (Let’s assume they’re all in the same model file):  
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
  
 Diese Textvorlage ausgeführt wird, laden die `SourceDsl`\-Direktive die Datei `Sample.source`.  Die Vorlage kann die Elemente dieses Modells zugreifen und `this.ModelRoot`.  Der Code kann die Domänen Klassen und Eigenschaften dieses DSL verwenden.  
  
 Darüber hinaus kann die Vorlage ModelBus\-Verweise auflösen.  Wo Daten in das Zielmodell, die Assemblydirektive der Code die Domänen Klassen und Eigenschaften des DSL dieses Modells können.  
  
-   Wenn Sie keine Direktive verwenden, die von einem DSL\-Projekt generiert wurde, sollten Sie auch Folgendes einschließen.  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   Verwenden Sie `this.ModelBus` abzurufen, um Zugriff auf ModelBus.  
  
## Exemplarische Vorgehensweise: Eine Textvorlage testen, die mit ModelBus  
 Im Verlauf dieser exemplarischen Vorgehensweise führen Sie folgende Schritte aus:  
  
1.  Konstrukt zwei DSL.  Ein DSL, der *Consumer*, verfügt über eine `ModelBusReference`\-Eigenschaft, die das andere DSL zugreifen kann, den *Anbieter*.  
  
2.  Erstellen Sie zwei ModelBus\-Adapter im Anbieter erstellt: Zugriff für ein von Textvorlagen, die andere für normalen Code.  
  
3.  Erstellen Sie Instanzen modelle des DSL mit einem einzelnen experimentellen Projekt.  
  
4.  Legen Sie eine Domäneneigenschaft in einem Modell so fest, dass es auf den anderen Modell zu veranschaulichen.  
  
5.  Schreiben Sie einen Doppelklick Ereignishandler, der das Modell geöffnet, in dem gezeigt wird.  
  
6.  Schreiben Sie eine Textvorlage, die das erste Modell laden kann, folgen dem Verweis auf den anderen Modell und lesen die andere Modell.  
  
#### Erstellen Sie ein DSL, das ModelBus zugegriffen werden kann  
  
1.  Erstellen Sie eine neue DSL\-Projektmappe.  Für dieses Beispiel Aufgaben\-Fluss Wählen Sie die Vorlage Projektmappe aus.  Legen Sie den Sprachennamen auf `MBProvider` und die Dateinamenerweiterung in „.provide“ fest.  
  
2.  DSL\-Definitions im Diagramm mit der rechten Maustaste auf einen leeren Bereich des Diagramms, das nicht im oberen Bereich handelt, und klicken Sie dann auf **ModelBus aktivieren**.  
  
    -   Wenn Sie nicht **ModelBus aktivieren**anzuzeigen, müssen Sie die Erweiterung VMSDK ModelBus herunterladen und installieren.  Suchen Sie es auf der VMSDK\-Website: [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
3.  Wählen Sie im Dialogfeld **ModelBus aktivierenDiese DSL für den ModelBus verfügbar machen**und klicken Sie dann auf **OK**.  
  
     Ein neues Projekt mit `ModelBusAdapter`, wird der Projektmappe hinzugefügt.  
  
 Sie haben jetzt ein DSL, das von Textvorlagen von ModelBus zugegriffen werden kann.  Verweise darauf im Code behoben werden können, von Befehlen oder Ereignishandler, die in AppDomain der Modelldatei editors arbeiten.  Allerdings simsen von Vorlagen in separaten Anwendungsdomäne ein Modell und kann nicht zugegriffen werden, wenn sie bearbeitet wird.  Wenn Sie ModelBus\-Verweise diesem DSL in einer Textvorlage zugreifen möchten, müssen Sie ein separates ModelBusAdapter haben.  
  
#### So erstellen Sie einen ModelBus\-Adapter für Textvorlagen konfiguriert ist  
  
1.  Kopieren und Einfügen in Windows\-Explorer den Ordner, der ModelBusAdapter.csproj enthält.  
  
     Benennen Sie den Ordner T4ModelBusAdapter.  
  
     Benennen Sie die Projektdatei T4ModelBusAdapter.csproj.  
  
2.  Klicken Sie im Projektmappen\-Explorer mit der MBProvider\-Projektmappe T4ModelBusAdapter hinzu.  Klicken Sie mit der rechten Maustaste auf den Projektmappenknoten, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Vorhandenes Projekt**.  
  
3.  Klicken Sie mit der rechten Maustaste auf T4ModelBusAdapter\-Projektknoten und klicken Sie dann auf Eigenschaften.  Klicken Sie im Fenster Projekteigenschaften ändern Sie **Assemblyname** und **Standardnamespace** zu `Company.MBProvider.T4ModelBusAdapters`.  
  
4.  In jeder \*.tt\-Datei in T4ModelBusAdapter“ 'T4, Einfügung in den letzten Teil des Namespaces, damit die Zeile dem folgenden ähnelt.  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  Fügen Sie im `DslPackage` Projekt einen Projektverweis hinzu. `T4ModelBusAdapter`  
  
6.  In DslPackage \\ source.extension.tt, fügen Sie die folgende Zeile unter `<Content>`hinzu.  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  Im `T4ModelBusAdapter` Projekt fügen Sie einen Verweis auf ein: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  Öffnen Sie T4ModelBusAdapter \\ AdapterManager.tt:  
  
    1.  Ändern Sie die Basisklasse von AdapterManagerBase zu <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  Dieser Teil der Datei sieht nun folgendermaßen aus.  
  
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
  
    2.  Wählen am Ende der Datei, fügen Sie das folgende zusätzliche Attribut vor AdapterManager Klasse ein.  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         Das Ergebnis entspricht in etwa dem folgenden Beispiel.  
  
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
  
9. Klicken Sie auf **Alle Vorlagen transformieren** in der Titelleiste des Projektmappen\-Explorers.  
  
10. Generieren Sie die Projektmappe neu.  Klicken Sie auf F5.  
  
11. Stellen Sie sicher, dass das DSL funktioniert, indem Sie F5 drücken.  Im experimentellen Projekt öffnen Sie `Sample.provider`.  Schließen Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Zu diesem ModelBus\-Verweise DSL können nun behoben werden in Textvorlagen und im normalen Code.  
  
#### Erstellen Sie ein DSL mit einer ModelBus\-Bezugsdomäneneigenschaft  
  
1.  Erstellen Sie ein neues DSL, indem Sie die minimale Sprachen Vorlage für Office\-Projektmappen verwenden.  Nennen Sie die Sprache MBConsumer, und legen Sie die Dateinamenerweiterung in „.consume“ fest.  
  
2.  Im DSL\-Projekt fügen Sie einen Verweis auf die Assembly hinzu. MBProvider DSL  Klicken Sie mit der rechten Maustaste auf `MBConsumer\Dsl\References` , und klicken Sie dann auf **Verweis hinzufügen**.  Suchen Sie auf der Registerkarte **Durchsuchen**`MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     Dies ermöglicht es Ihnen, Code erstellt, der die andere DSL verwendet.  Wenn Sie Verweise auf einige DSL erstellen möchten, fügen Sie sie ebenfalls hinzugefügt.  
  
3.  DSL\-Definitions im Diagramm mit der rechten Maustaste auf das Diagramm, und klicken Sie dann auf **ModelBus aktivieren**.  Wählen Sie im Dialogfeld **Diese DSL aktivieren, um den ModelBus zu nutzen**aus.  
  
4.  In der Klasse `ExampleElement`fügen Sie eine neue `MBR`Domäneneigenschaft, und legen Sie im Eigenschaftenfenster den Typ `ModelBusReference`hinzu.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Domäneneigenschaft im Diagramm, und klicken Sie dann auf **ModelBusReference\-spezifische Eigenschaften bearbeiten**.  Wählen Sie im Dialogfeld **ein Modellelement**.  
  
     Legen Sie im Dialogfeld Datei zum nächsten Filter fest.  
  
     `Provider File|*.provide`  
  
     Die Teilzeichenfolge „nachfolgend&#124;“ ist ein Filter für das Dialogfeld Datei\-Auswahl.  Sie können dies festlegen, um alle Dateien zuzulassen, indem Sie \*.\* frei  
  
     Klicken Sie in der Liste **Modellelementtyp** Geben Sie den Namen eines weiteren Domänen Erz Klassen im Anbieter DSL ein \(z. B. Company.MBProvider.Task\).  Sie können abstrakte Klasse sein.  Wenn Sie die Liste leer lassen, kann der Benutzer den Verweis auf jedes Element festlegen.  
  
6.  Schließen Sie das Dialogfeld, und **Alle Vorlagen transformieren**.  
  
 Sie haben ein DSL erstellt, das Verweise auf Elemente in einem anderen DSL enthalten kann.  
  
#### Erstellen Sie ein ModelBus\-Verweis auf eine andere Datei in der Projektmappe  
  
1.  In der MBConsumer\-Projektmappe drücken Sie STRG\+F5.  Eine experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird im **MBConsumer\\Debugging** Projekt.  
  
2.  Fügen Sie eine Kopie Sample.provide dem **MBConsumer\\Debugging** Projekt hinzu.  Dies ist erforderlich, da ein ModelBus\-Verweis eine Datei in der gleichen Projektmappe verweisen muss.  
  
    1.  Klicken Sie mit der rechten Maustaste auf das Projekt, zeigen Sie auf Debuggen, und klicken Sie dann auf **HinzufügenVorhandenes Element**.  
  
    2.  Legen Sie im Dialogfeld **Element hinzufügen** Filter auf **Alle Dateien \(\*.\*\)**fest.  
  
    3.  Navigieren Sie zu `MBProvider\Debugging\Sample.provide` und klicken Sie dann auf **Hinzufügen**.  
  
3.  Öffnen Sie `Sample.consume`.  
  
4.  Klicken Sie auf eine Beispiels Form, und legen Sie im Eigenschaftenfenster auf **\[...\]** in der MBR\-Eigenschaft.  Klicken Sie im Dialogfeld auf **Durchsuchen** , und wählen Sie `Sample.provide`aus.  Erweitern Sie im Fenster Element vom Typ Aufgabe, und wählen Sie eines der Elemente auswählen.  
  
5.  Speichern Sie die Datei.  
  
     \(Nicht immer noch schließen Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\).  
  
 Sie haben ein Modell erstellt wird, in dem ein ModelBus\-Verweis auf ein Element in einem anderen Modell enthält.  
  
#### Lösen Sie ein ModelBus\-Verweis in einer Textvorlage auf  
  
1.  Klicken Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], öffnen Sie eine vorlagendatei ein Beispieltext.  Legen Sie seinen Inhalt wie folgt fest.  
  
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
  
    1.  Die `hostSpecific` und `inherits`\-Attribute der `template`\-Direktive muss festgelegt werden.  
  
    2.  Das Modell der Consumer in der üblichen Weise durch den Direktivenprozessor zugegriffen, der in diesem DSL generiert wurde.  
  
    3.  Die Assembly\- und von Import\-Direktiven müssen in der Lage sein, ModelBus und die Typen des Anbieters DSL zuzugreifen.  
  
    4.  Wenn Sie wissen, dass viele MBRs dem gleichen Modell verknüpft sind, empfiehlt es sich, CreateAdapter nur einmal aufrufen.  
  
2.  Sie speichern die Vorlage.  Stellen Sie sicher, dass die resultierende Textdatei dem folgenden ähnelt.  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### Lösen Sie ein ModelBus\-Verweis in einem für Gestenhandler  
  
1.  Schließen Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], wenn sie ausgeführt wird.  
  
2.  Fügen Sie eine Datei mit dem MBConsumer \\ \\ Custom.cs Dsl mit dem Namen hinzu, und legen Sie seinen Inhalt folgendermaßen fest.  
  
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
  
3.  Drücken Sie STRG\+F5.  
  
4.  Klicken Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], öffnen Sie `Debugging\Sample.consume`.  
  
5.  Doppelklicken Sie auf eine Form.  
  
     Wenn Sie das MBR für dieses Element festgelegt haben, wird das Element, auf das verwiesen wird und das Modell, auf den verwiesen wird, ist ausgewählt.  
  
## Siehe auch  
 [Integrieren von Modellen mit Visual Studio\-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md)