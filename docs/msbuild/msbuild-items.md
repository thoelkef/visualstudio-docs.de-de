---
title: "MSBuild-Elemente | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild-Elemente"
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
caps.latest.revision: 35
caps.handback.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild-Elemente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild-Elemente sind Eingaben in das Buildsystem und stellen sie Dateien in der Regel dar. Elemente werden in Elementtypen auf Grundlage ihrer Elementnamen gruppiert. Elementtypen sind benannte Listen von Elementen, die als Parameter für Aufgaben verwendet werden können. In den Aufgaben werden die Schritte des Buildprozesses mithilfe der Elementwerte ausgeführt.  
  
 Da Elemente anhand des Elementtyps benannt werden, die sie angehören, können die Begriffe "Item" und "Elementwert" synonym verwendet werden.  
  
 **In diesem Thema**  
  
-   [Erstellen von Elementen in einer Projektdatei](#BKMK_Creating1)  
  
-   [Erstellen von Elementen während der Ausführung](#BKMK_Creating2)  
  
-   [Verweisen auf Elemente in einer Projektdatei](#BKMK_ReferencingItems)  
  
-   [Verwenden von Platzhaltern zum Angeben von Elementen](#BKMK_Wildcards)  
  
-   [Verwenden das Exclude-Attribut](#BKMK_ExcludeAttribute)  
  
-   [Elementmetadaten](#BKMK_ItemMetadata)  
  
    -   [Verweisen auf Elementmetadaten in einer Projektdatei](#BKMK_ReferencingItemMetadata)  
  
    -   [Bekannte Elementmetadaten](#BKMK_WellKnownItemMetadata)  
  
    -   [Umwandeln von Elementtypen mit Metadaten](#BKMK_Transforming)  
  
-   [Elementdefinitionen](#BKMK_ItemDefinitions)  
  
-   [Attribute für Elemente in einem ItemGroup-Element eines Ziels](#BKMK_AttributesWithinTargets)  
  
    -   [Attribut entfernen](#BKMK_RemoveAttribute)  
  
    -   [KeepMetadata-Attribut](#BKMK_KeepMetadata)  
  
    -   [RemoveMetadata-Attribut](#BKMK_RemoveMetadata)  
  
    -   [KeepDuplicates-Attribut](#BKMK_KeepDuplicates)  
  
##  <a name="a-namebkmkcreating1a-creating-items-in-a-project-file"></a><a name="BKMK_Creating1"></a> Erstellen von Elementen in einer Projektdatei  
 Sie deklarieren, Elemente in der Projektdatei als untergeordnete Elemente von einer [ItemGroup](../msbuild/itemgroup-element-msbuild.md) Element. Der Name des untergeordneten Elements ist der Typ des Elements. Das `Include` -Attribut des Elements gibt an, welche Elemente (Dateien) in den Elementtyp aufgenommen werden sollen. Das folgende XML erstellt z. B. einen Elementtyp mit dem Namen `Compile`, die zwei Dateien enthält.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Das Element "file2.cs" das Element "file1.cs"; nicht ersetzt werden. stattdessen der Dateinamen angehängt wird, um die Liste der Werte für die `Compile` Elementtyp. Sie können kein Element aus einem Elementtyp entfernen, während der Auswertungsphase eines Builds.  
  
 Das folgende XML erstellt den gleichen Elementtyp durch Deklarieren beide Dateien in einem `Include` Attribut. Beachten Sie, dass die Dateinamen durch ein Semikolon voneinander getrennt sind.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="a-namebkmkcreating2a-creating-items-during-execution"></a><a name="BKMK_Creating2"></a> Erstellen von Elementen während der Ausführung  
 Elemente, die außerhalb [Ziel](../msbuild/target-element-msbuild.md) Elemente sind Werte im Rahmen der Auswertungsphase eines Builds zugewiesen. Während der anschließenden Ausführungsphase können Elemente erstellt oder auf folgende Weise geändert werden:  
  
-   Jede Aufgabe kann es sich um ein Element ausgeben. Ein Element ausgeben der [Aufgabe](../msbuild/task-element-msbuild.md) -Element muss ein untergeordnetes Element verfügen [Ausgabe](../msbuild/output-element-msbuild.md) Element mit einer `ItemName` Attribut.  
  
-   Die [CreateItem](../msbuild/createitem-task.md) Task kann ein Element ausgeben. Diese Verwendung ist veraltet.  
  
-   Ab .NET Framework 3.5 `Target` -Elemente [ItemGroup](../msbuild/itemgroup-element-msbuild.md) Elemente, enthalten möglicherweise, Artikel Elemente.  
  
##  <a name="a-namebkmkreferencingitemsa-referencing-items-in-a-project-file"></a><a name="BKMK_ReferencingItems"></a> Verweisen auf Elemente in einer Projektdatei  
 Elementtypen in der gesamten Projektdatei verweisen möchten, verwenden Sie die Syntax @(`ItemType`). Beispielsweise würden Sie den Elementtyp im vorherigen Beispiel verweisen, indem `@(Compile)`. Mithilfe dieser Syntax können Sie Elemente an Aufgaben übergeben, durch Angabe des Elements als Parameter für diese Aufgabe. Weitere Informationen finden Sie unter [Gewusst wie: Auswählen von Dateien für den Buildvorgang](../msbuild/how-to-select-the-files-to-build.md).  
  
 Standardmäßig sind die Elemente eines Elementtyps durch Semikolons (;) getrennt, wenn es erweitert wird. Verwenden Sie Syntax @(*ItemType*, "*Trennzeichen*') eine Trennzeichen als den Standardwert angeben. Weitere Informationen finden Sie unter [Gewusst wie: anzeigen, ein Element Liste durch Trennzeichen getrennten Elementliste](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="a-namebkmkwildcardsa-using-wildcards-to-specify-items"></a><a name="BKMK_Wildcards"></a> Verwenden von Platzhaltern zum Angeben von Elementen  
 Sie können die **, \*, und? Platzhalterzeichen an eine Gruppe von Dateien als Eingaben für einen Build, anstatt jede Datei separat aufzulisten.  
  
-   Die? entspricht ein einzelnes Zeichen.  
  
-   Die * entspricht null oder mehr Zeichen.  
  
-   Die ** entspricht einen partiellen Pfad.  
  
 Beispielsweise können Sie alle CS-Dateien im Verzeichnis, die die Projektdatei enthält, verwenden Sie das folgende Element in der Projektdatei angeben.  
  
```  
<CSFile Include="*.cs"/>  
```  
  
 Das folgende Element wählt alle VB-Dateien auf Laufwerk D: aus:  
  
```  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Weitere Informationen zu Platzhaltern finden Sie unter [Gewusst wie: Auswählen von Dateien für den Buildvorgang](../msbuild/how-to-select-the-files-to-build.md).  
  
##  <a name="a-namebkmkexcludeattributea-using-the-exclude-attribute"></a><a name="BKMK_ExcludeAttribute"></a> Verwenden das Exclude-Attribut  
 Können Elemente enthalten die `Exclude` -Attribut, das bestimmte Elemente (Dateien) aus dem Elementtyp ausschließt. Die `Exclude` Attribut wird normalerweise zusammen mit Platzhalterzeichen verwendet. Z. B. das folgende XML fügt alle CS-Dateien im Verzeichnis dem CSFile-Elementtyp, mit Ausnahme der `DoNotBuild.cs` Datei.  
  
```  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 Die `Exclude` Attribut wirkt sich nur auf die Elemente, die von hinzugefügt werden die `Include` -Attribut in das Element, das beide enthält. Im folgende Beispiel würde nicht die Datei Form1.cs, ausschließen, die im vorherigen Elementelement hinzugefügt wurde.  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Ausschließen von Dateien aus dem Build](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="a-namebkmkitemmetadataa-item-metadata"></a><a name="BKMK_ItemMetadata"></a> Elementmetadaten  
 Elemente können zusätzlich zu den Informationen in Metadaten enthalten die `Include` und `Exclude` Attribute. Diese Metadaten kann von Aufgaben verwendet werden, die Weitere Informationen zu den Elementen oder für die Batchverarbeitung von Aufgaben und Zielen erfordern. Weitere Informationen finden Sie unter [Batchverarbeitung](../msbuild/msbuild-batching.md).  
  
 Metadaten sind eine Auflistung von Schlüssel-Wert-Paare, die als untergeordnete Elemente des Item-Elements in der Projektdatei deklariert sind. Der Name des untergeordneten Elements ist der Name der Metadaten, und der Wert des untergeordneten Elements ist der Wert der Metadaten.  
  
 Die Metadaten, die das Element, das es enthält zugeordnet ist. Das folgende XML fügt beispielsweise `Culture` Metadaten mit dem Wert `Fr` "one.cs" und dem Element "Two.cs" von der CSFile-Elementtyp.  
  
```  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Ein Element kann über 0 (null) oder mehr Metadatenwerte verfügen. Sie können Metadaten zu einem beliebigen Zeitpunkt ändern. Wenn Sie die Metadaten auf einen leeren Wert festlegen, entfernen Sie ihn effektiv aus dem Build.  
  
###  <a name="a-namebkmkreferencingitemmetadataa-referencing-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> Verweisen auf Elementmetadaten in einer Projektdatei  
 Sie können Metadaten in der gesamten Projektdatei mit der Syntax %(verweisen`ItemMetadataName`). Wenn Mehrdeutigkeiten vorhanden ist, können Sie einen Verweis mit dem Namen des Elementtyps qualifizieren. Sie können z. B. %(angeben,*ItemType.ItemMetaDataName*). Im folgenden Beispiel wird die Metadaten anzeigen, die Message-Aufgabe Batch. Weitere Informationen zur Verwendung von Elementmetadaten für die Batchverarbeitung finden Sie unter [Elementmetadaten bei der Batchverarbeitung von Aufgaben](../msbuild/item-metadata-in-task-batching.md).  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Stuff Include="One.cs" >  
            <Display>false</Display>  
        </Stuff>  
        <Stuff Include="Two.cs">  
            <Display>true</Display>  
        </Stuff>  
    </ItemGroup>  
    <Target Name="Batching">  
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>  
    </Target>  
</Project>  
```  
  
###  <a name="a-namebkmkwellknownitemmetadataa-well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> Bekannte Elementmetadaten  
 Wenn einem Elementtyp ein Element hinzugefügt wird, werden diesem Element stets bekannten Metadaten zugewiesen. Beispielsweise verfügen alle Elemente die bekannte Metadaten `%(Filename)`, dessen Wert ist der Dateiname des Elements. Weitere Informationen finden Sie unter [bekannte Elementmetadaten](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="a-namebkmktransforminga-transforming-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> Umwandeln von Elementtypen mit Metadaten  
 Elementlisten können mit Metadaten in neue Elementlisten transformiert werden. Sie können z. B. einen Elementtyp transformieren `CppFiles` Elementen, cpp-Dateien in eine entsprechende Liste von OBJ-Dateien darstellen, mit dem Ausdruck, dessen `@(CppFiles -> '%(Filename).obj')`.  
  
 Der folgende Code erstellt ein `CultureResource` Elementtyp, das Kopien aller `EmbeddedResource` Elemente mit `Culture` Metadaten. Die `Culture` Metadatenwert wird der Wert der neuen Metadaten `CultureResource.TargetDirectory`.  
  
```  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 Weitere Informationen finden Sie unter [transformiert](../msbuild/msbuild-transforms.md).  
  
##  <a name="a-namebkmkitemdefinitionsa-item-definitions"></a><a name="BKMK_ItemDefinitions"></a> Elementdefinitionen  
 Ab .NET Framework 3.5, können Sie Standardmetadaten zu jedem Elementtyp hinzufügen, mit der [ItemDefinitionGroup-Element](../msbuild/itemdefinitiongroup-element-msbuild.md). Wie bekannte Metadaten werden die Standardmetadaten verknüpft mit allen Elementen des Elementtyps, die Sie angeben. Sie können die Standardmetadaten in einer Elementdefinition explizit überschreiben. Beispielsweise die folgende XML-CODE stellt die `Compile` Elemente "one.cs" und "three.cs" die Metadaten `BuildDay` mit dem Wert "Monday". Der Code bietet dem Element "two.cs" die Metadaten `BuildDay` mit dem Wert "Tuesday".  
  
```  
<ItemDefinitionGroup>  
    <Compile>  
        <BuildDay>Monday</BuildDay>  
    </Compile>  
</ItemDefinitionGroup>  
<ItemGroup>  
    <Compile Include="one.cs;three.cs" />  
    <Compile Include="two.cs">  
        <BuildDay>Tuesday</BuildDay>  
    </Compile>  
</ItemGroup>  
```  
  
 Weitere Informationen finden Sie unter [Elementdefinitionen](../msbuild/item-definitions.md).  
  
##  <a name="a-namebkmkattributeswithintargetsa-attributes-for-items-in-an-itemgroup-of-a-target"></a><a name="BKMK_AttributesWithinTargets"></a> Attribute für Elemente in einem ItemGroup-Element eines Ziels  
 Ab .NET Framework 3.5 `Target` -Elemente [ItemGroup](../msbuild/itemgroup-element-msbuild.md) Elemente, enthalten möglicherweise, Artikel Elemente. Die Attribute in diesem Abschnitt sind gültig, wenn sie für ein Element im angegeben sind eine `ItemGroup` die sich in einem `Target`.  
  
###  <a name="a-namebkmkremoveattributea-remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> Attribut entfernen  
 Elemente in einer `ItemGroup` eines Ziels enthalten möglicherweise die `Remove` -Attribut, das bestimmte Elemente (Dateien) aus dem Elementtyp entfernt. Dieses Attribut wurde in .NET Framework 3.5 eingeführt.  
  
 Im folgende Beispiel entfernt alle config-Dateien aus dem Compile-Elementtyp.  
  
```  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="a-namebkmkkeepmetadataa-keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> KeepMetadata-Attribut  
 Wenn ein Element in einem Ziel erstellt wird, kann das Element enthalten die `KeepMetadata` Attribut. Wenn dieses Attribut angegeben wird, werden nur die Metadaten, die in die durch Semikolons getrennte Liste der Namen angegeben wird aus dem Quellelement in das Zielelement übertragen. Ein leerer Wert für dieses Attribut entspricht nicht angegeben wird. Das `KeepMetadata` -Attribut wurde in .NET Framework 4.5 eingeführt.  
  
 Das folgende Beispiel zeigt, wie die `KeepMetadata` Attribut.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0">  
  
    <ItemGroup>  
        <FirstItem Include="rhinoceros">  
            <Class>mammal</Class>  
            <Size>large</Size>  
        </FirstItem>  
  
    </ItemGroup>  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />  
        </ItemGroup>  
  
        <Message Text="FirstItem: %(FirstItem.Identity)" />  
        <Message Text="  Class: %(FirstItem.Class)" />  
        <Message Text="  Size:  %(FirstItem.Size)"  />  
  
        <Message Text="SecondItem: %(SecondItem.Identity)" />  
        <Message Text="  Class: %(SecondItem.Class)" />  
        <Message Text="  Size:  %(SecondItem.Size)"  />  
    </Target>  
</Project>  
  
<!--  
Output:  
  FirstItem: rhinoceros  
    Class: mammal  
    Size:  large  
  SecondItem: rhinoceros  
    Class: mammal  
    Size:   
-->  
```  
  
###  <a name="a-namebkmkremovemetadataa-removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> RemoveMetadata-Attribut  
 Wenn ein Element in einem Ziel erstellt wird, kann das Element enthalten die `RemoveMetadata` Attribut. Wenn dieses Attribut angegeben ist, wird an das Zielelement mit Ausnahme von Metadaten aus dem Quellelement alle Metadaten übertragen, deren Namen in die durch Semikolons getrennte Liste der Namen enthalten sind. Ein leerer Wert für dieses Attribut entspricht nicht angegeben wird. Das `RemoveMetadata` -Attribut wurde in .NET Framework 4.5 eingeführt.  
  
 Das folgende Beispiel zeigt, wie die `RemoveMetadata` Attribut.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <MetadataToRemove>Size;Material</MetadataToRemove>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <Item1 Include="stapler">  
            <Size>medium</Size>  
            <Color>black</Color>  
            <Material>plastic</Material>  
        </Item1>  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />  
        </ItemGroup>  
  
        <Message Text="Item1: %(Item1.Identity)" />  
        <Message Text="  Size:     %(Item1.Size)" />  
        <Message Text="  Color:    %(Item1.Color)" />  
        <Message Text="  Material: %(Item1.Material)" />  
        <Message Text="Item2: %(Item2.Identity)" />  
        <Message Text="  Size:     %(Item2.Size)" />  
        <Message Text="  Color:    %(Item2.Color)" />  
        <Message Text="  Material: %(Item2.Material)" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: stapler  
    Size:     medium  
    Color:    black  
    Material: plastic  
  Item2: stapler  
    Size:       
    Color:    black  
    Material:   
-->  
```  
  
###  <a name="a-namebkmkkeepduplicatesa-keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> KeepDuplicates-Attribut  
 Wenn ein Element in einem Ziel erstellt wird, kann das Element enthalten die `KeepDuplicates` Attribut. `KeepDuplicates` ist ein `Boolean` -Attribut, das angibt, ob ein Element der Zielgruppe hinzugefügt werden soll, wenn das Element ein exaktes Duplikat eines vorhandenen Elements ist.  
  
 Das Element wird hinzugefügt, wenn die Quell- und Ziel-Element den gleichen Include-Wert, aber unterschiedliche Metadaten aufweisen, selbst wenn `KeepDuplicates` Wert `false`. Ein leerer Wert für dieses Attribut entspricht nicht angegeben wird. Das `KeepDuplicates` -Attribut wurde in .NET Framework 4.5 eingeführt.  
  
 Das folgende Beispiel zeigt, wie die `KeepDuplicates` Attribut.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Item1 Include="hourglass;boomerang" />  
        <Item2 Include="hourglass;boomerang" />  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item1 Include="hourglass" KeepDuplicates="false" />  
            <Item2 Include="hourglass" />  
        </ItemGroup>  
  
        <Message Text="Item1: @(Item1)" />  
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />  
        <Message Text="Item2: @(Item2)" />  
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: hourglass;boomerang  
    hourglass  Count: 1  
    boomerang  Count: 1  
  Item2: hourglass;boomerang;hourglass  
    hourglass  Count: 2  
    boomerang  Count: 1  
-->  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild-Konzepte](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild1.md)   
 [Gewusst wie: Auswählen von Dateien für den Buildvorgang](../msbuild/how-to-select-the-files-to-build.md)   
 [Gewusst wie: Ausschließen von Dateien vom Buildvorgang](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Gewusst wie: Anzeigen einer durch Kommas getrennten](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Elementdefinitionen](../msbuild/item-definitions.md)   
 [Batchverarbeitung](../msbuild/msbuild-batching.md)   
 [Item-Element (MSBuild)](../msbuild/item-element-msbuild.md)