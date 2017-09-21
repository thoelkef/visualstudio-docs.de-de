---
title: "Der Visual Studio-Men&#252;leiste hinzuf&#252;gen ein Men&#252; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Menüs obersten Ebene erstellen"
  - "Menüs der obersten Ebene"
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 51
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 51
---
# Der Visual Studio-Men&#252;leiste hinzuf&#252;gen ein Men&#252;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise veranschaulicht, wie ein Menü auf der Menüleiste von der integrierten Entwicklungsumgebung \(IDE\) von Visual Studio hinzufügen. Die IDE\-Menüleiste enthält z. B. die Kategorie **Datei**, **Bearbeiten**, **Ansicht**, **Fenster**, und **Hilfe**.  
  
 Der Visual Studio\-Menüleiste ein neues Menü hinzufügen, berücksichtigen Sie, ob die Befehle in einem vorhandenen Menü eingefügt werden soll. Weitere Informationen zur Platzierung der Befehl finden Sie unter [Menüs und Befehlen für Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).  
  
 Menüs werden in der VSCT\-Datei des Projekts deklariert. Weitere Informationen zu Menüs und VSCT\-Dateien finden Sie unter [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Diese exemplarische Vorgehensweise durcharbeiten, können Sie ein Menü mit dem Namen erstellen **TestMenu** die einen Befehl enthält.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eines VSIX\-Projekts mit einer benutzerdefinierten Befehls\-Elementvorlage  
  
1.  Erstellen Sie ein VSIX\-Projekt namens `TopLevelMenu`. Sie finden die VSIX\-Projektvorlage in die **Neues Projekt** Dialogfeld unter **Visual C\#\-** \/ **Erweiterbarkeit**.  Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierten Befehl Elementvorlage mit dem Namen **TestCommand**. In der **Projektmappen\-Explorer**, mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen \/ neues Element**. In der **Neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c\# \/ Erweiterbarkeit** und wählen Sie **Befehl benutzerdefinierte**. In den **Namen** Feld am unteren Rand des Fensters, das Ändern der Name der Befehlsdatei an **TestCommand.cs**.  
  
## Erstellen eines Menüs in der Menüleiste der IDE  
  
#### Um ein Menü zu erstellen.  
  
1.  In **Projektmappen\-Explorer**, TestCommandPackage.vsct zu öffnen.  
  
     Am Ende der Datei besteht ein \< Symbole \>\-Knoten, der mehrere \< GuidSymbol \>\-Knoten enthält. Fügen Sie ein neues Symbol, klicken Sie im Knoten mit dem Namen GuidTestCommandPackageCmdSet wie folgt:  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  Erstellen Sie einen leeren \< Menüs \>\-Knoten im Knoten \< Befehle \> unmittelbar vor dem \< Gruppen \>. Klicken Sie im Knoten \< Menüs \> Fügen Sie einen Knoten \< Menü \> wie folgt:  
  
    ```xml  
    <Menus>  
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">  
            <Parent guid="guidSHLMainMenu"  
                    id="IDG_VS_MM_TOOLSADDINS" />  
            <Strings>  
              <ButtonText>TestMenu</ButtonText>  
              <CommandName>TestMenu</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Die `guid` und `id` Werte des Menüs Geben Sie den Befehlssatz, und das Menü in den Befehlssatz.  
  
     Die `guid` und `id` Werte des übergeordneten Elements positionieren klicken Sie im Menü auf den Abschnitt der Visual Studio\-Menüleiste, die die Tools und Add\-Ins Menüs enthält.  
  
     Der Wert der `CommandName` Zeichenfolge gibt an, dass der Text im Menüelement angezeigt werden soll.  
  
3.  Klicken Sie im Abschnitt \< Gruppen \> Suchen Sie \< Gruppe \>, und ändern Sie das Element \< Parent \> Klicken Sie im Menü auf, die wir gerade hinzugefügt:  
  
    ```c#  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     Dadurch wird den Teil von Gruppe für das neue Menü.  
  
4.  Suchen Sie die `Buttons` Abschnitt. Beachten Sie, dass die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Paketvorlage wurde generiert ein `Button` \-Element, das das übergeordnete Element festgelegt hat `MyMenuGroup`. Daher wird dieser Befehl im Menü angezeigt.  
  
## Erstellen und Testen der Erweiterung  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Eine Instanz der experimentellen Instanz sollte angezeigt werden.  
  
2.  Die Menüleiste in der experimentellen Instanz sollte enthalten eine **TestMenu** Menü.  
  
3.  Auf der **TestMenu** Menü klicken Sie auf **Test\-Invoke\-Command**.  
  
     Ein Meldungsfeld angezeigt werden soll, und die Meldung "TestCommand Paket in TopLevelMenu.TestCommand.MenuItemCallback\(\)" angezeigt. Dies gibt an, dass der neue Befehl funktioniert.  
  
## Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)