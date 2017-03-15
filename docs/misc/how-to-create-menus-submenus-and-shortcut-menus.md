---
title: "Gewusst wie: Erstellen von Men&#252;s, Untermen&#252;s und Kontextmen&#252;s | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehlsleisten, Architektur"
  - "Menüs, erstellen"
  - "Menüs, Architektur"
  - "Befehle, Menüs"
  - "Menüs"
ms.assetid: 62004fd9-7f99-4f00-8d01-1dde53e23dbb
caps.latest.revision: 46
caps.handback.revision: 46
manager: "douge"
---
# Gewusst wie: Erstellen von Men&#252;s, Untermen&#252;s und Kontextmen&#252;s
Ein VSPackage muss die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]\-Architektur für Befehlsgruppenmenüs verwenden, um ein Menü zur integrierten Entwicklungsumgebung \(Integrated Development Environment, IDE\) von Visual Studio hinzuzufügen. Ein Befehlsgruppenmenü ermöglicht die Freigabe von Befehlen nach Komponenten und der integrierten Entwicklungsumgebung. Weitere Informationen zu Befehlsgruppenmenüs finden Sie unter [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 In VSPackages sind Menüs im Abschnitt [Menüs](../extensibility/menus-element.md) einer VSCT\-Datei definiert. In einer VSCT\-Datei sind Menüs, Symbolleisten, Gruppen und Befehle definiert. Ein Benutzer klickt auf einen Befehl, um eine Funktion auszuführen. Eine Gruppe ist ein Container für Befehle. Ein Menü ist ein Container für Gruppen. Zum Erstellen eines einfachen Menüs müssen Sie ein Menü, eine Befehlsgruppe und mindestens einen Befehl erstellen.  
  
 Es gibt drei grundlegende Arten, wie ein Menü in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] angezeigt werden kann:  
  
-   Als Menü in der Hauptmenüleiste.  
  
-   Als Untermenü eines anderen Menüs.  
  
-   Als Kontextmenü \(in der Regel durch Klicken mit der rechten Maustaste angezeigt\).  
  
 In diesem Thema wird die Erstellung der einzelnen Menüarten veranschaulicht. Die folgenden exemplarischen Vorgehensweisen zeigen ebenfalls die erforderlichen Schritte:  
  
