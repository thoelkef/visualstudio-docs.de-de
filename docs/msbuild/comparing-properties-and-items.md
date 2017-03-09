---
title: "Vergleich von Eigenschaften und Elementen | Microsoft Docs"
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
  - "MSBuild Msbuild-Eigenschaften"
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Vergleich von Eigenschaften und Elementen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild-Eigenschaften und Elemente werden beide verwendet, um Informationen an Aufgaben übergeben, Bedingungen auszuwerten und speichern Sie die Werte, die in der gesamten Projektdatei verwiesen werden können.  
  
-   Eigenschaften sind Name / Wert-Paare. Weitere Informationen finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).  
  
-   Elemente sind Objekte, die in der Regel Dateien darstellen. Objekte können Metadaten-Sammlungen zugeordnet. Metadaten sind Name-Wert-Paare. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).  
  
## <a name="scalars-and-vectors"></a>Skalare und Vektoren  
 Da MSBuild-Eigenschaften Name-Wert-Paare sind, nur einen Zeichenfolgenwert aufweisen, werden sie häufig beschrieben als *skalare*. Da MSBuild-Elementtypen Listen von Elementen sind, werden sie häufig beschrieben als *Vektor*. Allerdings in der Praxis Eigenschaften können mehrere Werte darstellen, und Elementtypen können 0 (null) oder ein Element aufweisen.  
  
### <a name="target-dependency-injection"></a>Target Dependency Injection  
 Um zu sehen, wie Eigenschaften für mehrere Werte darstellen können, sollten Sie ein häufiges Verwendungsmuster zum Hinzufügen eines Ziels, um eine Liste der zu erstellenden Ziele aus. Diese Liste wird in der Regel durch einen Eigenschaftswert, mit dem Zielnamen durch Semikolons getrennt dargestellt.  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Die `BuildDependsOn` Eigenschaft wird normalerweise verwendet, als Argument eines Ziels `DependsOnTargets` effektiv konvertieren in eine Elementliste-Attribut. Diese Eigenschaft kann überschrieben werden, um ein Ziel hinzuzufügen oder die Ausführungsreihenfolge der Ziele zu ändern. Beispiel:  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        $(BuildDependsOn);  
        CustomBuild;  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 der Zielliste das Ziel CustomBuild zu hinzugefügt erteilen `BuildDependsOn` den Wert `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.  
  
 Ab MSBuild 4.0 ist die Abhängigkeitsinjektion Ziel veraltet. Verwenden der `AfterTargets` und `BeforeTargets` stattdessen Attribute. Weitere Informationen finden Sie unter [Buildreihenfolge für Ziele](../msbuild/target-build-order.md).  
  
### <a name="conversions-between-strings-and-item-lists"></a>Konvertierungen zwischen Zeichenfolgen und Elementlisten  
 MSBuild führt Konvertierungen von Elementtypen und Zeichenfolgenwerte nach Bedarf. Um zu sehen, wie eine Elementliste ein String-Wert werden kann, erwägen Sie, was geschieht, wenn ein Elementtyp als Wert der MSBuild-Eigenschaft verwendet wird:  
  
```  
<ItemGroup>  
    <OutputDir Include="KeyFiles\;Certificates\" />  
  </ItemGroup>  
<PropertyGroup>  
    <OutputDirList>@(OutputDir)</OutputDirList>  
