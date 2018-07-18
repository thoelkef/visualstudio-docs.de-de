---
title: 'Neue Projektgenerierung: Hinter den Kulissen Teil 2 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69174be20a0961a6074650471bcb4b9d1df9fa98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133184"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Neue Projektgenerierung: Hinter den Kulissen Teil 2
In [neue Projekterstellung: Details, Teil 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) wurde erläutert, wie die **neues Projekt** Dialogfeld Feld wird aufgefüllt. Angenommen, Sie haben ausgewählt, eine **Visual C#-Windows-Anwendung**, ausgefüllten der **Namen** und **Speicherort** Textfelder, und klicken auf OK.  
  
## <a name="generating-the-solution-files"></a>Generieren die Projektmappendateien  
 Auswählen einer Anwendungsvorlage leitet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] extrahieren und öffnen Sie die entsprechenden VSTEMPLATE-Datei, und starten Sie eine Vorlage, um die XML-Befehle in dieser Datei zu interpretieren. Diese Befehle werden in der neuen oder vorhandenen Projektmappe Projekte und Projektelemente erstellen.  
  
 Die Vorlage entpackt Quelldateien, Elementvorlagen, aus dem gleichen ZIP-Ordner, der die VSTEMPLATE-Datei enthält aufgerufen. Die Vorlage übernimmt diese Dateien in das neue Projekt, und sie entsprechend anpassen.  
  
### <a name="template-parameter-replacement"></a>Vorlage Parameterersetzung  
 Wenn die Vorlage zu einem neuen Projekt eine Elementvorlage kopiert, ersetzt es, Vorlagenparameter mit Zeichenfolgen, um die Datei anzupassen. Ein Vorlagenparameter ist eine spezielle Token, das vorangestellt ist, und ein Dollarzeichen gefolgt sind, z. B. $date$.  
  
 Sehen wir uns einen typischen Projektelementvorlage an. Extrahieren Sie und untersuchen Sie die Datei "Program.cs" im Ordner "Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip".  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace $safeprojectname$  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Wenn Sie ein neues Windows-Anwendungsprojekt mit dem Namen einfach erstellen, die Vorlage ersetzt die `$safeprojectname$` Parameter mit dem Namen des Projekts.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace Simple  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Eine vollständige Liste der Vorlagenparameter finden Sie unter [Vorlagenparameter](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Ein Einblick in ein. VSTemplate-Datei  
 Eine einfache VSTEMPLATE-Datei hat dieses format  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Erläutert die \<TemplateData > im Abschnitt der [neue Projekterstellung: Details, Teil 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Die Tags in diesem Abschnitt werden verwendet, um die Darstellung der steuern die **neues Projekt** (Dialogfeld).  
  
 Die Tags in der \<TemplateContent >-Abschnitt Steuerelement die Generierung von neuen Projekten und Projektelementen. So sieht die \<TemplateContent > aus der cswindowsapplication.vstemplate-Datei im Ordner "\Programme\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip".  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
      Settings.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
      Form1.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Form1.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Program.cs  
    </ProjectItem>  
  </Project>  
</TemplateContent>  
```  
  
 Die \<Projekt > Tag steuert die Generierung eines Projekts, und die \<ProjectItem >-Tag steuert die Generierung des ein Projektelement. Wenn der Parameter ReplaceParameters auf "true" festgelegt ist, wird die Vorlage alle Vorlagenparameter in der Projektdatei oder Element anpassen. In diesem Fall werden alle Projektelemente angezeigt, mit Ausnahme von Settings.settings angepasst.  
  
 Der TargetFileName-Parameter gibt den Namen und den relativen Pfad der resultierenden Datei des Projekts oder des Elements. Dadurch können Sie eine Ordnerstruktur für das Projekt zu erstellen. Wenn Sie dieses Argument nicht angeben, wird das Projektelement den gleichen Namen wie die Projektelementvorlage haben.  
  
 Die resultierende Windows-Anwendung-Ordnerstruktur sieht folgendermaßen aus:  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 Die erste und einzige \<Projekt >-Tag in die Vorlage lautet:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 Dadurch wird die neue Projektvorlage So erstellen Sie die Projektdatei Simple.csproj kopieren und Anpassen der Vorlage Element windowsapplication.csproj angewiesen.  
  
### <a name="designers-and-references"></a>Designer und Verweise  
 Im Projektmappen-Explorer sehen Sie, dass der Ordner "Konfigurationseigenschaften" vorhanden ist und die erwarteten Dateien enthält. Aber was Projekt verweist, und Designerdatei Abhängigkeiten, z. B. Resources.Designer.cs auf "Resources.resx" und "Form1.Designer.cs" auf "Form1.cs"?  Diese werden in der Datei Simple.csproj eingerichtet, wenn sie generiert werden.  
  
 So sieht die \<ItemGroup > von Simple.csproj, die die Projektverweisen erstellt:  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 Sie sehen, dass die sechs Projektverweise handelt, die im Projektmappen-Explorer angezeigt werden. Hier ist ein Abschnitt von einem anderen \<ItemGroup >. Viele Codezeilen wurden aus Gründen der Übersichtlichkeit gelöscht. In diesem Abschnitt werden die Settings.Designer.cs Settings.settings abhängig:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Generieren neuer Projekte: Einblick in die Hintergründe, Teil 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)