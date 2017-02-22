---
title: "GUIDs und IDs der Visual Studio-Befehle | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehle"
  - "ID"
  - "Befehl-Platzierung"
  - "Visual Studio-Befehl"
  - "GUID"
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# GUIDs und IDs der Visual Studio-Befehle
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der GUID\-Wert und ID\-Werte der Befehle, die in der integrierten Entwicklungsumgebung \(IDE\) von Visual Studio enthaltenen werden in .vsct\-Dateien definiert, die als Teil von Visual Studio SDK installiert werden.  Weitere Informationen finden Sie unter [IDE\-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Weitere Informationen zum Arbeiten mit IDE\-Objekten, die in .vsct\-Dateien definiert werden, finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)funktioniert.  
  
## Eine Befehlsdefinition suchen  
 Da Visual Studio mehrere tausend Befehle definiert, ist es nicht empfehlenswert, alle um sie an dieser Stelle aufzulisten.  Stattdessen führen Sie die folgenden Schritte aus, um die Definition eines Befehls zu suchen.  
  
#### So erstellen Sie eine Befehlsdefinition suchen  
  
1.  Öffnen Sie in Visual Studio die folgenden Dateien in *Pfad SDK\-Installations Visual Studio*\\ VisualStudioIntegration Inc. \\ \\ Common \\ Ordner: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.  
  
     Die meisten Visual Studio\-Befehle werden in SharedCmdDef.vsct und ShellCmdDef.vsct definiert.  VsDbgCmdUsed.vsct Befehle definiert, die den Debugger beziehen, und Venusmenu.vsct Befehle definiert, die zur Webentwicklung spezifisch sind.  
  
2.  Wenn der Befehl ein Menüelement ist, notieren Sie sich den genauen Wortlaut des Menüelements.  Wenn der Befehl eine Schaltfläche auf einer Symbolleiste befindet, notieren Sie sich den QuickInfo\-Text, der angezeigt wird, wenn Sie auf darauf zeigen.  
  
3.  Drücken Sie STRG\+F, um den **Find** Dialogfeld zu öffnen.  
  
4.  Geben Sie im Feld **Suchen nach** Geben Sie den Text ein, den Sie in Schritt 2 werden.  
  
5.  Stellen Sie sicher, dass **Alle geöffneten Dokumente** im **Suchen in** Feld angezeigt wird.  
  
6.  Klicken Sie auf die Schaltfläche **Weitersuchen** , bis der Text im `<Strings>`\-Abschnitt von [Button\-Element](../../extensibility/button-element.md)ausgewählt ist.  
  
     Das Element, das `<Button>` aussieht, ist der Befehl in der Befehlsdefinition.  
  
 Wenn Sie die Befehlsdefinition gefunden haben, können Sie eine Kopie des Befehls in ein anderes Menü oder einer Symbolleiste setzen, indem Sie [CommandPlacement\-Element](../../extensibility/commandplacement-element.md) erstellen, die gleiche `guid` und `id`\-Werte wie der Befehl verfügt.  Weitere Informationen finden Sie unter [Erstellen von wieder verwendbaren Gruppen von Schaltflächen](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### Besondere Fälle  
 In den folgenden Fällen gleichen der Menütext oder möglicherweise nicht genau den QuickInfo\-Text ab, was in der Befehlsdefinition ist.  
  
-   Menüelemente, die ein unterstrichenes Zeichen, z. B. der **Drucken** Befehl im Menü **Datei** enthalten, wobei P unterstrichen ist.  
  
     Zeichen, die vom '&'Zeichen in den Namen des Menüelements vorangestellt werden, wie unterstrichen angezeigt werden.  .vsct\-Dateien werden jedoch in XML geschrieben, das das Zeichen „&verwendet, um Sonderzeichen anzugeben und erfordert, dass ein kaufmännisches Und\-Zeichen, das angezeigt werden soll, formuliert werden muss, z. B.“&amp;“.  Daher werden in einer .vsct\-Datei, wird der Befehl **Drucken**z '&amp;Print'.  
  
-   Befehle, die dynamischen Text, z. B. **Speichern** *Aktueller Dateiname*und dynamisch generierten Menüelemente verfügen, wie die Elemente auf der **Zuletzt geöffnete Dateien** Liste.  
  
     Es gibt keine zuverlässige Möglichkeit, auf dynamischem Text zu suchen.  Stattdessen müssen Sie eine Gruppe, die als Host für den gewünschten Befehl, durch das Nachschlagen von [GUIDs und IDs der Visual Studio\-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) oder [GUIDs und IDs der Visual Studio\-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)suchen und auf der ID dieser Gruppe.  Wenn der Befehlsdefinition die Gruppe nicht als [Parent\-Element](../../extensibility/parent-element.md), Suchen und SharedCmdPlace.vsct ShellCmdPlace.vsct \(oder VsDbgCmdPlace.vsct für Debuggerbefehle\) für ein `<CommandPlacement>`\-Element, das das übergeordnete Element des Befehls festlegen.  SharedCmdPlace.vsct, ShellCmdPlace.vsct, andVsDbgCmdPlace.vsct sind in *Pfad SDK\-Installations Visual Studio*\\ VisualStudioIntegration \\ Common \\ Inc. \\ Ordner.  
  
## Siehe auch  
 [MenuCommand\- und OleMenuCommand\-Objekte](../../misc/menucommands-vs-olemenucommands.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML\-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)