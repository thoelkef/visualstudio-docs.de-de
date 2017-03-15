---
title: "Lokalisieren von Menübefehlen | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 869a1c878a591e6b755fc1311132e159d38ffe8f
ms.lasthandoff: 02/22/2017

---
# <a name="localizing-menu-commands"></a>Lokalisieren von Menübefehlen
Sie können im Menü lokalisierten Text eingeben und Symbolleiste Befehle durch das Erstellen von lokalisierten VSCT-Dateien und RESX-Dateien für das VSPackage und aktualisieren anschließend die Projektdateien um die Änderungen übernehmen lokalisiert.  
  
 Informationen über das Lokalisieren von der Installation finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Lokalisieren von Befehlsnamen  
 In VSPackages sind Menübefehle und Schaltflächen der Symbolleiste in der VSCT-Datei definiert.  
  
1.  In **Projektmappen-Explorer**, ändern Sie den Namen der VSCT-Datei vom *Dateiname*VSCT auf *Dateiname*.en US.vsct.  
  
2.  Erstellen Sie eine Kopie der *Dateiname*.en-US.vsct für jede lokalisierte Sprache.  
  
     Benennen Sie jede Kopie *Dateiname*.* Gebietsschema*VSCT, wobei *Gebietsschema* ist der Name für eine bestimmte Kultur. Eine Liste der Werte für Name die Kultur, finden Sie unter [von Microsoft zugewiesene Gebietsschema-IDs](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx).  
  
     Diese *Dateiname*.* Gebietsschema*VSCT-Dateien enthält lokalisierte Menütext für das Paket.  
  
3.  Öffnen Sie jede *Dateiname*.* Gebietsschema*VSCT-Datei zum Lokalisieren von Text.  
  
    1.  Ändern der [ButtonText](../extensibility/buttontext-element.md) Elementen Werte nach Bedarf für die jeweilige Sprache.  
  
    2.  Wenn Sie lokalisierte Symbole möchten, ändern Sie die [Bitmap](../extensibility/bitmap-element.md) Werte auf die Zieldateien.  
  
     Das folgende Beispiel zeigt, Englisch und Spanisch Schaltflächentext für einen Befehl, um ein Stammbaum Explorer-Toolfenster zu öffnen.  
  
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
  
1.  Benennen Sie VSPackage.resx in VSPackage.en-US.resx.  
  
2.  Erstellen Sie eine Kopie der Datei "VSPackage.en-US.resx" für jede lokalisierte Sprache.  
  
     Benennen Sie jede Kopie VSPackage. *Gebietsschema*.resx, wobei *Gebietsschema* ist der Name für eine bestimmte Kultur.  
  
3.  Benennen Sie "Resources.resx" in "Ressourcen.en-us.resx".  
  
4.  Erstellen Sie eine Kopie der Datei "Ressourcen.en-us.resx" für jede lokalisierte Sprache.  
  
     Benennen Sie jede Kopie Ressourcen. *Gebietsschema*.resx, wobei *Gebietsschema* ist der Name für eine bestimmte Kultur.  
  
5.  Öffnen Sie jede RESX-Datei, um die Zeichenfolgenwerte nach Bedarf für die jeweilige Sprache und Kultur zu ändern. Das folgende Beispiel zeigt die Definition der lokalisierten Ressource für die Titelleiste eines Toolfensters.  
  
     ["Ressourcen.en-us.resx"]  
  
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
 Sie müssen die Datei assemblyinfo.cs und die Projektdatei, die die lokalisierten Ressourcen integrieren ändern.  
  
1.  Aus der **Eigenschaften** Knoten **Projektmappen-Explorer**, öffnen Sie die Datei assemblyinfo.cs oder assemblyinfo.vb im Editor.  
  
2.  Fügen Sie den folgenden Eintrag hinzu.  
  
    ```c#  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Dadurch wird die Standardsprache Englisch (USA).  
  
3.  Entladen Sie das Projekt wird.  
  
4.  Öffnen Sie die Datei im Editor.  
  
5.  Suchen Sie die `ItemGroup` Element, das enthält `EmbeddedResource` Elemente.  
  
6.  In der `EmbeddedResource` Element, das Aufrufe VSPackage.en-US.resx, ersetzen die `ManifestResourceName` Element mit einer `LogicalName` Elementsatz zur `VSPackage.en-US.Resources`wie folgt.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Kopieren Sie für jede lokalisierte Sprache, die `EmbeddedResource` Element für VsPackage.en-US, und legen die **einschließen** Attribut und **LogicalName** Element der Kopie auf das Zielgebietsschema, wie im folgenden Beispiel gezeigt.  
  
8.  Jeder lokalisierte `VSCTCompile` Element hinzufügen eine `ResourceName` Element, zeigt `Menus.ctmenu`, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Speichern Sie die Datei, und Laden Sie das Projekt erneut.  
  
10. Erstellen Sie das Projekt.  
  
     Dies erstellt eine Hauptassembly und Ressourcenassemblys für jede Sprache. Weitere Informationen zur Lokalisierung des Bereitstellungsprozess finden Sie unter [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands im Vergleich zu OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Globalisierung und Lokalisierung](http://msdn.microsoft.com/Library/9a59696b-d89b-45bd-946d-c75da4732d02)
