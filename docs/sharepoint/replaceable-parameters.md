---
title: "Ersetzbare Parameter | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Ersetzbare Parameter [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Ersetzbare Parameter"
  - "SharePoint-Entwicklung in Visual Studio, Token"
  - "Token [SharePoint-Entwicklung in Visual Studio]"
ms.assetid: 3c46bbb1-0a98-495c-9fd1-dc57a6aedc11
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Ersetzbare Parameter
  Ersetzbare Parameter oder *Token* können in Projektdateien verwendet werden, um Werte für SharePoint\-Lösungselemente bereitzustellen, deren tatsächliche Werte zur Entwurfszeit nicht bekannt sind.  Sie sind in der Funktion zu standardmäßigen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Vorlagentoken ähnlich.  Weitere Informationen finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  
  
## Tokenformat  
 Token beginnen und enden mit einem Dollarzeichen \($\).  Alle verwendeten Token werden durch tatsächliche Werte ersetzt, wenn ein Projekt zur Bereitstellungszeit in einer SharePoint\-Lösungspaketdatei \(WSP\) verpackt wird.  Beispielsweise kann das Token **$SharePoint.Package.Name$** in die Zeichenfolge "Test SharePoint Package" aufgelöst werden.  
  
## Tokenregeln  
 Für Token gelten die folgenden Regeln:  
  
-   Token können an beliebigen Positionen in einer Zeile angegeben werden.  
  
-   Token können nicht mehrere Zeilen umfassen.  
  
-   Ein Token kann mehrmals in derselben Zeile und in derselben Datei angegeben werden.  
  
-   Verschiedene Token können in derselben Zeile angegeben werden.  
  
 Token, die diesen Regeln nicht folgen, werden ignoriert, ohne dass eine Warnung oder ein Fehler bereitgestellt wird.  
  
 Die Ersetzung von Token durch Zeichenfolgenwerte erfolgt direkt nach der Manifesttransformation, sodass von einem Benutzer bearbeitete Manifestvorlagen Token verwenden können.  
  
### Tokennamensauflösung  
 In den meisten Fällen wird ein Token unabhängig vom Container zu einem bestimmten Wert aufgelöst.  Wenn sich das Token jedoch auf ein Paket oder eine Funktion bezieht, hängt der Wert des Tokens vom Container ab.  Wenn eine Funktion z. B. in Paket A enthalten ist, wird das Token `$SharePoint.Package.Name$` zum Wert "Paket A" aufgelöst. Ist die gleiche Funktion in Paket B enthalten, wird `$SharePoint.Package.Name$` zu "Paket B" aufgelöst.  
  
## Liste von Token  
 In der folgenden Tabelle sind die verfügbaren Token aufgeführt.  
  
