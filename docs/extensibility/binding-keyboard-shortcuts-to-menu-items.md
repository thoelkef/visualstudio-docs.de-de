---
title: "Bindung-Tastenkombinationen f&#252;r Men&#252;elemente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tastaturbefehl"
  - "Tastaturen"
  - "Befehlstaste"
  - "Tastenkombinationen"
  - "Menüelemente"
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Bindung-Tastenkombinationen f&#252;r Men&#252;elemente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um eine Tastenkombination auf einen benutzerdefinierten Menübefehl zu binden, fügen Sie einen Eintrag nur auf die VSCT\-Datei für das Paket. In diesem Thema wird erläutert, wie eine benutzerdefinierte Schaltfläche, Menüelement oder Symbolleistenbefehl eine Tastenkombination zugeordnet, und wie Sie in der Standard\-Editor das Tastaturzuordnungsschema anwenden oder nur für einen benutzerdefinierten Editor.  
  
 Vorhandene Visual Studio\-Menüelemente Tastenkombinationen zuweisen möchten, finden Sie unter [Identifizieren und Anpassen von Tastenkombinationen](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## Wählen eine Tastenkombination  
 Viele Tastenkombinationen sind in Visual Studio bereits verwendet. Sie sollten mehr als einen Befehl nicht dieselbe Tastenkombination zuweisen, da doppelte Bindungen schwer sind zu erkennen und können ebenfalls zu unvorhersehbare Ergebnissen führen. Daher ist es eine gute Idee, überprüfen die Verfügbarkeit einer Tastenkombination, damit Sie zugewiesen werden.  
  
#### So überprüfen die Verfügbarkeit einer Tastenkombination  
  
1.  In der **Extras \/ Optionen \/ Umgebung** wählen Sie im Fenster **Tastatur**.  
  
2.  Stellen Sie sicher, dass **Neue Tastenkomb in** Wert **Global**.  
  
3.  In der **Tastenkombination** Geben Sie die Tastenkombination, die Sie verwenden möchten.  
  
     Wenn die Tastenkombination bereits in Visual Studio verwendet wird die **Kontextmenü aktuell verwendete** Feld zeigt den Befehl, der die Verknüpfung derzeit aufruft.  
  
4.  Probieren Sie verschiedene Kombinationen von Schlüsseln, bis Sie eine gefunden, die nicht zugeordnet ist.  
  
    > [!NOTE]
    >  Tastenkombinationen, die ALT\-Taste verwenden möglicherweise ein Menü zu öffnen und nicht direkt einen Befehl ausführen. Aus diesem Grund die **Kontextmenü aktuell verwendete** Feld kann leer sein, wenn Sie eine Verknüpfung eingeben, die ALT\-Taste enthält. Überprüfen, ob die Verknüpfung ein Menü nicht schließende geöffnet wird die **Optionen** \(Dialogfeld\), und drücken die Tasten.  
  
 Das folgende Verfahren wird davon ausgegangen, dass Sie eine vorhandene VSPackage mit Menübefehl verfügen. Wenn Sie hierzu Hilfe benötigen, sehen Sie sich [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### Ein Befehl eine Tastenkombination zuweisen  
  
1.  Öffnen Sie die VSCT\-Datei für das Paket.  
  
2.  Erstellen Sie eine leere `<KeyBindings>` im Abschnitt nach der `<Commands>` wenn er nicht bereits vorhanden ist.  
  
    > [!WARNING]
    >  Weitere Informationen zu Tastenkombinationen finden Sie unter [Keybinding](../extensibility/keybinding-element.md).  
  
     In der `<KeyBindings>` im Abschnitt, erstellen Sie eine `<KeyBinding>` Eintrag.  
  
     Legen Sie die `guid`  und  `id` Attribute, die denen des Befehls, die Sie aufrufen möchten.  
  
     Legen Sie das `mod1` \-Attribut **Steuerelement**, **Alt**, oder **UMSCHALT**.  
  
     Abschnitt KeyBindings sollte etwa wie folgt aussehen:  
  
    ```xml  
    <KeyBindings> <KeyBinding guid="<name of command set>" id="<name of command id>" editor="guidVSStd97" key1="1" mod1="CONTROL"/> </KeyBindings>  
  
    ```  
  
 Wenn die Tastenkombination mit mehr als zwei Schlüssel erforderlich ist, legen Sie die `mod2` und `key2` Attribute.  
  
 In den meisten Fällen **UMSCHALT** sollten nicht ohne einen zweiten Modifizierer verwendet werden, da es bereits drücken führt dazu, dass die meisten Buchstaben ein Großbuchstabe oder ein Symbol.  
  
 Virtuelle Tastencodes können Sie die speziellen Schlüssel zuzugreifen, die nicht mit einem Zeichen zugeordnet werden, z. B. Funktionstasten verfügen und die **RÜCKTASTE** Schlüssel. Weitere Informationen finden Sie unter [virtuellen Tastencodes](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
 Um den Befehl in Visual Studio\-Editor verwenden, legen Sie das `editor` \-Attribut `guidVSStd97`.  
  
 Um den Befehl nur in einem benutzerdefinierten Editor verfügbar zu machen, legen Sie das `editor` \-Attribut auf den Namen des benutzerdefinierten Editors, die von generiert wurde die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Paketvorlage, wenn Sie das VSPackage erstellt enthält den benutzerdefinierten Editor. Um die Name\-Wert zu suchen, suchen Sie in der `<Symbols>` im Abschnitt für eine `<GuidSymbol>` Knoten, deren `name` Attribut endet in "`editorfactory`." Dies ist der Name der benutzerdefinierten Editor.  
  
## Beispiel  
 In diesem Beispiel wird die Tastenkombination STRG \+ ALT \+ C an einen Befehl mit dem Namen bindet `cmdidMyCommand` in einem Paket mit dem Namen `MyPackage`.  
  
```  
<CommandTable> . . . <Commands> . . . </Commands> <KeyBindings> <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand" key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" /> </KeyBindings> . . . </CommandTable>  
```  
  
## Beispiel  
 In diesem Beispiel bindet die Tastenkombination STRG \+ B, um einen Befehl mit dem Namen `cmdidBold` in einem Projekt namens `TestEditor`. Der Befehl ist nur in den benutzerdefinierten Editor und nicht in anderen Editoren verfügbar.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## Siehe auch  
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)