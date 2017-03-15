---
title: "MT Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCManifestTool.ResourceOutputFileName"
  - "VC.Project.VCManifestTool.SuppressDependencyElement"
  - "VC.Project.VCManifestTool.ManifestFromManagedAssembly"
  - "VC.Project.VCManifestTool.GenerateCategoryTags"
  - "VC.Project.VCManifestTool.EnableDPIAwareness"
  - "vc.task.mt"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBUILD (Visual C++), MT task"
  - "MT task (MSBuild (Visual C++))"
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# MT Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Umschließt das Microsoft Manifest\-Tool \("mt.exe"\).  Weitere Informationen finden Sie unter "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der **MT**\-Aufgabe beschrieben.  Die meisten Aufgabenparameter und einige Sätze von Parametern entsprechen einer Befehlszeilenoption.  
  
> [!NOTE]
>  Die mt.exe\-Dokumentation verwendet einen Bindestrich \(**\-**\) als Präfix für Befehlszeilenoptionen, doch in diesem Thema wird ein Schrägstrich verwendet \(**\/**\).  Beide Präfixe sind akzeptabel.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|**AdditionalManifestFiles**|Optionaler **String\[\]**\-Parameter.<br /><br /> Gibt den Namen einer oder mehrerer Manifestdateien an.<br /><br /> Weitere Informationen finden Sie in der Option **\/manifest** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**AdditionalOptions**|Optionaler **String**\-Parameter.<br /><br /> Eine Liste von Befehlszeilenoptionen.  Beispiel: "*\/option1 \/option2 \/option\#*".  Verwenden Sie diesen Parameter, um Befehlszeilenoptionen anzugeben, die nicht von einem beliebigen anderen **MT**\-Aufgabenparameter dargestellt werden.<br /><br /> Weitere Informationen finden Sie unter "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**AssemblyIdentity**|Optionaler **String**\-Parameter.<br /><br /> Gibt die Attributwerte des **assemblyIdentity**\-Elements des Manifests an.  Geben Sie eine durch Trennzeichen getrennte Liste an, wobei die erste Komponente der Wert des `name`\-Attributs ist, dem mindestens ein Name\-Wert\-Paar diese Form aufweist: *\<attribute name\>\=\<attribute\_value\>*.<br /><br /> Weitere Informationen finden Sie in der Option **\/identity** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**ComponentFileName**|Optionaler **String**\-Parameter.<br /><br /> Gibt den Namen der Dynamic Link Library an, die aus den RGS\- oder TLB\-Dateien erstellt werden soll.  Dieser Parameter ist erforderlich, wenn Sie den **RegistrarScriptFile**\-MT\-Aufgabenparameter oder den **TypeLibraryFile**\-MT\-Aufgabenparameter angeben.<br /><br /> Weitere Informationen finden Sie in der Option **\/dll** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**DependencyInformationFile**|Optionaler **String**\-Parameter.<br /><br /> Legt die Abhängigkeitsinformationsdatei fest, die von Visual Studio verwendet wird, um Buildabhängigkeitsinformationen für das Manifesttool nachzuverfolgen.|  
|**EmbedManifest**|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn `true`, wird die Manifestdatei in die Assembly eingebettet.  Wenn `false`, wird eine eigenständige Manifestdatei erstellt.|  
|**EnableDPIAwareness**|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn `true`, werden die Manifestinformationen ergänzt, die die Anwendung als DPI\-bewusst markieren.  Die Erstellung einer DPI\-kompatiblen Anwendung sorgt für eine einheitliche benutzerfreundliche Benutzeroberfläche in vielen verschiedenen Anzeigeeinstellungen mit hoher DPI\-Zahl.<br /><br /> Weitere Informationen finden Sie unter "High DPI" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**GenerateCatalogFiles**|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn `true`, werden Katalogdefinitionsdateien \(.cdf\) generiert.<br /><br /> Weitere Informationen finden Sie in der Option **\/makecdfs** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**GenerateCategoryTags**|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn `true`, werden Kategorietags generiert.  Ist dieser Parameter `true`, muss auch der **ManifestFromManagedAssemblyMT**\-Aufgabenparameter angegeben werden.<br /><br /> Weitere Informationen finden Sie in der Option **\/category** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**InputResourceManifests**|Optionaler **String**\-Parameter.<br /><br /> Geben Sie das Manifest einer Ressource vom RT\_MANIFEST\-Typ ein, der den angegebenen Bezeichner hat.  Geben Sie eine Ressource in dieser Form an, *\<file\>\[***;***\[***\#***\]\<resource\_id\>\]*, wobei der `resource_id`\-Parameter eine nicht\-negative 16\-Bit\-Zahl ist.<br /><br /> Wenn kein `resource_id`\-Element angegeben ist, wird der CREATEPROCESS\_MANIFEST\_RESOURCE\-Standardwert \(1\) verwendet.<br /><br /> Weitere Informationen finden Sie in der Option **\/inputresource** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**ManifestFromManagedAssembly**|Optionaler **String**\-Parameter.<br /><br /> Generieren Sie ein Manifest anhand der angegebenen verwalteten Assembly.<br /><br /> Weitere Informationen finden Sie in der Option **\/managedassemblyname** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**ManifestToIgnore**|Optionaler **String**\-Parameter.<br /><br /> \(Wird nicht verwendet.\)|  
|**OutputManifestFile**|Optionaler **String**\-Parameter.<br /><br /> Gibt den Namen des Ausgabemanifests an.  Wenn dieser Parameter weggelassen wird, und nur ein Manifest darauf angewendet wird, wird dieses Manifest an Ort und Stelle geändert.<br /><br /> Weitere Informationen finden Sie in der Option **\/out** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**OutputResourceManifests**|Optionaler **String**\-Parameter.<br /><br /> Geben Sie das Manifest an eine Ressource des RT\_MANIFEST\-Typs aus, der den angegebenen Bezeichner hat.  Die Ressource weist diese Form auf: *\<file\>\[***;***\[***\#***\]\<resource\_id\>\]*, wobei der `resource_id`\-Parameter eine nicht\-negative 16\-Bit\-Zahl ist.<br /><br /> Wenn kein `resource_id`\-Element angegeben ist, wird der CREATEPROCESS\_MANIFEST\_RESOURCE\-Standardwert \(1\) verwendet.<br /><br /> Weitere Informationen finden Sie in der Option **\/outputresource** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**RegistrarScriptFile**|Optionaler **String**\-Parameter.<br /><br /> Gibt den Namen der Registrierungsskriptdatei \(.rgs\) an, die für die registrierungsfreie COM\-Manifest\-Unterstützung verwendet werden soll.<br /><br /> Weitere Informationen finden Sie in der Option **\/rgs** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**ReplacementsFile**|Optionaler **String**\-Parameter.<br /><br /> Gibt die Datei an, die Werte für die ersetzbaren Zeichenfolgen in der Registrierungsstellenskriptdatei \(.rgs\) enthält.<br /><br /> Weitere Informationen finden Sie in der Option **\/replacements** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**ResourceOutputFileName**|Optionaler **String**\-Parameter.<br /><br /> Gibt die Ressourcenausgabedatei an, die zur Einbettung des Manifests in die Projektausgabe verwendet wird.|  
|**Sources**|Optionaler `ITaskItem[]`\-Parameter.<br /><br /> Gibt eine Liste von Manifestquelldateien an, die durch Leerzeichen getrennt sind.<br /><br /> Weitere Informationen finden Sie in der Option **\/manifest** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**SuppressDependencyElement**|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn `true`, wird ein Manifest ohne Abhängigkeitselemente generiert.  Ist dieser Parameter `true`, geben Sie auch den **ManifestFromManagedAssemblyMT**\-Aufgabenparameter an.<br /><br /> Weitere Informationen finden Sie in der Option **\/nodependency** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**SuppressStartupBanner**|Optionaler `Boolean`\-Parameter.<br /><br /> Bei `true` wird die Anzeige der Urheberrechts\- und Versionsnummernmeldung verhindert, wenn die Aufgabe startet.<br /><br /> Weitere Informationen finden Sie in der Option **\/nologo** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**TrackerLogDirectory**|Optionaler `String`\-Parameter.<br /><br /> Gibt das Zwischenverzeichnis an, in dem Nachverfolgungsprotokolle für diese Aufgabe gespeichert werden.|  
|**TypeLibraryFile**|Optionaler **String**\-Parameter.<br /><br /> Gibt den Namen der Typbibliotheksdatei \(.tlb\) an.  Ist dieser Parameter angegeben, geben Sie auch den **ComponentFileName MT**\-Aufgabenparameter an.<br /><br /> Weitere Informationen finden Sie in der Option **\/tlb** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
|**UpdateFileHashes**|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn `true`, wird der Hash\-Wert der Dateien im Pfad berechnet, der durch den **UpdateFileHashesSearchPathMT**\-Aufgabenparameter angegeben wird, und anschließend der Wert des **hash**\-Attributs des **file**\-Elements des Manifests mit dem berechneten Wert aktualisiert.<br /><br /> Weitere Informationen finden Sie in der Option **\/hashupdate** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.  Sehen Sie sich auch den **UpdateFileHashesSearchPath**\-Parameter in dieser Tabelle an.|  
|**UpdateFileHashesSearchPath**|Optionaler `String`\-Parameter.<br /><br /> Gibt den Suchpfad an, der verwendet werden soll, wenn die Dateihashs aktualisiert werden.  Verwenden Sie diesen Parameter mit dem **UpdateFileHashes MT**\-Aufgabenparameter.<br /><br /> Weitere Informationen erhalten Sie unter dem **UpdateFileHashes**\-Parameter in dieser Tabelle.|  
|**VerboseOutput**|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn `true`, werden ausführliche Debuginformationen angezeigt.<br /><br /> Weitere Informationen finden Sie in der Option **\/verbose** in "Mt.exe" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)\-Website.|  
  
## Hinweise  
  
## Siehe auch  
 [Task Reference](../msbuild/msbuild-task-reference.md)