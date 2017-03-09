---
title: "UpdateManifestForBrowserApplication Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "UpdateManifestForBrowserApplication task [WPF MSBuild]"
  - "adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]"
  - "building XBAP projects [WPF MSBuild]"
  - "UpdateManifestForBrowserApplication task [WPF MSBuild], parameters"
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# UpdateManifestForBrowserApplication Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> Aufgabe wird ausgeführt, um das  **\< HostInBrowser \>** Element dem Anwendungsmanifest \(*Projektname*. exe.manifest\) hinzuzufügen, wenn ein [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] Projekt erstellt wird.  
  
## Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`ApplicationManifest`|Erforderliche **ITaskItem \[\]** Parameter.<br /><br /> Gibt den Pfad und den Namen der Anwendungsmanifestdatei an, der Sie das `<hostInBrowser />` Element hinzufügen möchten.|  
|`HostInBrowser`|Erforderliche **boolesche** Parameter.<br /><br /> Gibt an, ob das Anwendungsmanifest geändert werden soll, um das **\< HostInBrowser \/\>** Element einzufügen.  Wenn **true**, dann ist ein neues `<`**hostInBrowser \/\>** Element im **\<entryPoint\/\>** Element enthalten.  Beachten Sie, dass der Einschluss von Elementen kumulativ ist: Wenn ein **\< hostInBrowser \/\>** Element bereits vorhanden ist, wird es weder entfernt noch überschrieben.  Stattdessen wird ein zusätzliches **\<HostInBrowser \/\>** Element erstellt.  Wenn **false**, dann ist das Anwendungsmanifest nicht geändert.|  
  
## Hinweise  
 [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)] wird mithilfe von [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] ausgeführt und muss aus diesem Grund mit unterstützenden Bereitstellungs\- und Anwendungsmanifesten veröffentlicht werden.  [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] verwendet die [GenerateApplicationManifest](http://msdn2.microsoft.com/library/6wc2ccdc.aspx) Aufgabe zum Generieren eines Anwendungsmanifests.  
  
 Anschließend muss ein zusätzliches Element  **\<hostInBrowser \/\>** zum Anwendungsmanifest hinzugefügt werden, um eine Anwendung zu konfigurieren, die von einem Browser gehostet wird; wie im folgenden Beispiel gezeigt:  
  
```  
<!--MyXBAPApplication.exe.manifest-->  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly ... >  
    <asmv1:assemblyIdentity ... />  
    <application />  
    <entryPoint>  
      ...  
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />  
    </entryPoint>  
  ...  
/>  
```  
  
 Die <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> Aufgabe wird ausgeführt, wenn ein [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] Projekt erstellt wird, um das `<hostInBrowser />` Element hinzuzufügen.  
  
## Beispiel  
 Das folgende Beispiel zeigt, wie Sie sicherstellen, dass das `<hostInBrowser />` Element in einer Anwendungsmanifestdatei eingefügt wird.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"  
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UpdateManifestForBrowserApplicationTask">  
    <UpdateManifestForBrowserApplication  
      ApplicationManifest="MyXBAPApplication.exe.manifest"  
      HostInBrowser="true" />  
  </Target>  
</Project>  
```  
  
## Siehe auch  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Erstellen einer WPF\-Anwendung \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Übersicht über WPF\-XAML\-Browseranwendungen](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)