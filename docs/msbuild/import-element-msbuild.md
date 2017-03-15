---
title: "Import-Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Import"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Import-Element [MSBuild]"
  - "<Import>-Element [MSBuild]"
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Import-Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Importiert die Inhalte einer Projektdatei in eine andere Projektdatei.  
  
 \<Project\>  
 \<Import\>  
  
## Syntax  
  
```  
<Import Project="ProjectPath"  
    Condition="'String A'=='String B'" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Project`|Erforderliches Attribut.<br /><br /> Der Pfad der zu importierenden Projektdatei. Der Pfad kann Platzhalter enthalten. Die entsprechenden Dateien werden in sortierter Reihenfolge importiert. Mit dieser Funktion können Sie Code einem Projekt hinzufügen, indem Sie einfach die Codedatei einem Verzeichnis hinzufügen.|  
|`Condition`|Optionales Attribut.<br /><br /> Eine auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Untergeordnete Elemente  
 Keine  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projektdatei.|  
|[ImportGroup](../msbuild/importgroup-element.md)|Enthält eine Sammlung von `Import`\-Elementen, die unter einer optionalen Bedingung gruppiert sind.|  
  
## Hinweise  
 Mithilfe des `Import`\-Elements können Sie Code wiederverwenden, der in vielen Projektdateien verwendet wird. Dies erleichtert die Verwaltung des Codes, da jedes von Ihnen ausgeführte Update für den freigegebenen Code an alle Projekte weitergegeben wird, die ihn importieren.  
  
 Gemäß der Konvention werden freigegebene importierte Projektdateien als TARGETS\-Dateien gespeichert, sie sind jedoch [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Standardprojektdateien.[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] hindert Sie nicht daran, ein Projekt zu importieren, das eine andere Dateinamenerweiterung besitzt. Es wird jedoch empfohlen, aus Konsistenzgründen die Erweiterung TARGETS zu verwenden.  
  
 Relative Pfade in importierten Projekten werden relativ zum Verzeichnis des importierenden Projekts interpretiert. Wenn eine Projektdatei in verschiedene Projektdateien an unterschiedliche Speicherorte importiert wird, werden daher die relativen Pfade in der importierten Projektdatei unterschiedlich für jedes importierte Projekt interpretiert.  
  
 Allen für [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] reservierten Eigenschaften, die sich auf die Projektdatei beziehen, z.B. `MSBuildProjectDirectory` und `MSBuildProjectFile`, und auf die in einem importierten Projekt verwiesen wird, werden basierend auf der importierenden Projektdatei Werte zugewiesen.  
  
 Wenn das importierte Projekt über kein `DefaultTargets`\-Attribut verfügt, werden importierte Projekte in der Reihenfolge untersucht, in der Sie importiert wurden und der Wert des ersten gefundenen `DefaultTargets`\-Attributs wird daraufhin verwendet. Wenn beispielsweise ProjectA ProjectB und ProjectC \(in dieser Reihenfolge\) importiert, und ProjectB importiert ProjectD, prüft [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zuerst, ob `DefaultTargets` in ProjectA angegeben ist, durchsucht dann ProjectB und ProjectD und schließlich ProjectC.  
  
 Das Schema eines importierten Projekts ist identisch mit dem Schema eines Standardprojekts. Obwohl [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] möglicherweise ein importiertes Projekt erstellen kann, ist es unwahrscheinlich, da ein importiertes Projekt normalerweise keine Informationen enthält, wie Eigenschaften festzulegen sind oder die Reihenfolge, in der Ziele ausgeführt werden. Das importierte Projekt ist abhängig vom Projekt in das es importiert wird, um diese Information bereitzustellen.  
  
> [!NOTE]
>  Während bedingte Import\-Anweisungen in Befehlszeilen\-MSBuilds arbeiten, arbeiten Sie nicht mit MSBuild in der integrierten Entwicklungsumgebung \(Integrated Development Environment; IDE\) von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Bedingte Importe werden mithilfe der Konfiguration und den Plattformwerten ausgewertet, die beim Laden des Projekts festgelegt werden. Wenn anschließend Änderungen vorgenommen werden, die eine erneute Auswertung der Bedingungen in der Projektdatei erfordern, z.B. Ändern der Plattform, wertet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die Bedingungen für Eigenschaften und Elemente aus, jedoch nicht für Importe. Da die Importbedingung nicht erneut ausgewertet wird, wird der Import übersprungen.  
>   
>  Um dies zu umgehen, fügen Sie bedingte Importe den TARGETS\-Dateien hinzu, oder fügen Sie Code in einen bedingten Block ein, z.B. den Block [Choose Element \(MSBuild\)](../msbuild/choose-element-msbuild.md).  
  
## Platzhalter  
 In .NET Framework 4 erlaubt MSBuild Platzhalter im Attribut „Projekt“. Wenn Platzhalter vorhanden sind, werden alle gefundenen Übereinstimmungen \(für die Reproduzierbarkeit\) sortiert und dann werden sie in dieser Reihenfolge importiert, so als ob diese explizit festgelegt wurde.  
  
 Dies ist hilfreich, wenn Sie einen Erweiterungspunkt zur Verfügung stellen möchten, sodass jemand anderes eine Datei importieren kann, ohne dass Sie explizit der zu importierenden Datei den Dateinamen hinzufügen müssen. Zu diesem Zweck enthält Microsoft.Common.Targets die folgende Zeile am Anfang der Datei.  
  
```  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  
  
## Beispiel  
 Das folgende Beispiel zeigt ein Projekt, das über mehrere Elemente und Eigenschaften verfügt und eine allgemeine Projektdatei importiert.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <resourcefile>Strings.resx</resourcefile>  
  
        <compiledresources>  
            $(O)\$(MSBuildProjectName).Strings.resources  
        </compiledresources>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs" />  
  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
    </ItemGroup>  
  
    <Import Project="$(CommonLocation)\General.targets" />  
</Project>  
```  
  
## Siehe auch  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [How to: Use the Same Target in Multiple Project Files](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)