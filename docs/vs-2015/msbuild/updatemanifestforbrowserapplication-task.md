---
title: UpdateManifestForBrowserApplication-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dffa98a8abbf74bd6eee8761d91f09a7c022666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68740217"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> Task wird ausgeführt, um das- **\<hostInBrowser />** Element dem Anwendungs Manifest (*ProjectName*. exe. manifest) hinzuzufügen, wenn ein [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] Projekt erstellt wird.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`ApplicationManifest`|Erforderlicher **ITaskItem[]** -Parameter.<br /><br /> Gibt den Pfad und den Namen der Anwendungsmanifestdatei an, der Sie das `<hostInBrowser />` Element hinzufügen möchten.|  
|`HostInBrowser`|Erforderlicher **boolescher** Parameter.<br /><br /> Gibt an, ob das Anwendungs Manifest geändert werden soll, um das Element einzuschließen **\<hostInBrowser />** . **True**gibt an, dass ein neues " `<` **tustinbrowser/>"-** Element im-Element enthalten ist **\<entryPoint />** . Beachten Sie, dass die Element Einbindung kumulativ ist: Wenn bereits ein- **\<hostInBrowser />** Element vorhanden ist, wird es nicht entfernt oder überschrieben. Stattdessen wird ein zusätzliches **\<hostInBrowser />** Element erstellt. Wenn **false**, dann ist das Anwendungsmanifest nicht geändert.|  
  
## <a name="remarks"></a>Hinweise  
 [!INCLUDE[TLA2#tla_xbap#plural](../includes/tla2sharptla-xbapsharpplural-md.md)] wird mithilfe von [!INCLUDE[TLA#tla_clickonce](../includes/tlasharptla-clickonce-md.md)] ausgeführt und muss aus diesem Grund mit unterstützenden Bereitstellungs- und Anwendungsmanifesten veröffentlicht werden. [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] verwendet die [GenerateApplicationManifest](/dotnet/api/microsoft.build.tasks.generateapplicationmanifest)-Aufgabe zum Generieren eines Anwendungsmanifests.  
  
 Zum Konfigurieren einer Anwendung, die von einem Browser gehostet werden soll, **\<hostInBrowser />** muss dem Anwendungs Manifest ein zusätzliches Element hinzugefügt werden, wie im folgenden Beispiel gezeigt:  
  
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
  
 Die <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> Aufgabe wird ausgeführt, wenn ein [!INCLUDE[TLA2#tla_xbap](../includes/tla2sharptla-xbap-md.md)] Projekt erstellt wird, um das `<hostInBrowser />` Element hinzuzufügen.  
  
## <a name="example"></a>Beispiel  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)   
 [Aufgaben Referenz](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)   
 [Entwickeln einer WPF-Anwendung (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Übersicht über WPF-XAML-Browseranwendungen](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
