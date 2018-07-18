---
title: Item-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b55cadc738fb54b1a7fe07a2d891103c0daa755d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
ms.locfileid: "31576949"
---
# <a name="item-element-msbuild"></a>Item-Element (MSBuild)
Enthält ein benutzerdefiniertes Element und die zugehörigen Metadaten. Jedes Element, das in einem [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projekt verwendet wird, muss als untergeordnetes Element eines `ItemGroup` Elements angegeben werden.  

 \<Project>  
 \<ItemGroup>  
 \<Item>  

## <a name="syntax"></a>Syntax  

```  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  

## <a name="specify-metadata-as-attributes"></a>Metadaten als Attribute angeben
In MSBuild 15.1 oder höher können Metadaten mit einem Namen, der der aktuellen Liste der Attribute nicht widerspricht, optional als Attribut ausgedrückt werden.

Um beispielsweise eine Liste von NuGet-Paketen anzugeben, würden Sie normalerweise etwas wie die folgende Syntax verwenden.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

Nun können Sie jedoch die `Version`-Metadaten als Attribut übergeben, z.B. die folgende Syntax:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />  
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  

### <a name="attributes"></a>Attribute  

|Attribut|description|  
|---------------|-----------------|  
|`Include`|Optionales Attribut.<br /><br /> Die Datei oder der Platzhalter, die bzw. der in die Liste der Elemente eingeschlossen werden soll.|  
|`Exclude`|Optionales Attribut.<br /><br /> Die Datei oder der Platzhalter, die bzw. der aus der Liste der Elemente ausgeschlossen werden soll.|  
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|  
|`Remove`|Optionales Attribut.<br /><br /> Die Datei oder der Platzhalter, die bzw. der aus der Liste der Elemente entfernt werden soll.<br /><br />|  
|`KeepDuplicates`|Optionales Attribut.<br /><br /> Gibt an, ob ein Element der Zielgruppe hinzugefügt werden soll, wenn es sich um ein exaktes Duplikat eines vorhandenen Elements handelt. Wenn das Quell- und Zielelement den gleichen `Include`-Wert aber unterschiedliche Metadaten aufweisen, wird das Element auch dann hinzugefügt, wenn `KeepDuplicates` auf `false` festgelegt ist. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).<br /><br /> Dieses Attribut ist nur gültig, wenn es für ein Element in einer `ItemGroup` angegeben wird, die sich in einem `Target` befindet.|  
|`KeepMetadata`|Optionales Attribut.<br /><br /> Die Metadaten für die Quellelemente, die den Zielelementen hinzugefügt werden sollen. Nur die Metadaten, deren Namen in der durch Semikolon getrennten Liste angegeben werden, werden von einem Quellelement in ein Zielelement übertragen. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).<br /><br /> Dieses Attribut ist nur gültig, wenn es für ein Element in einer `ItemGroup` angegeben wird, die sich in einem `Target` befindet.|  
|`RemoveMetadata`|Optionales Attribut.<br /><br /> Die Metadaten für die Quellelemente, die nicht an der Zielelemente übertragen werden sollen. Alle Metadaten werden aus einem Quellelement in ein Zielelement mit Ausnahme von Metadaten übertragen, deren Namen in der durch Semikolons getrennten Liste der Namen enthalten sind. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).<br /><br /> Dieses Attribut ist nur gültig, wenn es für ein Element in einer `ItemGroup` angegeben wird, die sich in einem `Target` befindet.|  
|`Update`|Optionales Attribut. (Nur für .NET Core-Projekte in Visual Studio 2017 oder höher verfügbar.)<br /><br /> Ermöglicht es Ihnen, Metadaten einer Datei zu ändern, die mithilfe einer Glob enthalten waren.<br /><br />  Dieses Attribut ist nur gültig, wenn es für ein Element in einer `ItemGroup` angegeben wird, die sich nicht in einem `Target` befindet.|  

### <a name="child-elements"></a>Untergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Ein benutzerdefinierter Elementmetadatenschlüssel, der den Elementmetadatenwert enthält. Es kann keine oder mehrere `ItemMetadata`-Elemente in einem Element geben.|  

### <a name="parent-elements"></a>Übergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Grouping-Element für Elemente.|  

## <a name="remarks"></a>Hinweise  
 `Item`-Elemente definieren Eingaben ins Buildsystem und sind basierend auf ihren benutzerdefinierten Auflistungsnamen in Elementauflistungen gruppiert. Diese Elementtypen können als Parameter für [Aufgaben](../msbuild/msbuild-tasks.md) verwendet werden, die mithilfe der einzelnen Elemente in den Auflistungen die Schritte des Buildprozesses ausführen. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).  

 Mithilfe der Notation `@(`*myType*`)` kann eine Auflistung von Elementen vom Typ *myType* in einer durch Semikolons getrennten Liste von Zeichenfolgen erweitert und an einen Parameter übergeben werden. Wenn der Parameter vom Typ `string` ist, entspricht der Wert des Parameters der Liste der Elemente, die durch Semikolons getrennt sind. Wenn der Parameter ein Array von Zeichenfolgen ist (`string[]`), werden die einzelnen Elemente ins Array basierend auf der Position der Semikolons eingefügt. Ist der Task-Parameter vom Typ <xref:Microsoft.Build.Framework.ITaskItem>`[]`, entspricht der Wert dem Inhalt der Elementauflistung einschließlich ggf. angefügter Metadaten. Um jedes Element durch ein anderes Zeichen als ein Semikolon voneinander zu trennen, verwenden Sie die Syntax `@(`*myType*`, '`*Trennzeichen*`')`.  

 Das [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Modul kann Platzhalter wie `*` und `?` sowie rekursive Platzhalter wie `/**/*.cs` auswerten. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).  

## <a name="examples"></a>Beispiele  
 Im folgenden Codebeispiel wird veranschaulicht, wie zwei Elemente vom Typ `CSFile` deklariert werden. Das zweite deklarierte Element enthält Metadaten, für die `MyMetadata` auf `HelloWorld` festgelegt ist.  

```xml  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
Das folgende Codebeispiel zeigt, wie Sie das `Update`-Attribut verwenden, um die Metadaten in einer Datei namens somefile.cs zu ändern, die durch ein Glob-Muster enthalten war. (Nur für .NET Core-Projekte in Visual Studio 2017 oder höher verfügbar.)

```xml  
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>  
```  


## <a name="see-also"></a>Siehe auch  
 [Elemente](../msbuild/msbuild-items.md)   
 [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md) (Referenz zum Projektdateischema von MSBuild)