-   [Der Visual Studio\-Menüleiste hinzufügen ein Menü](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
  
-   [Hinzufügen eines Untermenüs zu einem Menü](../extensibility/adding-a-submenu-to-a-menu.md)  
  
-   [Hinzufügen eines Kontextmenüs in einem Toolfenster](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)  
  
### So erstellen Sie ein Menü, ein Untermenü oder ein Kontextmenü  
  
1.  Doppelklicken Sie in Ihrem Projekt auf die VSCT\-Datei, um Sie im Editor zu öffnen.  
  
     Wenn in Ihrem Projekt keine VSCT\-Datei vorhanden ist, fügen Sie eine hinzu. Wenn Sie mithilfe der Visual Studio\-Paketvorlage ein Paket erstellen, wählen Sie **Menübefehl** aus. Auf diese Weise wird eine VSCT\-Datei generiert.  
  
2.  Suchen Sie im `Symbols`\-Abschnitt nach dem [GuidSymbol](../extensibility/guidsymbol-element.md)\-Element, das die Gruppen und Befehle enthält.  
  
3.  Erstellen Sie ein [IDSymbol](../extensibility/idsymbol-element.md)\-Element für jedes Menü, jede Gruppe oder jeden Befehlen, das, die oder den Sie hinzufügen möchten \(siehe folgendes Beispiel\).  
  
     [!CODE [ButtonGroup#01](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#01)]  
  
     Die `name`\-Attribute des `GuidSymbol`\- und des `IDSymbol`\-Elements stellen das GUID:ID\-Paar für jedes neue Menü, jede neue Gruppe oder jeden neuen Befehl bereit. Die `GUID` entspricht einem Befehlssatz, der für Ihr VSPackage definiert ist. Sie können mehrere Befehlssätze definieren. Jedes GUID:ID\-Paar muss eindeutig sein.  
  
4.  Definieren Sie das neue Menü wie folgt im Abschnitt `Menus`:  
  
    1.  Legen Sie die Felder `guid` und `id` so fest, dass sie dem GUID:ID\-Paar des neuen Menüs entsprechen.  
  
    2.  Legen Sie das `priority`\-Attribut fest.  
  
         Das `priority`\-Attribut wird von der VSCT\-Datei dazu verwendet, die Position des Menüs zwischen den anderen Objekten in der übergeordneten Gruppe zu bestimmen.  
  
         Menüs, die niedrigere Prioritätswerte haben, werden vor Menüs angezeigt, die über höhere Prioritätswerte verfügen. Doppelte Prioritätswerte sind zulässig, aber die relativen Positionen von Menüs, die dieselbe Priorität haben, werden durch die Reihenfolge bestimmt, in der VSPackages zur Laufzeit verarbeitet werden, und diese Reihenfolge kann nicht vorherbestimmt werden. Ist das `priority`\-Attribut nicht angegeben, wird sein Wert auf 0 festgelegt.  
  
         Legen Sie keine Priorität für ein Kontextmenü fest, da dessen Position durch den Code bestimmt wird, der es aufruft.  
  
    3.  Legen Sie für Menüs und Untermenüs das `type`\-Attribut auf `Menu` fest, wodurch ein typisches Menü beschrieben wird. Legen Sie für Kontextmenüs das `type`\-Attribut auf `Context` fest.  
  
         Beschreibungen zu anderen gültigen Menütypen wie Symbolleisten und Menücontroller finden Sie unter [Menu\-Element](../extensibility/menu-element.md).  
  
    4.  Erstellen Sie in der Menüdefinition einen [Strings](../extensibility/strings-element.md)\-Abschnitt, der Folgendes enthält: ein [ButtonText](../extensibility/buttontext-element.md)\-Element, in dem sich der Name des Menüs so befindet, wie er in der IDE angezeigt wird, sowie ein [CommandName](../extensibility/commandname-element.md)\-Element, in dem sich der Name des Befehls befindet, über den im Fenster **Befehl** auf das Menü zugegriffen wird.  
  
         Enthält die Schaltflächenzeichenfolge das Zeichen „&“, kann das Menü geöffnet werden, indem ALT sowie das Zeichen gedrückt werden, das unmittelbar auf „&“ folgt.  
  
    5.  Fügen Sie nach Bedarf Befehlsflags hinzu, um das Aussehen und Verhalten des Menüs zu ändern. Fügen Sie zu diesem Zweck ein [CommandFlag](../extensibility/command-flag-element.md)\-Element in der Menüdefinition hinzu. Weitere Informationen finden Sie unter [Command\-Flag\-Element](../extensibility/command-flag-element.md).  
  
5.  Legen Sie das übergeordnete Objekt des Menüs fest. Verwenden Sie für ein Standard\- oder Untermenü in Abhängigkeit vom Entwurf eine der folgenden Methoden:  
  
    -   Erstellen Sie im `Menu`\-Element ein [Parent](../extensibility/parent-element.md)\-Element, und legen Sie dessen Felder `guid` und `id` auf das GUID:ID\-Paar der Gruppe fest, in der das Menü gehostet wird. Diese Gruppe wird auch als die *primäre übergeordnete Gruppe* bezeichnet. Die übergeordnete Gruppe kann eine Gruppe, die Sie im Abschnitt `Symbols` erstellt haben, eine Gruppe aus einem anderen Paket oder eine Gruppe aus der IDE sein. Legen Sie z. B. zum Hinzufügen Ihres Menüs zur Menüleiste der obersten Ebene der IDE für das übergeordnete Objekt neben dem Menü **Extras** den Wert „guidSHLMainMenu:IDG\_VS\_MM\_TOOLSADDINS“ fest.  
  
         Das folgende Beispiel zeigt ein Menü, das in der Visual Studio\-Menüleiste angezeigt wird.  
  
         [!CODE [TopLevelMenu#01](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#01)]  
  
    -   Sie können auf das `Parent`\-Element verzichten, wenn das Menü durch Befehlsplatzierung positioniert wird. Erstellen Sie einen [CommandPlacements](../extensibility/commandplacements-element.md)\-Abschnitt vor dem `Symbols`\-Abschnitt, und fügen Sie ein [CommandPlacement](../extensibility/commandplacement-element.md)\-Element hinzu, das das GUID:ID\-Paar des Menüs, eine Priorität und ein übergeordnetes Element aufweist, wie im folgenden Beispiel gezeigt.  
  
         [!CODE [ButtonGroup#04](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#04)]  
  
         Werden mehrere Befehlsplatzierungen erstellt, die dasselbe GUID:ID\-Paar und verschiedene übergeordnete Elemente aufweisen, wird ein Menü an mehreren Positionen angezeigt. Weitere Informationen finden Sie unter [CommandPlacements\-Element](../extensibility/commandplacements-element.md).  
  
     Ein Standardmenü muss über eine Gruppe in der Visual Studio\-Menüleiste als übergeordnetes Element verfügen. Für ein Untermenü muss das übergeordnete Element eine Gruppe in einem anderen Menü sein \(oder auf einer Symbolleiste bzw. einem anderen Menütyp\). Damit ein Menü oder Untermenü angezeigt wird, muss es eine Gruppe hosten, die mindestens einen aktiven Befehl enthält oder für die das `AlwaysCreate`\-Befehlsflag festgelegt ist.  
  
     Kontextmenüs besitzen keine übergeordneten Elemente oder Befehlsplatzierungen. Stattdessen müssen sie im Code aktiviert werden. In der Regel wird ein Kontextmenü als Antwort auf das Klicken mit der rechten Maustaste auf eine Steuerelementoberfläche aktiviert. Im folgenden Beispiel wird ein Kontextmenü definiert.  
  
     [!CODE [ButtonGroup#06](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#06)]  
  
6.  Erstellen Sie im [Groups](../extensibility/groups-element.md)\-Abschnitt ein [Group](../extensibility/group-element.md)\-Element, das die im Menü anzuzeigenden Befehle enthalten soll. Der `Symbols`\-Abschnitt muss einen Eintrag enthalten, der dasselbe GUID:ID\-Paar wie das neue `Group`\-Element aufweist.  
  
    1.  Legen Sie die Priorität der Gruppe so fest, dass sie im Menü an der gewünschten Position angezeigt wird.  
  
         Die Grenzen der einzelnen Gruppen im Menü werden als horizontale Linien angezeigt.  
  
    2.  Legen Sie für das übergeordnete Element dieser neuen Gruppe auf das GUID:ID\-Paar des von Ihnen erstellten Menüs fest. Auf diese Weise wird die Gruppe von Befehlen zum Menü hinzugefügt.  
  
     Die Gruppe im folgenden Beispiel wird im Menü der obersten Ebene angezeigt, das in einem vorherigen Beispiel veranschaulicht wurde.  
  
     [!CODE [TopLevelMenu#02](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#02)]  
  
     Menüs können sowohl Befehle als auch Untermenüs enthalten. Ein Untermenü \(auch als hierarchisches Menü bezeichnet\) ist nur ein Menü, jedoch handelt es sich um ein Menü, das zur Gruppe eines anderen Menüs hinzugefügt und nur dann verfügbar gemacht wird, wenn das andere Menü aufgerufen wurde. Indem das im folgenden Beispiel gezeigte Menü zu einer Gruppe des Menüs der obersten Ebene hinzugefügt wird, wird es zu einem Untermenü.  
  
     [!CODE [TopLevelMenu#06](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#06)]  
  
7.  Erstellen Sie Befehlseinträge im [Buttons](../extensibility/buttons-element.md)\-Abschnitt, und legen Sie für das übergeordnete Element der einzelnen Einträge das GUID:ID\-Paar Ihrer Gruppe fest. Jedes [Button](../extensibility/button-element.md)\-Element erfordert ein GUID:ID\-Paar, das einem Eintrag im `Symbols`\-Abschnitt entspricht.  
  
     Verwenden Sie das `priority`\-Attribut der einzelnen Schaltflächeneinträge, um die Reihenfolge anzugeben, in der die Befehle in der Gruppe angezeigt werden.  
  
     Im folgenden Beispiel wird ein Befehl definiert, der im Menü der obersten Ebene angezeigt wird.  
  
     [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
     Weitere Informationen zu Schaltflächen und Menüelementen finden Sie unter [Button\-Element](../extensibility/button-element.md).  
  
     Informationen zum Implementieren von Menübefehlen im Code finden Sie unter [MenuCommand\- und OleMenuCommand\-Objekte](../misc/menucommands-vs-olemenucommands.md) oder in den exemplarischen Vorgehensweisen, die weiter oben in diesem Thema erwähnt wurden.  
  
### So aktivieren Sie ein Kontextmenü  
  
1.  Rufen Sie das GUID:ID\-Paar des Kontextmenüs ab. Standardmäßig erstellt die Paketvorlage eine `GuidList`\-Klasse in einer „PkgCmdID.cs“\-Datei, um die GUID für den Befehlssatz aufzunehmen. Außerdem wird von der Vorlage eine `PkgCmdIdList`\-Klasse in einer „PkgCmdId.cs“\-Datei erstellt, um die ganzzahligen ID\-Werte von Befehlen aufzunehmen, die in der Vorlage deklariert werden. Die Kontextmenüs sowie alle weiteren Befehle müssen nach der Fertigstellung der Vorlage deklariert werden. Diese Deklarationen werden im folgenden Beispiel veranschaulicht.  
  
     [!code-cs[TWShortcutMenu#12](../misc/codesnippet/CSharp/how-to-create-menus-submenus-and-shortcut-menus_8.cs)]  
  
     Dieser Schritt kann ausgelassen werden, wenn die GUID\- und ID\-Werte direkt verwendet werden. Es wird jedoch empfohlen, dass Sie die Werte zur besseren Lesbarkeit hier festlegen.  
  
2.  Dann erfolgt das Anfügen an einen Ereignishandler. In der Regel wird ein Kontextmenü an das Klicken mit der rechten Maustaste auf eine Steuerelementoberfläche angefügt, wie im folgenden Beispiel veranschaulicht.  
  
     [!code-cs[TWShortcutMenu#43](../misc/codesnippet/CSharp/how-to-create-menus-submenus-and-shortcut-menus_9.cs)]  
  
     Die <xref:System.Windows.Forms.Control.PointToScreen%2A>\-Methode konvertiert die Position des Mausklicks, die relativ zum Steuerelement angegeben wird, in eine Bildschirmposition. Die <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A>\-Methode zeigt das Kontextmenü an.  
  
     Die Datei, die den Ereignishandler enthält, muss den <xref:System.ComponentModel.Design>\-Namespace für den Zugriff auf die <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>\-Klasse und den <xref:Microsoft.VisualStudio.Shell>\-Namespace für den Zugriff auf die <xref:System.ComponentModel.Design.IMenuCommandService>\-Schnittstelle einbeziehen.  
  
     [!code-cs[TWShortcutMenu#41](../misc/codesnippet/CSharp/how-to-create-menus-submenus-and-shortcut-menus_10.cs)]  
  
## Siehe auch  
 [MenuCommand\- und OleMenuCommand\-Objekte](../misc/menucommands-vs-olemenucommands.md)   
 [VSCT XML\-Schemareferenz](../extensibility/vsct-xml-schema-reference.md)   
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)