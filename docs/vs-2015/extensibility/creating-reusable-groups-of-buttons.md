---
title: Erstellen von Wiederverwendbaren Gruppen von Schaltflächen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: 45
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c88dbb1ac3b2c9419dc111843e360623dd15c7fe
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956489"
---
# <a name="creating-reusable-groups-of-buttons"></a>Erstellen von wiederverwendbaren Gruppen von Schaltflächen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Befehlsgruppe ist eine Auflistung von Befehlen, die immer zusammen in einem Menü oder Symbolleiste angezeigt werden. Alle Befehlsgruppe kann erneut verwendet werden, von verschiedenen übergeordneten Menüs im Abschnitt CommandPlacements der VSCT-Datei zuweisen.  
  
 Befehlsgruppen Schaltflächen in der Regel enthalten, aber sie können auch die anderen Menüs oder Kombinationsfelder enthalten.  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>Erstellen Sie eine wiederverwendbare Gruppe von Schaltflächen  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `ReusableButtons`. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierten Befehl-Elementvorlage, die mit dem Namen **ReusableCommand**. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual C# / Erweiterbarkeit** , und wählen Sie **benutzerdefinierten Befehls**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an **ReusableCommand.cs**.  
  
3.  Finden Sie in der VSCT-Datei unter dem Abschnitt "Symbols", und suchen Sie nach der GuidSymbol-Element, das Gruppen und Befehle für das Projekt enthält. Es sollten GuidReusableCommandPackageCmdSet benannt werden.  
  
4.  Fügen Sie eine IDSymbol für jede Schaltfläche, die Sie der Gruppe, wie im folgenden Beispiel hinzufügen.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     Die Elementvorlage für den Befehl erstellt standardmäßig eine Gruppe namens **"MyGroup"** und eine Schaltfläche mit dem Namen ab, die Sie angegeben haben, zusammen mit einem IDSymbol-Eintrag für jede.  
  
5.  Erstellen Sie im Abschnitt Gruppen ein Group-Element mit den gleichen GUID und ID-Attributen wie diejenigen in den Abschnitt "Symbols" angegeben ist. Sie können auch eine vorhandene Gruppe verwenden, oder verwenden Sie den Eintrag, der von der Befehlsvorlage wie im folgenden Beispiel bereitgestellt wird. Diese Gruppe wird angezeigt, auf die **Tools** Menü  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>Um eine Gruppe von Schaltflächen für die Wiederverwendung zu erstellen.  
  
1.  Sie können einen Befehl oder ein Menü in einer Gruppe mithilfe der Gruppe als übergeordnetes Element in der Definition der Befehl oder im Menü, oder indem Sie den Befehl oder das Menü in der Gruppe mithilfe des Abschnitts CommandPlacements einfügen einfügen.  
  
     Klicken Sie im Abschnitt Schaltflächen definieren Sie eine Schaltfläche mit Ihrer Gruppe als übergeordnete Klasse, oder verwenden Sie die Schaltfläche, die von der Paketvorlage bereitgestellt wird, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2.  Wenn eine Schaltfläche in mehr als einer Gruppe angezeigt werden muss, erstellen Sie einen Eintrag für sie im Abschnitt CommandPlacements, die nach dem Abschnitt Befehle platziert werden muss. Die GUID und ID-Attribute des CommandPlacement-Element, mit denen der Schaltfläche übereinstimmen, die Sie positionieren möchten, und legen Sie dann die GUID und ID des übergeordneten Elements, die von der Zielgruppe und wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  Der Wert des Felds Priorität bestimmt die Position des Befehls in der neuen Befehlsgruppe. Legen Sie Prioritäten in der CommandPlacement-Element überschreiben diejenigen in der Elementdefinition. Befehle, die niedrigere Prioritätswerte haben, werden vor Befehlen angezeigt, die höhere Prioritätswerte haben. Doppelte Prioritätswerte sind zulässig, aber die relativen Positionen von Befehlen, die den gleichen Prioritätswert kann nicht garantiert werden, da die Reihenfolge, in der **Devenv/Setup** Befehl wird die endgültige Benutzeroberfläche aus der Registrierung erstellt. unter Umständen nicht konsistent sein.  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Stellen Sie eine wiederverwendbare Gruppe von Schaltflächen in einem Menü  
  
1.  Erstellen Sie einen Eintrag in der `CommandPlacements` Abschnitt. Legen Sie die GUID und ID der `CommandPlacement` Element, mit denen Ihre Gruppe, und legen Sie das übergeordnete Element GUID und ID, die von den Zielspeicherort an.  
  
     Der CommandPlacements-Abschnitt sollte unmittelbar nach dem Abschnitt "Befehle" eingefügt werden:  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     Eine Befehlsgruppe kann mehr als ein Menü eingefügt werden. Klicken Sie im übergeordneten Menü kann eine, die Sie erstellt haben, eine, die vom bereitgestellt wird [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (wie beschrieben in ShellCmdDef.vsct oder SharedCmdDef.vsct), oder eine, die in einem anderen VSPackage definiert ist. Die Anzahl der übergeordneter Ebenen ist unbegrenzt, so lange im übergeordneten Menü schließlich verbunden ist [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oder in einem Kontextmenü Menüelemente, die von einem VSPackage angezeigt wird.  
  
     In diesem Beispiel werden die Gruppe auf die **Projektmappen-Explorer** Symbolleiste rechts neben die anderen Schaltflächen.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">  
          <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements>  
      <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"   
          priority="0x605">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />  
      </CommandPlacement>  
    </CommandPlacements>  
  
    ```
