---
title: "Erstellen von wieder verwendbaren Gruppen von Schaltfl&#228;chen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Schaltflächengruppen, die in VSPackages erstellen"
  - "VSPackages, wieder verwendbaren Schaltflächengruppen erstellen"
  - "Schaltflächen wieder verwendbare Gruppen erstellen"
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: 44
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 44
---
# Erstellen von wieder verwendbaren Gruppen von Schaltfl&#228;chen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine Befehlsgruppe ist eine Auflistung von Befehlen, die immer zusammen in einem Menü oder Symbolleiste angezeigt werden. Alle Befehlsgruppe kann erneut verwendet werden, von anderen übergeordneten Menüs im Abschnitt CommandPlacements der VSCT\-Datei zuweisen.  
  
 Befehlsgruppen Schaltflächen in der Regel enthalten, aber sie können auch andere Menüs oder Kombinationsfelder enthalten.  
  
### Erstellen Sie eine wieder verwendbare Gruppe von Schaltflächen  
  
1.  Erstellen Sie ein VSIX\-Projekt namens `ReusableButtons`. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie eine benutzerdefinierten Befehl Elementvorlage mit dem Namen **ReusableCommand**. In der **Projektmappen\-Explorer**, mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen \/ neues Element**. In der **Neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c\# \/ Erweiterbarkeit** und wählen Sie **Befehl benutzerdefinierte**. In den **Namen** Feld am unteren Rand des Fensters, das Ändern der Name der Befehlsdatei an **ReusableCommand.cs**.  
  
3.  Finden Sie in der VSCT\-Datei im Abschnitt Symbole, und suchen Sie das GuidSymbol\-Element, das Gruppen und Befehle für das Projekt enthält. Es sollten GuidReusableCommandPackageCmdSet benannt werden.  
  
4.  Fügen Sie eine IDSymbol für die einzelnen Schaltflächen, die Sie der Gruppe, wie im folgenden Beispiel hinzufügen.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}"> <IDSymbol name="MyMenuGroup" value="0x1020" /> <IDSymbol name="ReusableCommandId" value="0x0100" /> <IDSymbol name="SecondReusableCommandId" value="0x0200" /> </GuidSymbol>  
    ```  
  
     Die Befehl Elementvorlage erstellt standardmäßig eine Gruppe namens **MyGroup** und eine Schaltfläche mit dem Namen, den Sie angegeben haben, zusammen mit einem IDSymbol\-Eintrag für jede.  
  
5.  Erstellen Sie im Abschnitt Gruppen ein Group\-Element, das die gleichen GUID und ID\-Attribute wie diejenigen, die im Abschnitt Symbole angegeben wurde. Sie können auch eine vorhandene Gruppe verwenden oder verwenden Sie den Eintrag, der durch die Befehlsvorlage, wie im folgenden Beispiel bereitgestellt wird. Diese Gruppe wird auf der **Tools** Menü  
  
    ```xml  
    <Groups> <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600"> <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/> </Group> </Groups>  
    ```  
  
### Zum Erstellen einer Gruppe von Schaltflächen für die Wiederverwendung  
  
1.  Sie können einen Befehl oder ein Menü in einer Gruppe mithilfe der Gruppe als übergeordnetes Element in der Definition des Befehls oder des Menü oder indem der Befehl oder im Menü in der Gruppe mithilfe des Abschnitts CommandPlacements anordnen.  
  
     Definieren Sie im Abschnitt Schaltflächen eine Schaltfläche, die die Gruppe als übergeordnetes Element verfügt, oder verwenden Sie die Schaltfläche, die von der Paketvorlage bereitgestellt wird, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button"> <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" /> <Icon guid="guidImages" id="bmpPic1" /> <Strings> <ButtonText>Invoke ReusableCommand</ButtonText> </Strings> </Button>  
    ```  
  
2.  Wenn eine Schaltfläche in mehr als einer Gruppe angezeigt werden muss, erstellen Sie einen Eintrag für sie im Abschnitt CommandPlacements, die nach dem Abschnitt Befehle platziert werden muss. Legen Sie die GUID und ID\-Attribute des Elements CommandPlacement auf die Schaltfläche übereinstimmen, die Sie positionieren möchten, und legen Sie dann die GUID und ID des übergeordneten Elements mit denen der Zielgruppe, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105"> <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" /> </CommandPlacement> </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  Der Wert des Felds Priorität bestimmt die Position des Befehls in die neue Befehlsgruppe. Prioritäten, die in das Element zu überschreiben, die in der Elementdefinition CommandPlacement festgelegt werden. Befehle mit niedriger Prioritätswerte werden vor Befehlen angezeigt, die höhere Prioritätswerte aufweisen. Doppelte Priority\-Werte sind zulässig, jedoch die relative Position der Befehle, die denselben Prioritätswert aufweisen kann nicht garantiert werden, da die Reihenfolge, in der die **devenv \/setup** Befehl erstellt die endgültige Benutzeroberfläche aus der Registrierung möglicherweise nicht konsistent.  
  
### Stellen Sie eine wieder verwendbare Gruppe von Schaltflächen in einem Menü  
  
1.  Erstellen Sie einen Eintrag in der `CommandPlacements` Abschnitt. Legen Sie die GUID und ID des dem `CommandPlacement` Element der Gruppe, und legen Sie die übergeordnete GUID und ID, die der Zieladresse.  
  
     Abschnitt CommandPlacements sollte unmittelbar nach dem Abschnitt "Befehle" platziert werden:  
  
    ```xml  
    <CommandTable> ... <Commands>... </Commands> <CommandPlacements>... </CommandPlacements> ... </CommandTable>  
    ```  
  
     Eine Befehlsgruppe kann auf mehr als einem Menü enthalten sein. Im übergeordneten Menü kann eine die erstellt, die vom bereitgestellte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(wie beschrieben in ShellCmdDef.vsct oder SharedCmdDef.vsct\), oder in einem anderen VSPackage definiert ist. Die Anzahl der Ebenen Überordnung unbegrenzt ist, als im übergeordneten Menü schließlich verbunden ist [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder in einem Kontextmenü, das durch ein VSPackage angezeigt wird.  
  
     Im folgenden Beispiel wird die Gruppe auf die **Projektmappen\-Explorer** Symbolleiste rechts neben den anderen Schaltflächen.  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/> </CommandPlacement> </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup" priority="0x605"> <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" /> </CommandPlacement> </CommandPlacements>  
  
    ```