</PropertyGroup>  
```  
  
 Der Elementtyp OutputDir hat ein `Include` Attribut mit dem Wert "Schlüsseln\\; Zertifikate\\". MSBuild analysiert diese Zeichenfolge in zwei Elemente: Zertifikate und KeyFiles\\\. Wenn der OutputDir-Elementtyp als Wert der Eigenschaft OutputDirList verwendet wird, konvertiert oder den Elementtyp zur durch Semikolons getrennte Zeichenfolge "vereinfacht" MSBuild "Schlüsseln\\; Zertifikate\\".  
  
## <a name="properties-and-items-in-tasks"></a>Eigenschaften und Elemente in Aufgaben  
 Eigenschaften und Elemente werden als Eingaben und Ausgaben von MSBuild-Aufgaben verwendet. Weitere Informationen finden Sie unter [Aufgaben](../msbuild/msbuild-tasks.md).  
  
 Eigenschaften werden als Attribute an Aufgaben übergeben. Innerhalb der Aufgabe wird eine MSBuild-Eigenschaft durch einen Eigenschaftentyp dargestellt, dessen Wert in und aus einer Zeichenfolge konvertiert werden kann. Die unterstützten Datentypen gehören `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string`, sowie alle Typen, <xref:System.Convert.ChangeType%2A> behandeln können.  
  
 Elemente werden an Aufgaben übergeben <xref:Microsoft.Build.Framework.ITaskItem> Objekte. Innerhalb der Aufgabe <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> stellt den Wert des Elements und <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> Ruft die Metadaten ab.  
  
 Die Elementliste eines Elementtyps kann als Array von übergeben werden `ITaskItem` Objekte. Ab .NET Framework 3.5 können Elemente können entfernt werden aus einer Elementliste in einem Ziel mithilfe der `Remove` Attribut. Da Elemente aus einer Elementliste entfernt werden können, kann ein Elementtyp 0 (null) Elemente verfügen. Wenn eine Elementliste an eine Aufgabe übergeben wird, sollte der Code in der Aufgabe diese Möglichkeit überprüfen.  
  
## <a name="property-and-item-evaluation-order"></a>Eigenschaft und die Reihenfolge der Auswertung von Element  
 Während der Auswertungsphase eines Builds werden die importierte Dateien in den Build in der Reihenfolge integriert werden. Eigenschaften und Elemente werden in drei Durchläufen in der folgenden Reihenfolge definiert:  
  
-   Eigenschaften sind definiert und geändert, in der Reihenfolge, in der sie angezeigt werden.  
  
-   Elementdefinitionen sind definiert und geändert, in der Reihenfolge, in der sie angezeigt werden.  
  
-   Elemente werden definiert und geändert, in der Reihenfolge, in der sie angezeigt werden.  
  
 Während der Ausführungsphase eines Builds werden Eigenschaften und Elemente, die in den Zielen definiert werden zusammen in einer einzelnen Phase in der Reihenfolge ausgewertet werden.  
  
 Dies ist jedoch nicht die ganze Geschichte. Wenn eine Eigenschaft, eine Elementdefinition oder ein Element definiert ist, wird der Wert ausgewertet. Die Auswertung eines Ausdrucks erweitert die Zeichenfolge, die den Wert angibt. Die Erweiterung der Zeichenfolge ist abhängig von der Build-Phase. Hier ist eine detailliertere und Auswertungsreihenfolge:  
  
-   Während der Auswertungsphase eines Builds:  
  
    -   Eigenschaften sind definiert und geändert, in der Reihenfolge, in der sie angezeigt werden. Eigenschaftenfunktionen werden ausgeführt. Eigenschaftswerte der Form $(propertyname) werden in den Ausdrücken erweitert. Der Eigenschaftswert wird auf den erweiterten Ausdruck festgelegt.  
  
    -   Elementdefinitionen sind definiert und geändert, in der Reihenfolge, in der sie angezeigt werden. Eigenschaftenfunktionen wurden bereits in den Ausdrücken erweitert. Metadatenwerte werden auf die erweiterten Ausdrücke festgelegt.  
  
    -   Elementtypen werden definiert und geändert, in der Reihenfolge, in der sie angezeigt werden. Element Werte in der Form @(ItemType) werden erweitert. Elementtransformationen werden ebenfalls erweitert. Funktionen, Eigenschaften und Werte wurden bereits in den Ausdrücken erweitert. Der Elementwerte und die Metadatenwerte werden auf die erweiterten Ausdrücke festgelegt.  
  
-   Während der Ausführungsphase eines Builds:  
  
    -   Eigenschaften und Elemente, die in den Zielen definiert sind, werden zusammen in der Reihenfolge ausgewertet werden. Eigenschaftenfunktionen werden ausgeführt, und Eigenschaftswerte werden in Ausdrücken erweitert. Elementwerte und Elementtransformationen werden ebenfalls erweitert. Die Eigenschaftswerte, Elementtypwerte und Metadatenwerte werden auf die erweiterten Ausdrücke festgelegt.  
  
### <a name="subtle-effects-of-the-evaluation-order"></a>Raffinierten Effekten, der die Reihenfolge der Auswertung  
 In der Auswertungsphase eines Builds vorausgeht Auswertung Element-Bewertung. Trotzdem können Eigenschaften Werte besitzen, die scheinbar von Elementwerten abhängen. Betrachten Sie das folgende Skript aus.  
  
```  
<ItemGroup>  
    <KeyFile Include="KeyFile.cs">  
        <Version>1.0.0.3</Version>  
    </KeyFile>  
</ItemGroup>  
<PropertyGroup>  
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
</PropertyGroup>  
<Target Name="AfterBuild">  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Die Message-Aufgabe ausgeführt, wird diese Meldung angezeigt:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
 Grund hierfür ist der Wert des `KeyFileVersion` ist eigentlich die Zeichenfolge "@(KeyFile->'%(Version)')". Element und Elementtransformationen wurden nicht erweitert, wenn die Eigenschaft zunächst definiert wurde, damit der `KeyFileVersion` -Eigenschaft den Wert des nicht erweiterten Zeichenfolge zugewiesen wurde.  
  
 Während der Ausführungsphase des Builds, bei der Verarbeitung der Message-Aufgabe MSBuild erweitert die Zeichenfolge "@(KeyFile->'%(Version)')" "1.0.0.3" ergeben.  
  
 Beachten Sie, dass die gleiche Nachricht angezeigt wird, auch wenn die Eigenschaften- und Elementgruppen Reihenfolge umgekehrter.  
  
 Als zweites Beispiel beachten Sie, was passieren kann, wenn die Eigenschaften- und Elementgruppen in den Zielen befinden:  
  
```  
<Target Name="AfterBuild">  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Die Message-Aufgabe wird diese Meldung angezeigt:  
  
```  
KeyFileVersion:   
```  
  
 Dies ist, da während der Ausführungsphase des Builds, Eigenschaften- und Elementgruppen in den Zielen definierte ausgewertet werden von oben nach unten zur gleichen Zeit. Wenn `KeyFileVersion` definiert ist, `KeyFile` ist unbekannt. Daher wird die Elementtransformation auf eine leere Zeichenfolge erweitert.  
  
 In diesem Fall werden beim Umkehren der Reihenfolge der Gruppen und die ursprüngliche Nachricht wiederhergestellt:  
  
```  
<Target Name="AfterBuild">  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Der Wert der `KeyFileVersion` festgelegt ist, klicken Sie auf "1.0.0.3" und nicht auf "@(KeyFile->'%(Version)')". zeigt diese Meldung an die Message-Aufgabe:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Konzepte](../msbuild/msbuild-advanced-concepts.md)