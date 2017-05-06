---
title: "Von SharePoint unterst&#252;tzte MSBuild-Eigenschaften"
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
  - "SharePoint-Entwicklung in Visual Studio, MSBuild-Eigenschaften"
ms.assetid: 7b2b58c6-55cd-4682-a5d7-43874e70920d
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Von SharePoint unterst&#252;tzte MSBuild-Eigenschaften
  Jede [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]\-Eigenschaft, die in der Datei "Microsoft.VisualStudio.SharePoint.targets", in der Projektdatei oder in der Projektbenutzerdatei definiert ist, kann in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint\-Projekten verwendet werden.  Neben den allgemeinen, im Projekt angegebenen [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]\-Eigenschaften werden von SharePoint zusätzliche, für SharePoint\-Projekte spezifische Eigenschaften definiert.  
  
 Eine Liste allgemeiner Eigenschaften [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)], Sie finden [Allgemeine MSBuild\-Projekteigenschaften](http://go.microsoft.com/fwlink/?LinkID=168687).  Eine vollständige Liste mit den Eigenschaften, die von der Programmiersprache unterstützt werden, finden Sie in der TARGETS\-Datei, in der Projektdatei \(CSPROJ\- oder VBPROJ\-Datei\) oder in der Projektbenutzerdatei \(CSPROJ.USER\- oder VBPROJ.USER\-Datei\).  
  
## SharePoint\-spezifische MSBuild\-Eigenschaften  
 Die folgende Tabelle enthält die [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]\-Eigenschaften, die spezifisch für SharePoint\-Projekte in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] gelten.  Zwar sind noch weitere Eigenschaften vorhanden, diese dienen jedoch lediglich zur internen Verwendung.  
  
|Eigenschaftenname|**Beschreibung**|  
|-----------------------|----------------------|  
|SharePointSiteUrl|Eine Zeichenfolge, die die [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] zur SharePoint\-Website darstellt.|  
|SandboxedSolution|Ein boolescher Wert, der angibt, ob es sich bei der Lösung um eine Sandkastenlösung handelt.|  
|ActiveDeploymentConfiguration|Die aktive Bereitstellungskonfiguration.|  
|IncludeAssemblyInPackage|Ein boolescher Wert, der angibt, ob die Assembly in der Paketdatei enthalten ist.|  
|PreDeploymentCommand|Ein Zeichenfolgenwert, der den Befehl darstellt, der im Befehlsschritt vor der Bereitstellung ausgeführt werden soll.|  
|PostDeploymentCommand|Ein Zeichenfolgenwert, der den Befehl darstellt, der im Befehlsschritt nach der Bereitstellung ausgeführt werden soll.|  
|CustomBeforeSharePointTargets|Eine Zeichenfolge, die den Pfad einer [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]\-Zieledatei darstellt.  Wenn die Zieledatei vorhanden und definiert ist, wird sie vor allen SharePoint\-Zieledaten importiert.  Mithilfe dieser Eigenschaft können Sie den Packvorgang durch Vordefinieren packbezogener Eigenschaften anpassen, ohne die veröffentlichte SharePoint\-Zieledatei zu ändern; die Zieledatei gilt auch weiterhin für alle SharePoint\-Projekte.|  
|CustomAfterSharePointTargets|Eine Zeichenfolge, die den Pfad einer [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]\-Zieledatei darstellt.  Wenn die Zieledatei vorhanden und definiert ist, wird sie nach allen SharePoint\-Zieledaten importiert.  Mithilfe dieser Eigenschaft können Sie den Packvorgang durch Überschreiben packbezogener Eigenschaften und Ziele anpassen, ohne die veröffentlichte SharePoint\-Zieledatei ändern zu müssen; die Zieledatei gilt auch weiterhin für alle SharePoint\-Projekte.|  
|LayoutPath|Eine Zeichenfolge, die das Stammverzeichnis darstellt, in dem alle zu verpackenden Dateien vorübergehend platziert werden, bevor sie schließlich der WSP\-Datei hinzugefügt werden.  Dieser Pfad sollte Ihnen bekannt sein, wenn Sie das BeforeLayout\-Ziel und das AfterLayout\-Ziel zum Hinzufügen, Entfernen oder Ändern von zu packenden Dateien überschreiben, da Sie ihn zum Ändern des Inhalts der WSP\-Datei verwenden können.|  
|BasePackagePath|Eine Zeichenfolge, die den Ordner darstellt, in dem das Paket platziert wird.  Von diesem Wert wird das Ausgabeverzeichnis des Projekts \(beispielsweise "Bin\\Debug"\) verwendet.|  
|PackageExtension|Eine Zeichenfolge, die die an das Paket anzufügende Dateinamenerweiterung darstellt.  Standardwert: wsp.|  
|AssemblyDeploymentTarget|Eine Zeichenfolge, die den Ort darstellt, an dem die Projektassembly auf dem SharePoint\-Server bereitgestellt wird.  Der Wert lautet entweder "GlobalAssemblyCache" \(Standardwert\) oder "WebApplication".  Diese Eigenschaft kann auch im Eigenschaftenfenster festgelegt werden.|  
|PackageWithValidation|Ein boolescher Wert, der angibt, ob vor dem Packen eine Validierung ausgeführt wird.  Mithilfe dieser Eigenschaft können Validierungsfehler bei der Paketerstellung ignoriert werden.|  
|ValidatePackageDependsOn|Eine Zeichenfolge zum Definieren zusätzlicher Ziele, die vor dem ValidatePackage\-Ziel ausgeführt werden sollen.|  
|TokenReplacementFileExensions|Eine Zeichenfolge zum Definieren der Dateien, deren Token beim Packen ersetzt werden.|  
  
## Verwenden von MSBuild\-Eigenschaften auf der Eigenschaftenseite  
 Aus Gründen der Flexibilität können Sie anstelle der hartcodierten Zeichenfolgen in den Feldern **Befehlszeile vor der Bereitstellung** und **Befehlszeile nach der Bereitstellung** auf der SharePoint\-Eigenschaftenseite die SharePoint\-Eigenschaften als Argumente verwenden.  So können Sie beispielsweise `$(SharePointSiteUrl)` verwenden, anstatt eine bestimmte [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]\-Zeichenfolge für die SharePoint\-Website anzugeben.  
  
> [!NOTE]  
>  Eine Eigenschaft kann entweder mithilfe der [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]\-Variablensyntax `$(`*propertyName*`)` oder mithilfe der Umgebungsvariablensyntax `%`*propertyName*`%` angegeben werden.  
  
## Siehe auch  
 [MSBuild Reference](../msbuild/msbuild-reference.md)  
  
  