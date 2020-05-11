---
title: 'Neue Projektgeneration: Unter der Haube, Teil 2 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8692f2012e5f2733982f04e35a7fed415e49c636
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707022"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Generieren neuer Projekte: Einblick in die Hintergründe, Teil 2

In [New Project Generation: Under the Hood, Part One](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) haben wir gesehen, wie das Dialogfeld Neues **Projekt** ausgefüllt wird. Angenommen, Sie haben eine **Visual C-Windows-Anwendung**ausgewählt, die Textfelder **Name** und **Position** ausgefüllt und auf OK geklickt.

## <a name="generating-the-solution-files"></a>Generieren der Lösungsdateien
 Wenn Sie eine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Anwendungsvorlage auswählen, wird die entsprechende .vstemplate-Datei entpackt und geöffnet und eine Vorlage zum Interpretieren der XML-Befehle in dieser Datei gestartet. Mit diesen Befehlen werden Projekte und Projektelemente in der neuen oder vorhandenen Projektmappe erstellt.

 Die Vorlage entpackt Quelldateien, so genannte Elementvorlagen, aus demselben ZIP-Ordner, der die .vstemplate-Datei enthält. Die Vorlage kopiert diese Dateien in das neue Projekt und passt sie entsprechend an.

### <a name="template-parameter-replacement"></a>Vorlagenparameter-Ersetzung
 Wenn die Vorlage eine Elementvorlage in ein neues Projekt kopiert, werden alle Vorlagenparameter durch Zeichenfolgen ersetzt, um die Datei anzupassen. Ein Vorlagenparameter ist ein spezielles Token, dem ein Dollarzeichen vorangestellt und gefolgt wird, z. B. $date.

 Sehen wir uns eine typische Projektelementvorlage an. Extrahieren und untersuchen Sie Program.cs im Ordner "Programmdateien" ,,Microsoft Visual Studio 8' "Common7"IDE,ProjectTemplates, "CSharp", "Windows" und "WindowsApplication.zip".

```csharp
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

Wenn Sie ein neues Windows-Anwendungsprojekt mit dem `$safeprojectname$` Namen Einfach erstellen, ersetzt die Vorlage den Parameter durch den Namen des Projekts.

```csharp
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

## <a name="a-look-inside-a-vstemplate-file"></a>Ein Blick in eine . VSTemplate-Datei
 Eine einfache .vstemplate-Datei hat dieses Format

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Wir haben \<uns den Abschnitt TemplateData> in der [neuen Projektgeneration: Unter der Haube, Teil 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)angesehen. Die Tags in diesem Abschnitt werden verwendet, um die Darstellung des Dialogfelds **Neues Projekt** zu steuern.

 Die Tags \<im Abschnitt TemplateContent> steuern die Generierung neuer Projekte und Projektelemente. Hier ist \<der Abschnitt TemplateContent> aus der Datei cswindowsapplication.vstemplate im Ordner "Programmdateien" , Microsoft Visual Studio 8, "Common7", "IDE"-Projektvorlagen, "CSharp", "Windows" und "WindowsApplication.zip".

```xml
<TemplateContent>
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">
    <ProjectItem ReplaceParameters="true"
      TargetFileName="Properties\AssemblyInfo.cs">
      AssemblyInfo.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Resources.resx">
      Resources.resx
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
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

 Das \<Project>-Tag steuert die Generierung \<eines Projekts, und das ProjectItem>-Tag steuert die Generierung eines Projektelements. Wenn der Parameter ReplaceParameters true ist, passt die Vorlage alle Vorlagenparameter in der Projektdatei oder dem Projektelement an. In diesem Fall werden alle Projektelemente angepasst, mit Ausnahme von Settings.settings.

 Der Parameter TargetFileName gibt den Namen und den relativen Pfad der resultierenden Projektdatei oder des resultierenden Elements an. Auf diese Weise können Sie eine Ordnerstruktur für Ihr Projekt erstellen. Wenn Sie dieses Argument nicht angeben, hat das Projektelement denselben Namen wie die Projektelementvorlage.

 Die resultierende Windows-Anwendungsordnerstruktur sieht wie folgt aus:

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 Das erste \<und einzige Project>-Tag in der Vorlage lautet:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Dadurch wird die Vorlage "Neues Projekt" angewiesen, die Projektdatei Simple.csproj zu erstellen, indem das Vorlagenelement windowsapplication.csproj kopiert und angepasst wird.

### <a name="designers-and-references"></a>Designer und Referenzen
 Sie können im Projektmappen-Explorer sehen, dass der Eigenschaftenordner vorhanden ist und die erwarteten Dateien enthält. Aber was ist mit Projektverweisen und Designerdateiabhängigkeiten, z. B. Resources.Designer.cs zu Resources.resx und Form1.Designer.cs zu Form1.cs?  Diese werden in der Datei Simple.csproj eingerichtet, wenn sie generiert wird.

 Hier ist \<die ItemGroup-> von Simple.csproj, die die Projektreferenzen erstellt:

```xml
<ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Drawing" />
    <Reference Include="System.Windows.Forms" />
    <Reference Include="System.Xml" />
</ItemGroup>
```

 Sie können sehen, dass dies die sechs Projektverweise sind, die im Projektmappen-Explorer angezeigt werden. Hier ist ein Abschnitt \<aus einem anderen ItemGroup->. Viele Codezeilen wurden aus Gründen der Übersichtlichkeit gelöscht. In diesem Abschnitt wird Settings.Designer.cs von Einstellungen abhängig.

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Weitere Informationen

- [Generieren neuer Projekte: Einblick in die Hintergründe, Teil 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
