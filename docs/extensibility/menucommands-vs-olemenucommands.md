---
title: MenuCommand- und OleMenuCommands | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: 
manager: douge
ms.openlocfilehash: 144410e0e9b5b8d5d40fee86a1573bd179aea44a
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="menucommands-vs-olemenucommands"></a>MenuCommand- und OleMenuCommand-Objekte
Sie können Menübefehle erstellen, indem Sie entweder aus dem <xref:System.ComponentModel.Design.MenuCommand> - oder aus dem <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Objekt ableiten und die entsprechenden Ereignishandler implementieren. In den meisten Fällen können Sie <xref:System.ComponentModel.Design.MenuCommand>verwenden, wie dies in der VSPackage-Projektvorlage geschieht, gelegentlich müssen Sie aber möglicherweise <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>verwenden.  
  
 Die Befehle, die ein VSPackage für die IDE verfügbar macht, müssen sichtbar und aktiviert sein, damit ein Benutzer sie verwenden kann. Wenn Befehle in einer VSCT-Datei erstellt werden, indem die Visual Studio-Paket-Projektvorlage verwendet wird, sind sie standardmäßig sichtbar und aktiviert. Durch Festlegen einiger Befehlsflags, z. B. `DynamicItemStart`, kann das Standardverhalten geändert werden. Die Sichtbarkeit, der Aktivierungsstatus und andere Eigenschaften eines Befehls können im Code auch zur Laufzeit geändert werden, indem auf das <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Objekt zugegriffen wird, das dem Befehl zugeordnet ist.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Speicherorte für die Visual Studio-Paket-Vorlage  
 Sie finden die Visual Studio-Paket-Vorlage im Dialogfeld **Neues Projekt** unter **Visual Basic / Erweiterungen**, **C# / Erweiterungen**oder **Andere Projekttypen / Erweiterungen**.  
  