|Name|**Beschreibung**|  
|----------|----------------------|  
|$SharePoint.Project.FileName$|Der Name der enthaltenden Projektdatei, z. B. "NewProj.csproj".|  
|$SharePoint.Project.FileNameWithoutExtension$|Der Name der enthaltenden Projektdatei ohne Dateinamenerweiterung.  Beispiel: "NewProj".|  
|$SharePoint.Project.AssemblyFullName$|Der Anzeigename \(starker Name\) der Ausgabeassembly des enthaltenden Projekts.|  
|$SharePoint.Project.AssemblyFileName$|Der Name der Ausgabeassembly des enthaltenden Projekts.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Der Name der Ausgabeassembly des enthaltenden Projekts ohne Dateinamenerweiterung.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Das öffentliche Schlüsseltoken der Ausgabeassembly des enthaltenden Projekts, konvertiert in eine Zeichenfolge. \(16 Zeichen in "x2"\-Hexadezimalformat.\)|  
|$SharePoint.Package.Name$|Der Name des enthaltenden Pakets.|  
|$SharePoint.Package.FileName$|Der Name der Definitionsdatei des enthaltenden Pakets.|  
|$SharePoint.Package.FileNameWithoutExtension$|Der Name der Definitionsdatei des enthaltenden Pakets \(ohne Dateinamenerweiterung\).|  
|$SharePoint.Package.Id$|Die SharePoint\-ID für das enthaltende Paket.  Wenn eine Funktion in mehreren Paketen verwendet wird, ändert sich dieser Wert.|  
|$SharePoint.Feature.FileName$|Der Name der Definitionsdatei der enthaltenden Funktion, z. B. "Feature1.feature".|  
|$SharePoint.Feature.FileNameWithoutExtension$|Der Name der Definitionsdatei der Funktion ohne die Dateinamenerweiterung.|  
|$SharePoint.Feature.DeploymentPath$|Der Name des Ordners, der die Funktion im Paket enthält.  Dieses Token entspricht der Bereitstellungspfadeigenschaft im Funktions\-Designer.  Beispiel: "Project1\_Feature1".|  
|$SharePoint.Feature.Id$|Die SharePoint\-ID der enthaltenden Funktion.  Dieses Token sowie alle Token auf Funktionsebene können nur von Dateien verwendet werden, die über eine Funktion in ein Paket eingeschlossen wurden. Für Dateien, die einem Paket direkt außerhalb einer Funktion hinzugefügt wurden, ist dies nicht möglich.|  
|$SharePoint.ProjectItem.Name$|Der mit **ISharePointProjectItem.Name** abgerufene Name des Projektelements \(nicht der Dateiname\).|  
|$SharePoint.Type.GUID.AssemblyQualifiedName$\<\>|Der durch die Assembly qualifizierte Name des Typs, der der [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] des Tokens entspricht.  Das Format [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] wird klein geschrieben Format entspricht dem Guid.ToString \("D"\) \(das heißt,\-. Es|  
|$SharePoint.Type.GUID.FullName$\<\>|Der vollständige Name des Typs, der der GUID im Token entspricht.  Für das Format der GUID wird die Kleinschreibung verwendet. Es entspricht dem Guid.ToString \("D"\)\-Format \(d. h. xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx\).|  
  
## Hinzufügen von Erweiterungen zur Liste der Tokenersatz\-Dateinamenerweiterungen  
 Obwohl Token theoretisch von jeder Datei verwendet werden können, die zu einem im Paket enthaltenen SharePoint\-Projektelement gehört, sucht [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] standardmäßig nur in Paketdateien, Manifestdateien und Dateien mit den folgenden Dateinamenerweiterungen nach Token:  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Webpart  
  
-   DWP  
  
 Diese Erweiterungen werden durch das `<TokenReplacementFileExtensions>`\-Element in der Datei "Microsoft.VisualStudio.SharePoint.targets" definiert, im Ordner  "…\\\<Programme\>\\MSBuild\\Microsoft\\VisualStudio\\v11.0\\SharePointTools.  
  
 Sie können der Liste jedoch zusätzliche Dateinamenerweiterungen hinzufügen.  Hierzu, fügen Sie ein `<TokenReplacementFileExtensions>`\-Element einer Eigenschaftengruppe in der SharePoint\-Projektdatei hinzu die vor dem \<Import\> der SharePoint\-Zieledatei definiert wird.  
  
> [!NOTE]  
>  Da die Tokenersetzung nach dem Kompilieren eines Projekts erfolgt, sollten keine Dateierweiterungen für Dateitypen hinzugefügt werden, die kompiliert werden \(z. B. .cs, .vb oder .resx\).  Token werden nur in Dateien ersetzt, die nicht kompiliert werden.  
  
 Fügen Sie einer CSPROJ\-Datei z. B. Folgendes hinzu, um der Liste der Dateinamenerweiterungen für die Tokenersetzung die Erweiterungen ".myextension" und ".yourextension" hinzuzufügen:  
  
```  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 Alternativ können Sie der TARGETS\-Datei die Erweiterung direkt hinzufügen.  Hierdurch wird jedoch die Liste der Erweiterungen für alle im lokalen System verpackten SharePoint\-Projekte und nicht nur für Ihr Projekt geändert.  Dies ist möglicherweise zweckmäßig, wenn Sie der einzige Entwickler im System sind, oder wenn dies für die meisten Ihrer Projekte erforderlich ist.  Da dieser Ansatz jedoch systemspezifisch ist, ist er nicht sehr übertragbar. Es wird daher empfohlen, Erweiterungen stattdessen der Projektdatei hinzuzufügen.  
  
## Siehe auch  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  