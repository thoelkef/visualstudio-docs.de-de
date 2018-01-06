---
title: "Lokalisieren von Menübefehlen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
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
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 77bd698149ca4e73b462fc3ada9256ba5911177e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="localizing-menu-commands"></a>Lokalisieren von Menübefehlen
Können Sie lokalisierte Text angeben, für die Menüs und Symbolleiste Befehle durch Erstellen von lokalisierten VSCT-Dateien und RESX-Dateien für Ihr VSPackage, und klicken Sie dann die Projektdateien aktualisieren die Änderungen einzubeziehen lokalisiert.  
  
 Informationen zum Lokalisieren der Installationsvorgang finden Sie unter [VSIX-Pakete zum Lokalisieren von](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Lokalisieren von Befehlsnamen  
 VSPackages Menübefehle und Schaltflächen der Symbolleiste, die in der VSCT-Datei definiert sind.  
  
1.  In **Projektmappen-Explorer**, ändern Sie den Namen der VSCT-Datei aus *Filename*VSCT auf *Filename*.en-US.vsct.  
  
2.  Erstellen Sie eine Kopie der *Filename*.en-US.vsct für jede lokalisierte Sprache.  
  
     Benennen Sie jede Kopie *Filename*. *Gebietsschema*VSCT, wobei *Gebietsschema* ist der Name für eine bestimmte Kultur. Eine Liste der Namenswerte Kultur, finden Sie unter [von Microsoft zugewiesene Gebietsschema-IDs](https://msdn.microsoft.com/en-us/library/windows/apps/jj657969.aspx).  
  
     Diese *Filename*. *Gebietsschema*VSCT-Dateien enthält die lokalisierten Menütext für Ihr Paket.  
  
3.  Öffnen der einzelnen *Filename*. *Gebietsschema*VSCT-Datei zum Lokalisieren von Text.  
  
    1.  Ändern der [ButtonText](../extensibility/buttontext-element.md) Elementen Werte nach Bedarf für die jeweilige Sprache.  
  
    2.  Wenn Sie lokalisierte Symbole gewähren möchten, ändern Sie die [Bitmap](../extensibility/bitmap-element.md) Werte auf der TARGETS-Dateien verweisen.  
  
     Das folgende Beispiel zeigt Englisch und Spanisch Schaltflächentext für einen Befehl aus, um eine Familie Struktur-Explorer-Toolfenster zu öffnen.  
  
     [FamilyTree.en US.vsct]  
  
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
  
     [FamilyTree.es ES.vsct]  
  
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
 Textressourcen, mit Ausnahme des Befehlsnamen werden in Ressourcendateien (.resx) definiert.  
  
1.  Benennen Sie VSPackage.resx in VSPackage.en-US.resx.  
  
2.  Erstellen Sie eine Kopie der Datei VSPackage.en-US.resx für jede lokalisierte Sprache.  
  
     Benennen Sie jede Kopie VSPackage ein. *Gebietsschema*RESX, wobei *Gebietsschema* ist der Name für eine bestimmte Kultur.  
  
3.  Benennen Sie um Resources.en-US.resx "Resources.resx".  
  
4.  Erstellen Sie eine Kopie der Datei Resources.en-US.resx für jede lokalisierte Sprache.  
  
     Benennen Sie jede Kopie Ressourcen. *Gebietsschema*RESX, wobei *Gebietsschema* ist der Name für eine bestimmte Kultur.  
  
5.  Öffnen Sie jede RESX-Datei, um die Zeichenfolgenwerte entsprechend der Einstellung für die jeweilige Sprache und Kultur zu ändern. Im folgende Beispiel wird gezeigt, die lokalisierte Ressourcen-Definition für die Titelleiste eines Toolfensters.  
  
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
  
## <a name="incorporating-localized-resources-into-the-project"></a>Einbinden von lokalisierten Ressourcen in das Projekt  
 Sie müssen die Datei assemblyinfo.cs und die Projektdatei, integrieren die lokalisierten Ressourcen ändern.  
  
1.  Aus der **Eigenschaften** Knoten **Projektmappen-Explorer**, assemblyinfo.cs oder assemblyinfo.vb im Editor zu öffnen.  
  
2.  Fügen Sie den folgenden Eintrag hinzu.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Dadurch wird die Standardsprache Englisch (USA).  
  
3.  Entladen Sie das Projekt.  
  
4.  Öffnen Sie die Projektdatei im Editor.  
  
5.  Suchen Sie die `ItemGroup` Element, das enthält `EmbeddedResource` Elemente.  
  
6.  In der `EmbeddedResource` Element, das Aufrufe VSPackage.en-US.resx, ersetzen die `ManifestResourceName` Element mit einer `LogicalName` Elementsatz um `VSPackage.en-US.Resources`wie folgt.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7.  Kopieren Sie für jede lokalisierte Sprache der `EmbeddedResource` -Element für VsPackage.en-US, und legen die **Include** Attribut und **LogicalName** Element der Kopie auf das Zielgebietsschema, wie im folgenden dargestellt Beispiel:.  
  
8.  Jeder lokalisierte `VSCTCompile` Element, Hinzufügen einer `ResourceName` Elements, verweist `Menus.ctmenu`, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Speichern Sie die Projektdatei, und Laden Sie das Projekt erneut.  
  
10. Erstellen Sie das Projekt.  
  
     Dies erstellt eine Hauptassembly und Ressourcenassemblys für jede Sprache. Informationen zum Lokalisieren von den Bereitstellungsprozess finden Sie unter [Lokalisieren von VSIX-Pakete](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Menüs und Befehle](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands im Vergleich zu OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)