## <a name="creating-a-command"></a>Erstellen eines Befehls  
 Alle Befehle, Befehlsgruppen, Menüs, Symbolleisten und Toolfenster sind in der VSCT-Datei definiert. Weitere Informationen finden Sie unter [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Wenn Sie ein VSPackage mit der Paketvorlage erstellen, wählen Sie **Menübefehl** aus, um eine VSCT-Datei zu erstellen und einen Standardmenübefehl festzulegen. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-add-a-command-to-the-ide"></a>So fügen Sie der IDE einen Befehl hinzu  
  
1.  Öffnen Sie die VSCT-Datei.  
  
2.  Suchen Sie im `Symbols` -Abschnitt nach dem [GuidSymbol](../extensibility/guidsymbol-element.md) -Element, das die Gruppen und Befehle enthält.  
  
3.  Erstellen Sie ein [IDSymbol](../extensibility/idsymbol-element.md) -Element für jedes Menü, jede Gruppe oder jeden Befehl, das, die oder den Sie hinzufügen möchten (siehe folgendes Beispiel).  
  
     <!--FIXME [!CODE [ButtonGroup#01](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#01)]  -->
    ```xaml  
    <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
      <IDSymbol name="MyMenuGroup" value="0x1020" />
      <IDSymbol name="cmdidMyCommand" value="0x0100" />
    </GuidSymbol>
    ```  
  
    Die `name` -Attribute des `GuidSymbol` - und des `IDSymbol` -Elements stellen das GUID:ID-Paar für jedes neue Menü, jede neue Gruppe oder jeden neuen Befehl bereit. Die `guid` entspricht einem Befehlssatz, der für Ihr VSPackage definiert ist. Sie können mehrere Befehlssätze definieren. Jedes GUID:ID-Paar muss eindeutig sein.  
  
4.  Erstellen Sie im [Buttons](../extensibility/buttons-element.md) -Abschnitt ein [Button](../extensibility/button-element.md) -Element, um den Befehl zu definieren (siehe folgendes Beispiel).  
  
     <!--FIXME [!CODE [ButtonGroup#03](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#03)]  -->
    ```xaml  
    <Button guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```  
  
    1.  Legen Sie die Felder `guid` und `id` so fest, dass sie dem GUID:ID-Paar des neuen Befehls entsprechen.  
  
    2.  Legen Sie das `priority` -Attribut fest.  
  
         Das `priority` -Attribut wird von der VSCT-Datei dazu verwendet, die Position der Schaltfläche zwischen den anderen Objekten in ihrer übergeordneten Gruppe zu bestimmen.  
  
         Befehle, die niedrigere Prioritätswerte haben, werden über oder links von Befehlen angezeigt, die höhere Prioritätswerte haben. Doppelte Prioritätswerte sind zulässig, aber die relativen Positionen von Befehlen, die dieselbe Priorität haben, werden durch die Reihenfolge bestimmt, in der VSPackages zur Laufzeit verarbeitet werden, und diese Reihenfolge kann nicht vorherbestimmt werden.  
  
         Ist das `priority` -Attribut nicht angegeben, wird sein Wert auf 0 festgelegt.  
  
    3.  Legen Sie das `type` -Attribut fest. In den meisten Fällen hat es den Wert `"Button"`. Beschreibungen von anderen gültigen Schaltflächentypen finden Sie unter [Button Element](../extensibility/button-element.md).  
  
5.  Erstellen Sie in der Schaltflächendefinition ein [Strings](../extensibility/strings-element.md) -Element, das Folgendes enthält: ein [ButtonText](../extensibility/buttontext-element.md) -Element, in dem sich der Name des Menüs so befindet, wie er in der IDE angezeigt wird, sowie ein [CommandName](../extensibility/commandname-element.md) -Element, in dem sich der Name des Befehls befindet, über den im Fenster **Befehl** auf das Menü zugegriffen wird.  
  
     Enthält die Schaltflächenzeichenfolge das Zeichen „&“, kann das Menü geöffnet werden, indem ALT sowie das Zeichen gedrückt werden, das unmittelbar auf „&“ folgt.  
  
     Wird ein `Tooltip` -Element hinzugefügt, wird der darin enthaltene Text angezeigt, wenn mit dem Mauszeiger auf die Schaltfläche gezeigt wird.  
  
6.  Fügen Sie ein [Icon](../extensibility/icon-element.md) -Element hinzu, um das Symbol anzugeben, das mit dem Befehl angezeigt werden soll. Symbole sind für Schaltflächen in Symbolleisten, jedoch nicht für Menüelemente erforderlich. Die `guid` und die `id` des `Icon` -Elements müssen mit denjenigen eines [Bitmap](../extensibility/bitmap-element.md) -Elements übereinstimmen, das im `Bitmaps` -Abschnitt definiert ist.  
  
7.  Fügen Sie nach Bedarf Befehlsflags hinzu, um das Aussehen und Verhalten der Schaltfläche zu ändern. Fügen Sie zu diesem Zweck ein [CommandFlag](../extensibility/command-flag-element.md) -Element in der Menüdefinition hinzu.  
  
8.  Legen Sie die übergeordnete Gruppe des Befehls fest. Die übergeordnete Gruppe kann Folgendes sein: eine Gruppe, die Sie erstellen, eine Gruppe aus einem anderen Paket oder eine Gruppe aus der IDE. Soll der Befehl beispielsweise zur Visual Studio-Bearbeitungssymbolleiste neben den Schaltflächen **Kommentar** und **Kommentare entfernen** hinzugefügt werden, legen Sie das übergeordnete Element auf „guidStdEditor:IDG_VS_EDITTOOLBAR_COMMENT“ fest. Ist die übergeordnete Gruppe eine benutzerdefinierte Gruppe, muss sie untergeordnetes Element eines Menüs, einer Symbolleiste oder eines Toolfensters sein, die oder das in der IDE angezeigt wird.  
  
     Sie erreichen dies, abhängig von Ihrem Entwurf, durch eine von zwei Möglichkeiten:  
  
    -   Erstellen Sie im `Button` -Element ein [Parent](../extensibility/parent-element.md) -Element, und legen Sie dessen Felder `guid` und `id` auf die Guid und die ID der Gruppe fest, in der der Befehl gehostet wird. Diese Gruppe wird auch als die *primäre übergeordnete Gruppe*bezeichnet.  
  
         Im folgenden Beispiel wird ein Befehl definiert, der in einem benutzerdefinierten Menü angezeigt wird.  
  
         <!--FIXME [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  -->
        ```xaml  
        <Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
          <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
          <Icon guid="guidImages" id="bmpPic1" />
          <Strings>
            <CommandName>cmdidTestCommand</CommandName>
            <ButtonText>Test Command</ButtonText>
          </Strings>
        </Button>
        ```  
  
    -   Sie können auf das `Parent` -Element verzichten, wenn der Befehl durch Befehlsplatzierung positioniert wird. Erstellen Sie ein [CommandPlacements](../extensibility/commandplacements-element.md) -Element vor dem `Symbols` -Abschnitt, und fügen Sie ein [CommandPlacement](../extensibility/commandplacement-element.md) -Element hinzu, das die `guid` und die `id` des Befehls, einen `priority`-Wert und ein übergeordnetes Element hat (siehe folgendes Beispiel).  
  
         <!-- FIXME [!CODE [ButtonGroup#04](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#04)] -->  
        ```xaml  
        <CommandPlacements>
          <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
            <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
          </CommandPlacement>
        </CommandPlacements>
        ```  
  
         Werden mehrere Befehlsplatzierungen erstellt, die dasselbe GUID:ID-Paar und verschiedene übergeordnete Elemente haben, wird ein Menü an mehreren Positionen angezeigt. Weitere Informationen finden Sie in der Beschreibung des [CommandPlacements](../extensibility/commandplacements-element.md) -Elements.  
  
     Weitere Informationen zu Befehlsgruppen und Überordnung finden Sie unter [erstellen Wiederverwendbarer Gruppen von Schaltflächen](../extensibility/creating-reusable-groups-of-buttons.md).  
  
 An diesem Punkt ist der Befehl in der IDE sichtbar, hat aber noch keine Funktionalität. Wurde der Befehl über die Paketvorlage erstellt, hat er standardmäßig einen Click-Handler, der eine Meldung angezeigt.  
  
## <a name="handling-the-new-command"></a>Behandeln des neuen Befehls  
 Die meisten Befehle in verwaltetem Code können durch das Managed Package Framework (MPF) behandelt werden, indem der Befehl einem <xref:System.ComponentModel.Design.MenuCommand> -Objekt oder einem <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Objekt zugeordnet und dessen Ereignishandler implementiert werden.  
  
 Für Code, in dem die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle direkt zur Befehlsbehandelung verwendet wird, müssen Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle und deren Methoden implementieren. Die beiden wichtigsten Methoden sind <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> und <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>.  
  
1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> -Instanz ab, wie im folgenden Beispiel gezeigt.  
  
     [!code-csharp[ButtonGroup#21](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_5.cs)]  
  
2.  Erstellen Sie ein <xref:System.ComponentModel.Design.CommandID> -Objekt, dessen Parameter aus der GUID und der ID des zu behandelnden Befehls bestehen (siehe folgendes Beispiel).  
  
     [!code-csharp[ButtonGroup#22](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_6.cs)]  
  
     Die Visual Studio-Paket-Vorlage stellt zwei Sammlungen, `GuidList` und `PkgCmdIDList`, bereit, um die GUIDs und IDs von Befehlen zu speichern. Diese Sammlungen werden automatisch für Befehle aufgefüllt, die über die Vorlage hinzugefügt werden, aber für Befehle, die Sie manuell hinzufügen, müssen Sie auch den ID-Eintrag zur `PkgCmdIdList` -Klasse hinzufügen.  
  
     Alternativ können Sie das <xref:System.ComponentModel.Design.CommandID> -Objekt auffüllen, indem Sie den unformatierten Zeichenfolgenwert der GUID und den Integer-Wert der ID verwenden.  
  
3.  Instanziieren Sie entweder ein <xref:System.ComponentModel.Design.MenuCommand> - oder ein <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Objekt, das die Methode, die den Befehl behandelt, zusammen mit der <xref:System.ComponentModel.Design.CommandID>angibt (siehe folgendes Beispiel).  
  
     [!code-csharp[ButtonGroup#23](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_7.cs)]  
  
     Das <xref:System.ComponentModel.Design.MenuCommand> -Objekt ist für statische Befehle geeignet. Dynamisches Anzeigen von Menüelementen erfordert QueryStatus-Ereignishandler. Das <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Objekt fügt das <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> -Ereignis, das auftritt, wenn das Hostmenü des Befehls geöffnet wird, sowie einige andere Eigenschaften hinzu, z. B. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Befehle, die durch die Paketvorlage erstellt wurden, werden standardmäßig an ein <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Objekt in der `Initialize()` -Methode der Paketklasse übergeben.  
  
4.  Das <xref:System.ComponentModel.Design.MenuCommand> -Objekt ist für statische Befehle geeignet. Dynamisches Anzeigen von Menüelementen erfordert QueryStatus-Ereignishandler. Das <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Objekt fügt das <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> -Ereignis, das auftritt, wenn das Hostmenü des Befehls geöffnet wird, sowie einige andere Eigenschaften hinzu, z. B. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Befehle, die durch die Paketvorlage erstellt wurden, werden standardmäßig an ein <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Objekt in der `Initialize()` -Methode der Paketklasse übergeben. Der Visual Studio-Assistent implementiert die `Initialize` -Methode durch Verwenden von `MenuCommand`. Für ein dynamisches Anzeigen von Menüelementen müssen Sie dies in `OleMenuCommand`ändern, wie im nächsten Schritt gezeigt. Außerdem müssen Sie, um den Menüelementtext zu ändern, der Schaltfläche des Menübefehls in der VSCT-Datei ein TextChanges-Befehlsflag hinzufügen (siehe folgendes Beispiel).  
  
     <!--FIXME [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]-->  
    ```xaml  
    <Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <CommandFlag>TextChanges</CommandFlag>
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```
  
5.  Übergeben Sie den neuen Menübefehl an die <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> -Methode in der <xref:System.ComponentModel.Design.IMenuCommandService> -Schnittstelle. Für Befehle, die durch die Paketvorlage erstellt wurden, wird dies standardmäßig erledigt, wie im folgenden Beispiel gezeigt.  
  
     [!code-csharp[ButtonGroup#24](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_9.cs)]  
  
6.  Implementieren Sie die Methode, die den Befehl behandelt.  
  
#### <a name="to-implement-querystatus"></a>So implementieren Sie „QueryStatus“  
  
1.  Das QueryStatus-Ereignis tritt auf, bevor ein Befehl angezeigt wird. Dadurch wird es möglich, Eigenschaften dieses Befehls im Ereignishandler festzulegen, bevor der Befehl den Benutzer erreicht. Nur Befehle, die als <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Objekte hinzugefügt werden, können auf diese Methode zugreifen.  
  
     Fügen Sie ein `EventHandler` -Objekt zum <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> -Ereignis im <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Objekt hinzu, das erstellt wird, um den Befehl zu behandeln, wie im folgenden Beispiel gezeigt (`menuItem` ist die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Instanz).  
  
     [!code-csharp[MenuText#14](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_10.cs)]
     [!code-vb[MenuText#14](../extensibility/codesnippet/VisualBasic/menucommands-vs-olemenucommands_10.vb)]  
  
     Dem `EventHandler` -Objekt wird der Name einer Methode übergeben, die aufgerufen wird, wenn der Status des Menübefehls abgefragt wird.  
  
2.  Implementieren Sie die Abfragestatus-Handlermethode für den Befehl. Der `object` `sender` -Parameter kann in ein <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Objekt umgewandelt werden, das dazu verwendet wird, die verschiedenen Attribute des Menübefehls, so auch den Text, festzulegen. In der folgenden Tabelle sind die Eigenschaften der <xref:System.ComponentModel.Design.MenuCommand> -Klasse (aus der die MPF-Klasse <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> abgeleitet wird) aufgeführt, die den <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> -Flags entsprechen.  
  
    |MenuCommand-Eigenschaft|OLECMDF-Flag|  
    |--------------------------|------------------|  
    |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|OLECMDF_LATCHED|  
    |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|OLECMDF_INVISIBLE|  
    |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|OLECMDF_ENABLED|  
  
     Wenn Sie den Text eines Menübefehls ändern möchten, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> -Eigenschaft des <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Objekts (siehe folgendes Beispiel).  
  
     [!code-csharp[MenuText#11](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_11.cs)]
     [!code-vb[MenuText#11](../extensibility/codesnippet/VisualBasic/menucommands-vs-olemenucommands_11.vb)]  
  
 Das MPF behandelt automatisch den Fall nicht unterstützter oder unbekannter Gruppen. Ein Befehl wird nur dann unterstützt, wenn er dem <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> über die <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> -Methode hinzugefügt wurde.  
  
### <a name="handling-commands-by-using-the-iolecommandtarget-interface"></a>Behandeln von Befehlen über die IOleCommandTarget-Schnittstelle  
 Für Code, in dem die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle direkt verwendet wird, muss das VSPackage sowohl die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> - als auch die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle implementieren. Wird in dem VSPackage eine Projekthierarchie implementiert, müssen stattdessen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> - und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> -Methode der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> -Schnittstelle implementiert werden.  
  
 Sowohl die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> - als auch die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> -Methode sind so gestaltet, dass sie eine einzige Befehlssatz- `GUID` und ein Array mit Befehls-IDs als Eingabe empfangen. Es empfiehlt sich, dass VSPackages dieses Konzept mehrerer IDs in einem Aufruf vollständig unterstützen. Solange ein VSPackage nicht aus anderen VSPackages aufgerufen wird, können Sie aber davon ausgehen, dass das Befehlsarray nur eine Befehls-ID enthält, da die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> - und die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> -Methode in einer klar definierten Reihenfolge ausgeführt werden. Weitere Informationen zum routing finden Sie unter [Befehlsrouting in VSPackages](../extensibility/internals/command-routing-in-vspackages.md).  
  
 Für Code, in dem die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle direkt zur Befehlsbehandelung verwendet wird, müssen Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> -Methode wie folgt im VSPackage implementieren, um Befehle zu behandeln.  
  
##### <a name="to-implement-the-querystatus-method"></a>So implementieren Sie die QueryStatus-Methode  
  
1.  Geben Sie <xref:Microsoft.VisualStudio.VSConstants.S_OK> für gültige Befehle zurück.  
  
2.  Legen Sie das `cmdf` -Element des `prgCmds` -Parameters fest.  
  
     Der Wert des `cmdf` -Elements ist die logische Vereinigung von Werten aus der <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> -Enumeration, die über den logischen ODER-Operator (`|`) kombiniert werden.  
  
     Verwenden Sie die geeignete Enumeration entsprechend dem Status des Befehls:  
  
    -   Wenn der Befehl unterstützt wird:  
  
         `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
    -   Wenn der Befehl im Moment nicht sichtbar sein soll:  
  
         `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
    -   Wenn der Befehl eingeschaltet ist und es so aussieht, als wurde auf ihn geklickt:  
  
         `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
         Bei einer Verarbeitung von Befehlen, die in einem Menü des Typs `MenuControllerLatched`gehostet werden, ist der erste Befehl, der durch das `OLECMDF_LATCHED` -Flag markiert ist, der Standardbefehl, der im Menü beim Start angezeigt wird. Weitere Informationen zu `MenuController` -Menütypen finden Sie unter [Menu Element](../extensibility/menu-element.md)verwenden.  
  
    -   Wenn der Befehl derzeit aktiviert ist:  
  
         `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
    -   Wenn der Befehl zu einem Kontextmenü gehört und standardmäßig ausgeblendet ist:  
  
         `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXTMENU`  
  
    -   Wenn für den Befehl das `TEXTCHANGES` -Flag verwendet wird, legen Sie das `rgwz` -Element des `pCmdText` -Parameters auf den neuen Text des Befehls und das `cwActual` -Element des `pCmdText` Parameters auf die Länge der Befehlszeichenfolge fest.  
  
     Hinsichtlich Fehlerbedingungen muss die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> -Methode die folgenden Fehlerfälle behandeln:  
  
    -   Wenn die GUID unbekannt ist oder nicht unterstützt wird, geben Sie `OLECMDERR_E_UNKNOWNGROUP`zurück.  
  
    -   Wenn die GUID bekannt ist, aber die Befehls-ID unbekannt ist oder nicht unterstützt wird, geben Sie `OLECMDERR_E_NOTSUPPORTED`zurück.  
  
 Die VSPackage-Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> -Methode muss außerdem abhängig davon, ob der Befehl unterstützt wird und ob er erfolgreich behandelt wurde, bestimmte Fehlercodes zurückgeben.  
  
##### <a name="to-implement-the-exec-method"></a>So implementieren Sie die Exec-Methode  
  
-   Wenn die Befehls- `GUID` unbekannt ist, geben Sie `OLECMDERR_E_UNKNOWNGROUP`zurück.  
  
-   Wenn die `GUID` bekannt, aber die Befehls-ID unbekannt ist, geben Sie `OLECMDERR_E_NOTSUPPORTED`zurück.  
  
-   Wenn die `GUID` und die Befehls-ID mit dem GUID:ID-Paar übereinstimmen, das für den Befehl in der VSCT-Datei verwendet wird, führen Sie den Code aus, der dem Befehl zugeordnet ist, und geben Sie <xref:Microsoft.VisualStudio.VSConstants.S_OK>zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-XML-Schemareferenz](../extensibility/vsct-xml-schema-reference.md)   
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)