---
title: "Projekt- und Elementvorlagen für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e3ce315cd1ddff9445c72f7299a8d6aaf0a3a82
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2018
---
# <a name="template-parameters"></a>Vorlagenparameter

Indem Sie Parameter in Ihren Vorlagen verwenden, können Sie die Werte von Schlüsselteilen der Vorlage, wie z. B. Klassennamen und Namespaces, bei Instanziierung die Vorlage ersetzen. Diese Parameter werden durch den Vorlagen-Assistenten ersetzt, der im Hintergrund ausgeführt wird, wenn ein Benutzer in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** auf **OK** oder **Hinzufügen** klickt.

## <a name="declaring-and-enabling-template-parameters"></a>Deklarieren und Aktivieren von Vorlagenparametern

Vorlagenparameter werden im Format $*parameter*$ deklariert. Zum Beispiel:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="to-enable-parameter-substitution-in-templates"></a>So aktivieren Sie die Parameterersetzung in Vorlagen

1. Suchen Sie in der VSTEMPLATE-Datei der Vorlage das `ProjectItem`-Element, das dem Element entspricht, für das Sie die Parameterersetzung aktivieren möchten.

1. Legen Sie das `ReplaceParameters`-Attribut des `ProjectItem`-Elements auf `true` fest.

1. Schließen Sie in der Codedatei für das Projektelement ggf. Parameter ein. Durch den folgenden Parameter wird beispielsweise angegeben, dass der sichere Projektname für den Namespace in einer Datei verwendet werden soll:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Reservierte Vorlagenparameter

In der folgenden Tabelle sind die reservierten Vorlagenparameter aufgelistet, die von beliebigen Vorlagen verwendet werden können.

|Parameter|description|
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
|webnamespace|Der Name der aktuellen Website. Dieser Parameter wird in der Web Form-Vorlage verwendet und gewährleistet eindeutige Klassennamen. Wenn sich die Website im Stammverzeichnis des Webservers befindet, wird dieser Vorlagenparameter in das Stammverzeichnis des Webservers aufgelöst.|
|Jahr|Das aktuelle Jahr im Format JJJJ.|

> [!NOTE]
> Bei Vorlagenparametern wird die Groß-/Kleinschreibung beachtet.

## <a name="custom-template-parameters"></a>Benutzerdefinierte Vorlagenparameter

Neben den reservierten Standardvorlagenparametern, die während dem Ersetzen von Parametern verwendet werden, können Sie eigene Vorlagenparameter und -werte angeben. Weitere Informationen finden Sie unter [CustomParameters-Element (Visual Studio-Vorlagen)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-using-the-project-name-for-a-file-name"></a>Beispiel: Verwenden des Projektnamens für den Dateinamen

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

## <a name="example-using-the-safe-project-name-for-the-namespace-name"></a>Beispiel: Verwenden des sicheren Projektnamens für den Namespacenamen

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

Fügen Sie der VSTEMPLATE-Datei für die Projektvorlage das `ReplaceParameters="true"`-Attribut hinzu, wenn Sie auf die Datei verweisen:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Siehe auch

[Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md)  
[Vorgehensweise: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md)