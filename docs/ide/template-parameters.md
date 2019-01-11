---
title: Projekt- und Elementvorlagenparameter
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e945ac065b2c7f5e3a677ae2175b45a94af2910a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935189"
---
# <a name="template-parameters"></a>Vorlagenparameter

Wenn die Vorlage instanziiert wird, können Sie die darin erhaltenen Werte ersetzen. Verwenden Sie *Vorlagenparameter*, um diese Funktion einzurichten. Sie können diese Vorlagenparameter dazu verwenden, Werte wie Klassennamen und Namespaces in der Vorlage zu ersetzen. Der Vorlagen-Assistent, der im Hintergrund ausgeführt wird, wenn ein Benutzer ein neues Element oder Projekt hinzufügt, ersetzt diese Parameter.

## <a name="declaring-and-enabling-template-parameters"></a>Deklarieren und Aktivieren von Vorlagenparametern

Vorlagenparameter werden im Format $*parameter*$ deklariert. Beispiel:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="to-enable-parameter-substitution-in-templates"></a>So aktivieren Sie die Parameterersetzung in Vorlagen

1. Suchen Sie in der *VSTEMPLATE*-Datei der Vorlage das `ProjectItem`-Element, das dem Element entspricht, für das Sie die Parameterersetzung aktivieren möchten.

1. Legen Sie das `ReplaceParameters`-Attribut des `ProjectItem`-Elements auf `true` fest.

1. Schließen Sie in der Codedatei für das Projektelement ggf. Parameter ein. Durch den folgenden Parameter wird beispielsweise angegeben, dass der sichere Projektname für den Namespace in einer Datei verwendet wird:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Reservierte Vorlagenparameter

In der folgenden Tabelle sind die reservierten Vorlagenparameter aufgelistet, die von beliebigen Vorlagen verwendet werden können.

|Parameter|Beschreibung|
|---------------|-----------------|
|clrversion|Aktuelle Version der Common Language Runtime (CLR).|
|guid[1-10]|Eine GUID zum Ersetzen der Projekt-GUID in einer Projektdatei. Sie können bis zu zehn eindeutige GUIDs (z.B. `guid1`) angeben.|
|itemname|Der vom Benutzer im Dialogfeld **Neues Element hinzufügen** angegebene Name|
|machinename|Der aktuelle Computername (z. B. Computer01).|
|projectname|Der vom Benutzer im Dialogfeld **Neues Projekt** angegebene Name|
|registeredorganization|Der Registrierungsschlüsselwert aus HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|rootnamespace|Der Stammnamespace des aktuellen Projekts. Dieser Parameter gilt nur für Elementvorlagen.|
|safeitemname|Der vom Benutzer im Dialogfeld **Neues Element hinzufügen** angegebene Name, aus dem alle unsicheren Zeichen sowie Leerzeichen entfernt wurden|
|safeprojectname|Der vom Benutzer im Dialogfeld **Neues Projekt** angegebene Name, aus dem alle unsicheren Zeichen sowie Leerzeichen entfernt wurden|
|Uhrzeit|Die aktuelle Uhrzeit im Format TT/MM/JJJJ 00:00:00.|
|SpecificSolutionName|Der Name der Projektmappe. Wenn "Projektmappenverzeichnis erstellen" aktiviert ist, verfügt `SpecificSolutionName` über den Projektmappennamen. Wenn "Projektmappenverzeichnis erstellen" nicht aktiviert ist, ist `SpecificSolutionName` leer.|
|userdomain|Die aktuelle Benutzerdomäne.|
|username|Der aktuelle Benutzername.|
|webnamespace|Der Name der aktuellen Website. Dieser Parameter wird in der Webformularvorlage verwendet und gewährleistet eindeutige Klassennamen. Wenn sich die Website im Stammverzeichnis des Webservers befindet, wird dieser Vorlagenparameter in das Stammverzeichnis des Webservers aufgelöst.|
|Jahr|Das aktuelle Jahr im Format JJJJ.|

> [!NOTE]
> Bei Vorlagenparametern wird die Groß-/Kleinschreibung beachtet.

## <a name="custom-template-parameters"></a>Benutzerdefinierte Vorlagenparameter

Neben den reservierten Standardvorlagenparametern, die während dem Ersetzen von Parametern verwendet werden, können Sie eigene Vorlagenparameter und -werte angeben. Weitere Informationen finden Sie unter [CustomParameters-Element (Visual Studio-Vorlagen)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Beispiel: Verwenden des Projektnamens für den Dateinamen

Sie können variable Dateinamen für Projektelemente festlegen, indem Sie einen Parameter im `TargetFileName`-Attribut verwenden.

Im folgenden Beispiel wird deutlich, dass der von `$projectname$` angegebene Projektname als Name für eine ausführbare Datei verwendet wird.

```xml
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Beispiel: Verwenden des sicheren Projektnamens für den Namespacenamen

Verwenden Sie folgende Syntax, um den Projektnamen für den Namespace in einer C#-Klassendatei zu übernehmen:

```csharp
namespace $safeprojectname$
{
    public class Class1
    {
        public Class1()
        { }
    }
}
```

Fügen Sie der *VSTEMPLATE*-Datei für die Projektvorlage das `ReplaceParameters="true"`-Attribut hinzu, wenn Sie auf die Datei verweisen:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Siehe auch

- [Anpassen von Projekt- und Elementvorlagen](../ide/customizing-project-and-item-templates.md)
- [Vorgehensweise: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md)
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
