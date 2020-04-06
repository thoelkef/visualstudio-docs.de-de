---
title: Lokalisieren von Menübefehlen | Microsoft Docs
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d363b495eb84dc3bfeabd7bf7c5d05fabcbc4d36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702949"
---
# <a name="localize-menu-commands"></a>Lokalisieren von Menübefehlen

Sie können lokalisierten Text für Menü- und Symbolleistenbefehle bereitstellen, indem Sie lokalisierte *.vsct-Dateien* und lokalisierte *.resx-Dateien* für Ihr VSPackage erstellen und dann die Projektdateien aktualisieren, um die Änderungen zu integrieren.

Informationen zum Lokalisieren der Installationsumgebung finden Sie unter Lokalisieren von [VSIX-Paketen](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Lokalisieren von Befehlsnamen

In VSPackages werden Menübefehle und Symbolleistenschaltflächen in der *.vsct-Datei* definiert.

1. Ändern Sie im **Projektmappen-Explorer**den Namen der *.vsct-Datei* von *filename.vsct* in *filename.en-US.vsct*.

2. Erstellen Sie eine Kopie von *filename.en-US.vsct* für jede lokalisierte Sprache.

    Benennen Sie jede Kopie *Dateiname. Locale.vsct*, wobei *"Locale"* ein bestimmter Kulturname ist. Eine Liste der Kulturnamenwerte finden Sie [unter Gebietsschema-IDs, die von Microsoft zugewiesen wurden.](/windows/uwp/publish/supported-languages)

    Diese *Dateinamen. Locale.vsct-Dateien* enthalten den lokalisierten Menütext für Ihr Paket.

3. Öffnen Sie jeden *Dateinamen. Locale.vsct-Datei,* um den Text zu lokalisieren.

   1. Ändern Sie die [ButtonText-Elementwerte](../extensibility/buttontext-element.md) entsprechend der jeweiligen Sprache.

   2. Wenn Sie lokalisierte Symbole bereitstellen, ändern Sie die [Bitmap-Werte](../extensibility/bitmap-element.md) so, dass sie auf die Zieldateien verweisen.

      Das folgende Beispiel zeigt den englischen und spanischen Schaltflächentext für einen Befehl zum Öffnen eines Familienbaum-Explorer-Toolfensters.

      [*FamilyTree.de-US.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Family Tree Explorer</ButtonText>
     </Strings>
   </Button>
   ```

    [*FamilyTree.es-ES.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Explorar el arbol genealogico</ButtonText>
     </Strings>
   </Button>
   ```

## <a name="localize-other-text-resources"></a>Lokalisieren anderer Textressourcen

Textressourcen außer Befehlsnamen werden in Ressourcendateien (*.resx*) definiert.

1. *VsPackage.resx* in *VSPackage.en-US.resx*umbenennen.

2. Erstellen Sie eine Kopie der *Datei VSPackage.en-US.resx* für jede lokalisierte Sprache.

     Benennen Sie jede Kopie *VSPackage. Locale.resx*, wobei *"Locale"* ein bestimmter Kulturname ist.

3. *Resources.resx* in *Resources.en-US.resx umbenennen.*

4. Erstellen Sie eine Kopie der Datei *Resources.en-US.resx* für jede lokalisierte Sprache.

     Benennen Sie jede Kopie *Ressourcen. Locale.resx*, wobei *"Locale"* ein bestimmter Kulturname ist.

5. Öffnen Sie jede *.resx-Datei,* um die Zeichenfolgenwerte entsprechend der jeweiligen Sprache und Kultur zu ändern. Das folgende Beispiel zeigt die lokalisierte Ressourcendefinition für die Titelleiste eines Werkzeugfensters.

     [*Ressourcen.de-US.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-ES.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Integrieren lokalisierter Ressourcen in das Projekt

Sie müssen die *assemblyinfo.cs* Und die Projektdatei ändern, um die lokalisierten Ressourcen zu integrieren.

1. Öffnen Sie im **Eigenschaftenknoten** im **Projektmappen-Explorer** *assemblyinfo.cs* oder *assemblyinfo.vb* im Editor.

2. Fügen Sie den folgenden Eintrag hinzu.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Dadurch wird US-Englisch als Standardsprache festgelegt.

3. Entladen Sie das Projekt.

4. Öffnen Sie die Projektdatei im Editor.

5. Fügen Sie `Project` im Stammelement `PropertyGroup` ein `UICulture` Element mit einem Element hinzu, das mit der Standardsprache übereinstimmt.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Dadurch wird US-Englisch als Standard-UI-Kultur für Windows Presentation Foundation (WPF)-Steuerelemente festgelegt.

6. Suchen `ItemGroup` Sie das `EmbeddedResource` Element, das Elemente enthält.

7. Ersetzen `EmbeddedResource` Sie im Element *VSPackage.en-US.resx*das `ManifestResourceName` `LogicalName` Element wie folgt `VSPackage.en-US.Resources`durch ein Element, das auf festgelegt ist:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Kopieren Sie für jede `EmbeddedResource` lokalisierte `VsPackage.en-US`Sprache das Element für , und legen Sie das **Include-Attribut** und das **LogicalName-Element** der Kopie auf das Zielgebietsschema fest.

9. Fügen Sie `VSCTCompile` jedem lokalisierten `ResourceName` Element ein `Menus.ctmenu`Element hinzu, das auf zeigt, wie im folgenden Beispiel gezeigt:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Speichern Sie die Projektdatei, und laden Sie das Projekt neu.

11. Erstellen Sie das Projekt.

     Dadurch werden eine Hauptassembly und Ressourcenassemblys für jede Sprache erstellt. Informationen zur Lokalisierung des Bereitstellungsprozesses finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Weitere Informationen

- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
- [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)
