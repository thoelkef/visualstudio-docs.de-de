---
title: Lokalisieren von Menübefehlen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62c6011d1a04b60d1bd0cc538e9560d8977f9799
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344670"
---
# <a name="localize-menu-commands"></a>Lokalisieren von Menübefehlen
Sie können lokalisierten Text für die Menü-und Symbolleistenbefehle bereitstellen, durch das Erstellen von lokalisierten *VSCT* Dateien und lokalisierte *resx* -Dateien für das VSPackage, und aktualisieren Sie dann die Projektdateien integriert die ändert.

 Weitere Informationen zum Lokalisieren der installationserfahrung, finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Lokalisieren von Befehlsnamen
 VSPackages, Menübefehle und Schaltflächen der Symbolleiste im definiert sind die *VSCT* Datei.

1. In **Projektmappen-Explorer**, ändern Sie den Namen des der *VSCT* Datei *filename.vsct* zu *filename.en-US.vsct*.

2. Erstellen Sie eine Kopie der *filename.en-US.vsct* für jede lokalisierte Sprache.

    Benennen Sie jede Kopie *Filename. {} Gebietsschema} VSCT*, wobei *{Gebietsschema}* Name einer bestimmten Kultur ist. Eine Liste der Werte für Name die Kultur, finden Sie unter [von Microsoft zugewiesene Gebietsschema-IDs](/windows/uwp/publish/supported-languages).

    Diese *Dateiname. Locale.VSCT* Dateien lokalisierte Menütext für das Paket enthält.

3. Öffnen Sie jede *Dateiname. Locale.VSCT* Datei zum Lokalisieren von Text.

   1. Ändern der [ButtonText](../extensibility/buttontext-element.md) Elementen Werte nach Bedarf für die jeweilige Sprache.

   2. Wenn Sie lokalisierte Symbole bereitstellen möchten, ändern Sie die [Bitmap](../extensibility/bitmap-element.md) Werte, um auf die Zieldateien zu verweisen.

      Das folgende Beispiel zeigt die englische und spanische Schaltflächentext für einen Befehl zu einer Familie Struktur-Explorer-Toolfenster zu öffnen.

      [*FamilyTree.en-US.vsct*]

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

## <a name="localize-other-text-resources"></a>Lokalisieren von anderen Textressourcen
 Textressourcen als Befehlsnamen werden definiert, in der Ressource (*resx*) Dateien.

1. Benennen Sie *VSPackage.resx* zu *VSPackage.en-US.resx*.

2. Erstellen einer Kopie der *VSPackage.en-US.resx* -Datei für jede lokalisierte Sprache.

     Benennen Sie jede Kopie *VSPackage. {} Gebietsschema} resx*, wobei *{Gebietsschema}* Name einer bestimmten Kultur ist.

3. Benennen Sie *"Resources.resx"* zu *Ressourcen.en-US.resx*.

4. Erstellen einer Kopie der *Ressourcen.en-US.resx* -Datei für jede lokalisierte Sprache.

     Benennen Sie jede Kopie *Ressourcen. {} Gebietsschema} resx*, wobei *{Gebietsschema}* Name einer bestimmten Kultur ist.

5. Öffnen Sie jede *resx* Datei so ändern Sie die Zeichenfolge Werte nach Bedarf für die jeweilige Sprache und Kultur. Das folgende Beispiel zeigt die lokalisierte Ressourcen-Definition für die Titelleiste eines Toolfensters.

     [*Resources.en-US.resx*]

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

## <a name="incorporate-localized-resources-into-the-project"></a>Lokalisierte Ressourcen in das Projekt integrieren
 Müssen Sie ändern die *"AssemblyInfo.cs"* -Datei und die Projektdatei, die lokalisierten Ressourcen zu integrieren.

1. Von der **Eigenschaften** Knoten **Projektmappen-Explorer**öffnen *"AssemblyInfo.cs"* oder *assemblyinfo.vb* im Editor.

2. Fügen Sie den folgenden Eintrag hinzu.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Dadurch wird die Standardsprache Englisch (USA).

3. Entladen Sie das Projekt ein.

4. Öffnen Sie die Projektdatei im Editor ein.

5. Suchen Sie die `ItemGroup` -Element mit `EmbeddedResource` Elemente.

6. In der `EmbeddedResource` -Element, das Aufrufe *VSPackage.en-US.resx*, ersetzen die `ManifestResourceName` -Element mit einer `LogicalName` Element, und legen Sie auf `VSPackage.en-US.Resources`wie folgt.

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

7. Kopieren Sie für jede lokalisierte Sprache, die `EmbeddedResource` -Element für `VsPackage.en-US`, und legen Sie die **einschließen** Attribut und **LogicalName** Element der Kopie auf das Zielgebietsschema, wie im folgenden dargestellt. Beispiel:.

8. Auf jede lokalisierte `VSCTCompile` -Element, Hinzufügen einer `ResourceName` Element, zeigt `Menus.ctmenu`, wie im folgenden Beispiel gezeigt.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

9. Speichern Sie die Projektdatei, und Laden Sie das Projekt.

10. Erstellen Sie das Projekt.

     Dies erstellt eine Hauptassembly und Ressourcenassemblys für jede Sprache. Weitere Informationen zur Lokalisierung des Bereitstellungsprozess finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Siehe auch
- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
- [MenuCommands im Vergleich zu OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)
- [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)