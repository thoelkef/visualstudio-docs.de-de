---
title: Define a custom modeling toolbox item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac299f18e544ef4f3215707abbdc3d9e8d266de6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299290"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Definieren eines benutzerdefinierten Elements für die Modellerstellungstoolbox
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Für die einfache Erstellung eines Elements oder einer Gruppe von Elementen gemäß eines Musters, das Sie häufig verwenden, können Sie der Toolbox mit Modellierungsdiagrammen in Visual Studio neue Tools hinzufügen. Sie können diese Toolboxelemente an andere Visual Studio-Benutzer verteilen.

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Ein benutzerdefiniertes Tool erstellt ein oder mehrere neue Elemente in einem Diagramm. Sie können z. B. ein benutzerdefiniertes Tool zum Erstellen von Elementen, wie beispielsweise die folgenden, erstellen:

- Ein Paket, das mit dem .NET-Profil verknüpft ist, und eine Klasse mit dem .NET-Stereotyp.

- Ein Paar von Klassen, das durch eine Zuordnung verknüpft ist, um das Observer-Muster darzustellen.

> [!NOTE]
> Sie können diese Methode verwenden, um Elementtools zu erstellen. Das heißt, Sie können Tools erstellen, die Sie aus der Toolbox in ein Diagramm ziehen. Sie können keine Connector-Tools erstellen.

## <a name="DefineTool"></a> Defining a Custom Modeling Tool

#### <a name="to-define-a-custom-modeling-tool"></a>So definieren Sie ein benutzerdefiniertes Modellierungstool

1. Erstellen Sie ein UML-Diagramm, das ein Element oder eine Gruppe von Elementen enthält.

    - Diese Elemente können Beziehungen untereinander haben und untergeordnete Elemente wie Ports, Attribute, Vorgänge oder Pins aufweisen.

2. Speichern Sie das Diagramm mit dem Namen, den das neue Tool erhalten soll. On the **File** menu, use **Save…As**.

3. Kopieren Sie mithilfe von Windows-Explorer die zwei Diagrammdateien in den folgenden Ordner oder einen beliebigen Unterordner:

     *YourDocuments* **\Visual Studio\Architecture Tools\Custom Toolbox Items**

    - Erstellen Sie diesen Ordner, wenn er nicht bereits vorhanden ist. You might have to create both **Architecture Tools** and **Custom Toolbox Items**.

    - Copy both diagram files, one with a name that ends "…**diagram**" and the other with a name that ends "…**diagram.layout**"

    - Sie können beliebig viele benutzerdefinierte Tools erstellen. Verwenden Sie ein Diagramm für jedes Tool.

