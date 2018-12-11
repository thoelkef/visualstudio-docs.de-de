---
title: MSBuild-Elemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d517d3fd24b17c33a7bba9f888fbb904631be5f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851932"
---
# <a name="msbuild-items"></a>MSBuild-Elemente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
MSBuild-Elemente sind Eingaben in das Buildsystem. In der Regel handelt es sich dabei um Dateien. Elemente werden auf Grundlage benutzerdefinierter Elementnamen in Elementtypen gruppiert. Elementtypen sind benannte Listen von Elementen, die als Parameter für Aufgaben verwendet werden können. In den Aufgaben werden die Schritte des Buildprozesses mithilfe der Elementwerte ausgeführt.  
  
 Da Elemente anhand des Elementtyps benannt werden, zu dem sie gehören, können die Begriffe „Element“ und „Elementwert“ synonym verwendet werden.  
  
 **Inhalt**  
  
-   [Erstellen von Elementen in einer Projektdatei](#BKMK_Creating1)  
  
-   [Erstellen von Elementen während der Ausführung](#BKMK_Creating2)  
  
-   [Verweisen auf Elemente in einer Projektdatei](#BKMK_ReferencingItems)  
  
-   [Verwenden von Platzhaltern zum Angeben von Elementen](#BKMK_Wildcards)  
  
-   [Verwenden des Exclude-Attributs](#BKMK_ExcludeAttribute)  
  
-   [Elementmetadaten](#BKMK_ItemMetadata)  
  
    -   [Verweisen auf Elementmetadaten in einer Projektdatei](#BKMK_ReferencingItemMetadata)  
  
    -   [Bekannte Elementmetadaten](#BKMK_WellKnownItemMetadata)  
  
    -   [Umwandeln von Elementtypen mit Metadaten](#BKMK_Transforming)  
  
-   [Elementdefinitionen](#BKMK_ItemDefinitions)  
  
-   [Attribute für Elemente im ItemGroup-Element eines Ziels](#BKMK_AttributesWithinTargets)  
  
    -   [Entfernen des Attributs](#BKMK_RemoveAttribute)  
  
    -   [KeepMetadata-Attribut](#BKMK_KeepMetadata)  
  
    -   [RemoveMetadata-Attribut](#BKMK_RemoveMetadata)  
  
    -   [KeepDuplicates-Attribut](#BKMK_KeepDuplicates)  
  
##  <a name="BKMK_Creating1"></a>Erstellen von Elementen in einer Projektdatei  
 Elemente werden in der Projektdatei als untergeordnete Elemente eines [ItemGroup](../msbuild/itemgroup-element-msbuild.md)-Elements deklariert. Der Name des untergeordneten Elements ist der Typ des Elements. Durch das `Include`-Attribut des Elements wird angegeben, welche Elemente (Dateien) in den jeweiligen Elementtyp aufgenommen werden sollen. Im folgenden XML wird z.B. der mit `Compile` benannte Elementtyp erstellt, der zwei Dateien umfasst.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Das Element „file2.cs“ ersetzt nicht das Element „file1.cs“. Stattdessen wird der Dateiname an die Liste der Werte für den `Compile`-Elementtyp angefügt. Elemente können nicht während der Auswertungsphase eines Builds aus Elementtypen entfernt werden.  
  
 Das folgende XML erstellt den gleichen Elementtyp, indem beide Dateien in einem `Include`-Attribut deklariert werden. Achten Sie darauf, dass die Dateinamen durch ein Semikolon voneinander getrennt sind.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="BKMK_Creating2"></a>Erstellen von Elementen während der Ausführung  
 Elementen außerhalb von [Ziel](../msbuild/target-element-msbuild.md)-Elementen werden während der Auswertungsphase eines Builds Werte zugewiesen. Während der anschließenden Ausführungsphase können Elemente wie folgt erstellt oder geändert werden:  
  
-   Jede Aufgabe kann ein Element ausgeben. Das [Aufgabe](../msbuild/task-element-msbuild.md)-Element muss über ein untergeordnetes [Ausgabe](../msbuild/output-element-msbuild.md)-Element mit einem `ItemName`-Attribut verfügen, damit ein Element ausgegeben werden kann.  
  
-   Die [CreateItem](../msbuild/createitem-task.md)-Aufgabe kann ein Element ausgeben. Diese Verwendung ist veraltet.  
  
-   Ab .NET Framework 3.5 enthalten `Target`-Elemente möglicherweise [ItemGroup](../msbuild/itemgroup-element-msbuild.md)-Elemente, die Item-Elemente enthalten.  
  
##  <a name="BKMK_ReferencingItems"></a>Verweisen auf Elemente in einer Projektdatei  
 Verwenden Sie die Syntax @(`ItemType`), um auf Elementtypen in der gesamten Projektdatei zu verweisen. Auf den Elementtyp aus dem vorherigen Beispiel würden Sie z.B. mithilfe von `@(Compile)` verweisen. Mithilfe dieser Syntax können Sie Elemente an Aufgaben übergeben, indem Sie den Elementtyp als einen Parameter dieser Aufgabe angeben. Weitere Informationen finden Sie unter [How to: Select the Files to Build (Vorgehensweise: Auswählen von Dateien für den Buildvorgang)](../msbuild/how-to-select-the-files-to-build.md).  
  
 Standardmäßig sind die Elemente eines Elementtyps durch Semikolons (;) getrennt, wenn er erweitert wird. Verwenden Sie die Syntax @(*ItemType*, „*Trennzeichen*“), um ein anderes Trennzeichen als den Standard anzugeben. Weitere Informationen finden Sie unter [How to: Display an Item List Separated with Commas (Vorgehensweise: Anzeigen einer durch Kommas getrennten Elementliste)](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="BKMK_Wildcards"></a>Verwenden von Platzhaltern zum Angeben von Elementen  
 Sie können die Platzhalterzeichen **, \* und ? verwenden, um eine Gruppe von Dateien als Eingaben für einen Build anzugeben. So müssen Sie nicht alle Dateien separat auflisten.  
  
- Das Platzhalterzeichen ? entspricht einem einzelnen Zeichen.  
  
- Das Platzhalterzeichen * entspricht 0 (null) oder mehr Zeichen.  
  
- Die Platzhalterzeichenfolge ** entspricht einem partiellen Pfad.  
  
  Sie können z.B. alle CS-Dateien im Verzeichnis der Projektdatei angeben, indem Sie das folgende Element in der Projektdatei verwenden.  
  
```  
<CSFile Include="*.cs"/>  
```  
  
 Das folgende Element wählt alle VB-Dateien auf Laufwerk D: aus:  
  
```  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Weitere Informationen zu Platzhalterzeichen finden Sie unter [How to: Select the Files to Build (Vorgehensweise: Auswählen von Dateien für den Buildvorgang)](../msbuild/how-to-select-the-files-to-build.md).  
  
##  <a name="BKMK_ExcludeAttribute"></a>Verwenden des Exclude-Attributs  
 Item-Elemente können das `Exclude`-Attribut enthalten, das bestimmte Elemente (Dateien) aus dem Elementtyp ausschließt. Das `Exclude`-Attribut wird normalerweise zusammen mit Platzhalterzeichen verwendet. Das folgende XML fügt z.B. dem Elementtyp der CS-Datei alle CS-Dateien im Verzeichnis mit Ausnahme der `DoNotBuild.cs`-Datei hinzu.  
  
```  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 Das `Exclude`-Attribut wirkt sich nur auf Elemente aus, die über das `Include`-Attribut in dem Item-Element hinzugefügt wurden, das beide enthält. Im folgenden Beispiel würde also nicht die im vorherigen Item-Element hinzugefügte Datei Form1.cs ausgeschlossen werden.  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Ausschließen von Dateien vom Buildvorgang](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="BKMK_ItemMetadata"></a>Elementmetadaten  
 Zusätzlich zu den Informationen aus den Attributen `Include` und `Exclude` können Elemente Metadaten enthalten. Diese Metadaten können von Aufgaben verwendet werden, die weitere Informationen zu den Elementen oder zur Batchverarbeitung von Aufgaben und Zielen benötigen. Weitere Informationen finden Sie unter [MSBuild Batching (Batchverarbeitung)](../msbuild/msbuild-batching.md).  
  
 Bei Metadaten handelt es sich um eine Auflistung von Schlüssel-Wert-Paaren, die in der Projektdatei als untergeordnete Elemente eines Item-Elements deklariert sind. Der Name des untergeordneten Elements entspricht dem Metadatennamen, und der Wert des untergeordneten Elements entspricht dem Metadatenwert.  
  
 Die Metadaten sind dem Item-Element zugeordnet, in dem sie enthalten sind. Das folgende XML fügt z.B. den Elementen „one.cs“ und „two.cs“ des Elementtyps der CS-Datei `Culture`-Metadaten mit dem Wert `Fr` hinzu.  
  
```  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Ein Element kann über 0 (null) oder mehr Metadatenwerte verfügen. Metadaten lassen sich immer ändern. Wenn Sie Metadaten auf einen leeren Wert festlegen, entfernen Sie sie unwiderruflich aus dem Build.  
  
###  <a name="BKMK_ReferencingItemMetadata"></a>Verweisen auf Elementmetadaten in einer Projektdatei  
 Mithilfe der Syntax %(`ItemMetadataName`) kann in der gesamten Projektdatei auf Elementmetadaten verwiesen werden. Bei Mehrdeutigkeiten können Sie mit dem Namen des Elementtyps einen Verweis qualifizieren. Sie können z.B. %(*ItemType.ItemMetaDataName*). angeben. Im folgenden Beispiel erfolgt die Batchverarbeitung der Meldungsaufgabe mithilfe der Anzeige von Metadaten. Weitere Informationen zur Verwendung von Elementmetadaten für die Batchverarbeitung finden Sie unter [Item Metadata in Task Batching (Elementmetadaten bei der Batchverarbeitung von Aufgaben)](../msbuild/item-metadata-in-task-batching.md).  
  
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
  
###  <a name="BKMK_WellKnownItemMetadata"></a>Bekannte Elementmetadaten  
 Wenn einem Elementtypen ein Element hinzugefügt wird, werden diesem Element bekannte Metadaten zugewiesen. So verfügen z.B. alle Elemente über die bekannten Metadaten `%(Filename)`, deren Wert dem Dateiname des Elements entspricht. Weitere Informationen finden Sie unter [Well-known Item Metadata (Bekannte Elementmetadaten)](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="BKMK_Transforming"></a>Umwandeln von Elementtypen mithilfe von Metadaten  
 Elementlisten können mithilfe von Metadaten in neue Elementlisten umgewandelt werden. Sie können z.B. mit dem Ausdruck `@(CppFiles -> '%(Filename).obj')` einen Elementtyp `CppFiles`, der über Elemente in Form von CPP-Dateien verfügt, in eine entsprechende Liste von OBJ-Dateien umwandeln.  
  
 Der folgende Code erstellt einen `CultureResource`-Elementtyp, der Kopien aller `EmbeddedResource`-Elemente mit `Culture`-Metadaten enthält. Der `Culture`-Metadatenwert ist nun der Wert der neuen Metadaten `CultureResource.TargetDirectory`.  
  
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
  
 Weitere Informationen finden Sie unter [MSBuild Transforms (Transformationen)](../msbuild/msbuild-transforms.md).  
  
##  <a name="BKMK_ItemDefinitions"></a>Elementdefinitionen  
 Ab .NET Framework 3.5 können Sie jedem Elementtypen mit dem [ItemDefinitionGroup-Element](../msbuild/itemdefinitiongroup-element-msbuild.md) Standardmetadaten hinzufügen. Standardmetadaten sind genau wie bekannte Metadaten allen Elementen des jeweils angegebenen Elementtyps zugeordnet. Standardmetadaten können in einer Elementdefinition explizit überschrieben werden. Das folgende XML vergibt z.B. an die `Compile`-Elemente „one.cs“ und „three.cs“ die Metadaten `BuildDay` mit dem Wert „Monday“. Der Code vergibt an das Element „two.cs“ die Metadaten `BuildDay` mit dem Wert „Tuesday“.  
  
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
  
 Weitere Informationen finden Sie unter [Item Definitions](../msbuild/item-definitions.md) (Elementdefinitionen).  
  
##  <a name="BKMK_AttributesWithinTargets"></a>Attribute für Elemente im ItemGroup-Element eines Ziels  
 Ab .NET Framework 3.5 enthalten `Target`-Elemente möglicherweise [ItemGroup](../msbuild/itemgroup-element-msbuild.md)-Elemente, die Item-Elemente enthalten. Die Attribute in diesem Abschnitt sind gültig, wenn sie für ein Element in einem `ItemGroup` angegeben werden, das ein `Target` ist.  
  
###  <a name="BKMK_RemoveAttribute"></a> Entfernen des Attributs  
 Elemente im `ItemGroup` eines Ziels enthalten möglicherweise das Attribut `Remove`, das bestimmte Elemente (Dateien) aus dem Elementtyp entfernt. Dieses Attribut wurde in .NET Framework 3.5 eingeführt.  
  
 Das folgende Beispiel veranschaulicht das Entfernen aller CONFIG-Dateien aus dem Elementtyp „Compile.  
  
```  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="BKMK_KeepMetadata"></a>KeepMetadata-Attribut  
 Wenn ein Element in einem Ziel erstellt wird, enthält das Item-Element möglicherweise das `KeepMetadata`-Attribut. Wenn dieses Attribut angegeben wird, werden nur die Metadaten aus dem Quellelement in das Zielelement übertragen, die in der durch Semikolons getrennten Liste von Namen angegeben sind. Wird für dieses Attribut ein leerer Wert angegeben, ist dies, als wäre nichts angegeben worden. Das `KeepMetadata`-Attribut wurde in .NET Framework 4.5 eingeführt.  
  
 Das folgende Beispiel veranschaulicht, wie das `KeepMetadata`-Attribut verwendet wird.  
  
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
  
###  <a name="BKMK_RemoveMetadata"></a> RemoveMetadata-Attribut  
 Wenn ein Element in einem Ziel erstellt wird, enthält das Item-Element möglicherweise das `RemoveMetadata`-Attribut. Wenn dieses Attribut angegeben wird, werden alle Metadaten aus dem Quellelement in das Zielelement übertragen. Davon ausgenommen sind Metadaten, deren Namen in der durch Semikolons getrennten Liste von Namen enthalten sind. Wird für dieses Attribut ein leerer Wert angegeben, ist dies, als wäre nichts angegeben worden. Das `RemoveMetadata`-Attribut wurde in .NET Framework 4.5 eingeführt.  
  
 Das folgende Beispiel veranschaulicht, wie das `RemoveMetadata`-Attribut verwendet wird.  
  
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
  
###  <a name="BKMK_KeepDuplicates"></a>KeepDuplicates-Attribut  
 Wenn ein Element in einem Ziel erstellt wird, enthält das Item-Element möglicherweise das `KeepDuplicates`-Attribut. `KeepDuplicates` ist ein `Boolean`-Attribut, das angibt, ob ein Element der Zielgruppe hinzugefügt werden soll, wenn es sich um ein exaktes Duplikat eines bereits vorhandenen Elements handelt.  
  
 Wenn Quell- und Zielelement denselben Include-Wert, aber unterschiedliche Metadaten aufweisen, wird das Element auch dann hinzugefügt, wenn für `KeepDuplicates` `false` festgelegt wurde. Wird für dieses Attribut ein leerer Wert angegeben, ist dies, als wäre nichts angegeben worden. Das `KeepDuplicates`-Attribut wurde in .NET Framework 4.5 eingeführt.  
  
 Das folgende Beispiel veranschaulicht, wie das `KeepDuplicates`-Attribut verwendet wird.  
  
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
 [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)  
 [MSBuild](msbuild.md)   
 [How to: Select the Files to Build (Vorgehensweise: Auswählen von Dateien für den Buildvorgang)](../msbuild/how-to-select-the-files-to-build.md)   
 [How to: Exclude Files from the Build (Vorgehensweise: Ausschließen von Dateien aus den Buildvorgang)](../msbuild/how-to-exclude-files-from-the-build.md)   
 [How to: Display an Item List Separated with Commas (Vorgehensweise: Anzeigen von durch Trennzeichen getrennten Elementlisten)](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Item Definitions (Elementdefinitionen)](../msbuild/item-definitions.md)   
 [Batching (Batchverarbeitung)](../msbuild/msbuild-batching.md)   
 [Item-Element (MSBuild)](../msbuild/item-element-msbuild.md)


