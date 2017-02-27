---
title: "Item Functions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, Item functions"
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Item Functions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ab MSBuild 4.0 kann Code in Aufgaben und Zielen Elementfunktionen aufrufen, um Informationen über die Elemente im Projekt abzurufen.  Diese Funktionen vereinfachen das Abrufen von Distinct\(\)\-Elementen, und mit ihnen erfolgt der Abruf schneller als beim Durchlaufen der Elemente.  
  
## Zeichenfolgen\-Element\-Funktionen  
 Sie können Zeichenfolgenmethoden und Eigenschaften in .NET Framework verwenden, um jeden Elementwert an auszuführen.  Für <xref:System.String>\-Methoden geben Sie den Methodennamen an.  Für <xref:System.String>\-Eigenschaften geben Sie den Eigenschaftennamen nach "get\_" an.  
  
 Bei Elementen, die mehrere Zeichenfolgen, die Zeichenfolgenmethode oder die Eigenschaftausführungen auf jeder Zeichenfolge enthalten.  
  
 Das folgende Beispiel zeigt, wie diese String Elementfunktionen verwendet.  
  
```  
<ItemGroup>  
    <theItem Include="andromeda;tadpole;cartwheel" />  
</ItemGroup>  
  
<Target Name = "go">  
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />  
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />  
    <Message Text="Length   @(theItem->get_Length())" />  
    <Message Text="Chars    @(theItem->get_Chars(2))" />  
</Target>  
  
  <!--  
  Output:  
    IndexOf  3;-1;2  
    Replace  andromeda;pinwheel;cartwheel  
    Length   9;7;9  
    Chars    d;d;r  
  -->  
```  
  
## Systeminterne Element\-Funktionen  
 In der folgenden Tabelle werden die systeminternen Funktionen aufgeführt, die für Elemente verfügbar sind.  
  
|Funktion|Beispiel|Description|  
|--------------|--------------|-----------------|  
|`Count`|`@(MyItem->Count())`|Gibt die Anzahl der Elemente zurück.|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|Gibt die Entsprechung von `Path.DirectoryName` für jedes Element zurück.|  
|`Distinct`|`@(MyItem->Distinct())`|Gibt Elemente zurück, die `Include` unterschiedliche Werte aufweisen.  Metadaten werden ignoriert.  Beim Vergleich wird die Groß\- und Kleinschreibung nicht berücksichtigt.|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Gibt Elemente zurück, die `itemspec` unterschiedliche Werte aufweisen.  Metadaten werden ignoriert.  Beim Vergleich wird die Groß\- und Kleinschreibung berücksichtigt.|  
|`Reverse`|`@(MyItem->Reverse())`|Gibt die in umgekehrter Reihenfolge zurück.|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Gibt `boolean` zurück, um anzugeben, ob jedes Element den angegebenen Metadaten und den Wert hat.  Beim Vergleich wird die Groß\- und Kleinschreibung nicht berücksichtigt.|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Gibt Elemente mit gelöschten Metadaten zurück.  Nur `itemspec` wird beibehalten.|  
|`HasMetadata`|`@(MyItem->HasMetadataValue("MetadataName")`|Gibt Elemente zurück, die den angegebenen Metadatennamen haben.  Beim Vergleich wird die Groß\- und Kleinschreibung nicht berücksichtigt.|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Gibt die Werte der Metadaten zurück, die den Metadaten verfügen.|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue")`|Gibt Elemente zurück, die den angegebenen Metadaten und den Wert haben.  Beim Vergleich wird die Groß\- und Kleinschreibung nicht berücksichtigt.|  
  
 Im folgenden Beispiel wird gezeigt, wie systeminternes Element funktioniert verwendet.  
  
```  
<ItemGroup>  
    <TheItem Include="first">  
        <Plant>geranium</Plant>  
    </TheItem>  
    <TheItem Include="second">  
        <Plant>algae</Plant>  
    </TheItem>  
    <TheItem Include="third">  
        <Plant>geranium</Plant>  
    </TheItem>  
</ItemGroup>  
  
<Target Name="go">  
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />  
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />  
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />  
    <Message Text=" " />  
    <Message Text="Count:   @(theItem->Count())" />  
    <Message Text="Reverse: @(theItem->Reverse())" />  
</Target>  
  
  <!--   
  Output:  
    MetaData:    geranium;algae;geranium  
    HasMetadata: first;second;third  
    WithMetadataValue: first;third  
  
    Count:   3  
    Reverse: third;second;first  
  -->  
```  
  
## Siehe auch  
 [Items](../msbuild/msbuild-items.md)