4. (Optional) Create a **.tbxinfo** file as described in [How to Define the Properties of Custom Tools](#tbxinfo), and add it to the same directory. Auf diese Weise können Sie ein Toolboxsymbol, eine QuickInfo usw. definieren.

    - A single **.tbxinfo** file can be used to define several tools. Diese kann auf Diagrammdateien verweisen, die sich in Unterordnern befinden.

5. Starten Sie Visual Studio neu. Das zusätzliche Tool wird in der Toolbox für den entsprechenden Diagrammtyp angezeigt.

### <a name="what-the-custom-tool-will-replicate"></a>Was vom benutzerdefinierten Tool repliziert wird
 Ein benutzerdefiniertes Tool repliziert die meisten Funktionen des Quelldiagramms:

- Namen Wenn ein Element aus der Toolbox erstellt wird, wird bei Bedarf eine Zahl am Ende des Namens hinzugefügt, um doppelte Namen im selben Namespace zu verhindern.

- Farben, Größen und Formen

- Stereotype und Paketprofile

- Eigenschaftswerte wie z. B. Is Abstract

- Verknüpfte Arbeitsaufgaben

- Multiplizitäten und andere Eigenschaften von Beziehungen

- Die relativen Positionen von Formen

  Die folgenden Funktionen werden in einem benutzerdefinierten Tool nicht beibehalten:

- Einfache Formen Hierbei handelt es sich um Formen, die nicht im Zusammenhang mit Modellelementen stehen, die Sie in einigen Arten von Diagrammen zeichnen können.

- Connector-Routing Wenn Sie Connectors manuell weiterleiten, wird das Routing nicht beibehalten, wenn das Tool verwendet wird. Die Positionen einiger geschachtelter Formen, wie z. B. Ports, werden in Bezug auf ihre Besitzer nicht beibehalten.

## <a name="tbxinfo"></a> How to Define the Properties of Custom Tools
 A toolbox information ( **.tbxinfo**) file allows you to specify a toolbox name, icon, tooltip, tab, and help keyword for one or more custom tools. Give it any name, such as **MyTools.tbxinfo**.

 Die allgemeine Form der Datei ist wie folgt:

```
<?xml version="1.0" encoding="utf-8" ?>
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">
  <customToolboxItem fileName="MyObserverTool.classdiagram">
    <displayName>
       <value>Observer Pattern</value>
    </displayName>
    <tabName>
       <value>UML Class Diagram</value>
    </tabName>
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>
    <f1Keyword>
      <value>ObserverPatternHelp</value>
    </f1Keyword>
    <tooltip>
       <value>Create a pair of classes</value>
    </tooltip>
  </customToolboxItem>
</customToolboxItems>
```

 Der Wert jedes Elements kann Folgendes sein:

- `<bmp fileName="…"/>` für das Toolboxsymbol und `<value>string</value>` für die anderen Elemente, wie in dem Beispiel dargestellt.

  \- oder -

- `<resource fileName="Resources.dll"`

   `baseName="Observer.resources" id="Observer.tabname" />`

   In diesem Fall geben Sie eine kompilierte Assembly an, in der die Zeichenfolgenwerte als Ressourcen kompiliert wurden.

  Fügen Sie einen `<customToolboxItem>`-Knoten für jedes Toolboxelement hinzu, das Sie definieren möchten.

  The nodes in the **.tbxinfo** file are as follows. Es gibt einen Standardwert für jeden Knoten.

|Knotenname|Definiert|
|---------------|-------------|
|displayName|Der Name des Toolboxelements.|
|tabName|Die Toolboxregisterkarte, in der das Element angezeigt werden soll. Sie können entweder den Namen der normalen Registerkarte für diesen Typ von Diagramm oder einen anderen Namen angeben.|
|Bild|The location of the bitmap ( **.bmp**) file, which must have height and width of 16, and a color depth of 24 bits.|
|f1Keyword|Das Schlüsselwort, mit dem ein Hilfethema gesucht wird.|
|QuickInfo|Eine QuickInfo für dieses Tool.|

 Sie können die Bitmapdatei in Visual Studio bearbeiten und ihre Höhe und Breite im Eigenschaftenfenster auf 16 festlegen.

> [!NOTE]
> Wenn Sie beginnen, eine TBXINFO-Datei zu verwenden, nachdem Sie mit der alleinigen Verwendung von Diagrammdateien experimentiert haben, stellen sie möglicherweise fest, dass die Toolbox sowohl die alten als auch die neuen Versionen eines Toolboxelements enthält. Dies kann auch auftreten, wenn der Name der Diagrammdatei in der TBXINFO-Datei falsch eingegeben wurde. If this occurs, on the shortcut menu of the toolbox choose **Reset Toolbox**. Die benutzerdefinierten Toolboxelemente werden ausgeblendet. Starten Sie Visual Studio neu; daraufhin werden die richtigen benutzerdefinierten Elemente angezeigt.

## <a name="Extension"></a> How to Distribute Toolbox Items in a Visual Studio Extension
 You can distribute toolbox items to other [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] users by packaging them into a Visual Studio Extension (VSIX). Sie können Befehle, Profile und andere Erweiterungen in der gleichen VSIX-Datei verpacken. For more information, see [Deploying Visual Studio Extensions](https://go.microsoft.com/fwlink/?LinkId=160780).

 Die übliche Vorgehensweise zum Erstellen einer Visual Studio-Erweiterung besteht darin, die VSIX-Projektvorlage zu verwenden. Zu diesem Zweck muss [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] installiert sein.

#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>So fügen Sie ein Toolboxelement zu einer Visual Studio-Erweiterung hinzu

1. [Create and test one or more custom tools](#DefineTool).

2. [Create a .tbxinfo file](#tbxinfo) that references the tools.

3. Öffnen Sie ein vorhandenes Visual Studio-Erweiterungsprojekt.

     \- oder -

     Definieren Sie ein neues Visual Studio-Erweiterungsprojekt.

    1. Wählen Sie im Menü **Datei** die Optionsfolge **Neu**, **Projekt**aus.

    2. In the **New Project** dialog box, under **Installed Templates**, choose **Visual C#** , **Extensibility**, **VSIX project**.

4. Fügen Sie die Toolboxdefinitionen dem Projekt hinzu. Include the **.tbxinfo** file, the diagram files, bitmap files, and any resource files, and make sure that they are included in the VSIX.

    - In Solution Explorer, on the shortcut menu of the VSIX project, choose **Add**, **Existing Item**. In the dialog box, set **Objects of Type: All Files**. Locate the files, select them all, and then choose **Add**.

        > [!NOTE]
        > In diesem Projekt können die Diagrammdateien nicht im Modell-Editor geöffnet werden.

5. Legen Sie die folgenden Eigenschaften aller Dateien fest, die Sie gerade hinzugefügt haben. Sie können ihre Eigenschaften gleichzeitig festlegen, indem Sie alle im Projektmappen-Explorer auswählen. Achten Sie darauf, dass Sie keine Änderungen an den Eigenschaften der anderen Dateien im Projekt vornehmen.

     **Copy to Output Directory** = **Copy Always**

     **Build Action** = **Content**

     **Include in VSIX** = **true**

6. Öffnen Sie **source.extension.vsixmanifest**. Die Datei wird im Erweiterungsmanifest-Editor geöffnet.

7. Under **Metadata**, add a description for the custom tools.

     Under **Assets**, choose **New** and then set the fields in the dialog as follows:

    - **Type** = **Custom Extension Type**

    - Typ = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`

        > [!NOTE]
        > Dies ist keine der Optionen in der Dropdownliste. Sie müssen sie über die Tastatur eingeben.

    - **Source** = **File on filesystem**.

    - **Path** = your **.tbxinfo** file, for example **MyTools.tbxinfo**

8. Erstellen Sie das Projekt.

9. **To verify that the extension works**, press F5. Die experimentelle Instanz von Visual Studio wird geöffnet.

     Erstellen oder öffnen Sie in der experimentellen Instanz ein UML-Diagramm des relevanten Typs. Stellen Sie sicher, dass das neue Tool in der Toolbox angezeigt wird und dass Elemente ordnungsgemäß erstellt werden.

10. **To obtain a VSIX file for deployment:** In Windows Explorer, open the folder **.\bin\Debug** or **.\bin\Release** to find the **.vsix** file. Dies ist eine [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Erweiterungsdatei. Sie kann auf dem Computer installiert und an andere Visual Studio-Benutzer gesendet werden.

#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>So installieren Sie benutzerdefinierte Tools aus einer Visual Studio-Erweiterung

1. Öffnen Sie im Windows-Explorer oder in Visual Studio die `.vsix`-Datei.

2. Choose **Install** in the dialog box that appears.

3. To uninstall or temporarily disable the extension, open **Extensions and Updates** from the **Tools** menu.

## <a name="localization"></a>Lokalisierung
 Sie können eine Erweiterung erstellen, die bei der Installation auf einem anderen Computer Toolnamen und QuickInfos in der Sprache des Zielcomputers anzeigt.

#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>So stellen Sie Versionen des Tools in mehreren Sprachen bereit

1. Erstellen Sie ein Visual Studio-Erweiterungsprojekt, das ein oder mehrere benutzerdefinierte Tools enthält.

    In the **.tbxinfo** file, use the resource file method to define the tool's `displayName`, toolbox `tabName`, and the tooltip. Erstellen Sie eine Ressourcendatei, in der diese Zeichenfolgen definiert sind, kompilieren Sie diese in eine Assembly, und verweisen Sie dann aus der TBXINFO-Datei darauf.

2. Erstellen Sie zusätzliche Assemblys, die Ressourcendateien mit Zeichenfolgen in anderen Sprachen enthalten.

3. Legen Sie jede zusätzliche Assembly in einen Ordner, dessen Name der Kulturcode für die Sprache ist. For example, place a French version of the assembly inside a folder that is named **fr**.

4. Sie sollten einen neutralen Kulturcode verwenden, also in der Regel zwei Buchstaben. Verwenden Sie keine speziellen Kulturcodes wie `fr-CA`. For more information about culture codes, see [CultureInfo.GetCultures method](https://go.microsoft.com/fwlink/?LinkId=160782), which provides a complete list of culture codes.

5. Erstellen Sie die Visual Studio-Erweiterung, und verteilen Sie sie.

6. Wenn die Erweiterung auf einem anderen Computer installiert ist, wird die Version der Ressourcendatei für die lokale Kultur des Benutzers automatisch geladen. Wenn Sie keine Version für die Kultur des Benutzers angegeben haben, werden die Standardressourcen verwendet.

   Sie können diese Methode verwenden, um verschiedene Versionen des Prototypdiagramms zu installieren. Die Namen von Elementen und Connectors sind in jeder Installation identisch.

## <a name="other-toolbox-operations"></a>Andere Toolboxvorgänge
 In [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] können Sie normalerweise die Toolbox anpassen, indem Sie Tools umbenennen, diese in andere Toolboxregisterkarten verschieben und löschen. Aber diese Änderungen werden für benutzerdefinierte Modellierungstools, die mit den in diesem Thema beschriebenen Verfahren erstellt wurden, nicht beibehalten. Beim Neustart von [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] werden benutzerdefinierte Tools wieder mit ihren definierten Namen und Toolboxspeicherorten angezeigt.

 Furthermore, your custom tools will disappear if you perform the **Reset Toolbox** command. Sie werden jedoch wieder angezeigt, wenn Sie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] neu starten.

## <a name="see-also"></a>Siehe auch
 [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md) [Define a profile to extend UML](../modeling/define-a-profile-to-extend-uml.md) [Define a menu command on a modeling diagram](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Define validation constraints for UML models](../modeling/define-validation-constraints-for-uml-models.md)
