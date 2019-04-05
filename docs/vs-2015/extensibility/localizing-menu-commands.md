---
title: Lokalisieren von Menübefehlen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27be664fb035af2c97f0536026b590c468b68b9e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957475"
---
# <a name="localizing-menu-commands"></a>Lokalisieren von Menübefehlen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können lokalisierten Text angeben, für die Menüs und Symbolleiste Befehle durch das Erstellen von lokalisierten VSCT-Dateien und die lokalisierte RESX-Dateien für Ihr VSPackage und aktualisieren Sie dann die Projektdateien, die Änderungen zu übernehmen.  
  
 Weitere Informationen zum Lokalisieren der installationserfahrung, finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Lokalisieren von Befehlsnamen  
 In VSPackages werden die Befehle des Menüs und Symbolleisten-Schaltflächen in der VSCT-Datei definiert.  
  
1. In **Projektmappen-Explorer**, ändern Sie den Namen der VSCT-Datei aus *Filename*VSCT zu *Filename*.en-US.vsct.  
  
2. Erstellen Sie eine Kopie der *Filename*.en-US.vsct für jede lokalisierte Sprache.  
  
    Benennen Sie jede Kopie *Filename*. *Gebietsschema*VSCT, wobei *Gebietsschema* Name einer bestimmten Kultur ist. Eine Liste der Werte für Name die Kultur, finden Sie unter [von Microsoft zugewiesene Gebietsschema-IDs](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx).  
  
    Diese *Filename*. *Gebietsschema*VSCT-Dateien lokalisierte Menütext für das Paket enthält.  
  
3. Öffnen Sie jede *Filename*. *Gebietsschema*VSCT-Datei zum Lokalisieren von Text.  
  
   1. Ändern der [ButtonText](../extensibility/buttontext-element.md) Elementen Werte nach Bedarf für die jeweilige Sprache.  
  
   2. Wenn Sie lokalisierte Symbole bereitstellen möchten, ändern Sie die [Bitmap](../extensibility/bitmap-element.md) Werte, um auf die Zieldateien zu verweisen.  
  
      Das folgende Beispiel zeigt die englische und spanische Schaltflächentext für einen Befehl zu einer Familie Struktur-Explorer-Toolfenster zu öffnen.  
  
      [FamilyTree.en-US.vsct]  
  
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
  
    [FamilyTree.es-ES.vsct]  
  
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
  
## <a name="localizing-other-text-resources"></a>Lokalisieren von anderen Textressourcen  
 Textressourcen als Befehlsnamen werden in Ressourcendateien (.resx) definiert.  
  
1.  Benennen Sie VSPackage.resx in VSPackage.en-US.resx an.  
  
2.  Stellen Sie eine Kopie der Datei "VSPackage.en-US.resx" für jede lokalisierte Sprache.  
  
     Benennen Sie jede Kopie VSPackage ein. *Gebietsschema*RESX, wobei *Gebietsschema* Name einer bestimmten Kultur ist.  
  
3.  Benennen Sie um Ressourcen.en-US.resx "Resources.resx".  
  
4.  Stellen Sie eine Kopie der Datei "Ressourcen.en-US.resx" für jede lokalisierte Sprache.  
  
     Benennen Sie jede Kopie Ressourcen. *Gebietsschema*RESX, wobei *Gebietsschema* Name einer bestimmten Kultur ist.  
  
5.  Öffnen Sie jede RESX-Datei, um die Zeichenfolgenwerte nach Bedarf für die jeweilige Sprache und Kultur zu ändern. Das folgende Beispiel zeigt die lokalisierte Ressourcen-Definition für die Titelleiste eines Toolfensters.  
  
     [Resources.en-US.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES.resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Das Integrieren lokalisierter Ressourcen in das Projekt  
 Sie müssen die Datei "assemblyinfo.cs" und die Projektdatei, integrieren die lokalisierten Ressourcen ändern.  
  
1.  Von der **Eigenschaften** Knoten **Projektmappen-Explorer**, öffnen Sie die Datei assemblyinfo.cs oder assemblyinfo.vb im Editor.  
  
2.  Fügen Sie den folgenden Eintrag hinzu.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Dadurch wird die Standardsprache Englisch (USA).  
  
3.  Entladen Sie das Projekt ein.  
  
4.  Öffnen Sie die Projektdatei im Editor ein.  
  
5.  Suchen Sie die `ItemGroup` -Element mit `EmbeddedResource` Elemente.  
  
6.  In der `EmbeddedResource` -Element, das Aufrufe VSPackage.en-US.resx, ersetzen die `ManifestResourceName` -Element mit einer `LogicalName` Element, und legen Sie auf `VSPackage.en-US.Resources`wie folgt.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Kopieren Sie für jede lokalisierte Sprache, die `EmbeddedResource` -Element für VsPackage.en-US, und legen Sie die **einschließen** Attribut und **LogicalName** Element der Kopie auf das Zielgebietsschema, wie im folgenden dargestellt. Beispiel:.  
  
8.  Auf jede lokalisierte `VSCTCompile` -Element, Hinzufügen einer `ResourceName` Element, zeigt `Menus.ctmenu`, wie im folgenden Beispiel gezeigt.  
  
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
 [Erweitern von Menüs und Befehle](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands im Vergleich zu OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Globalisierung und Lokalisierung](http://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)
