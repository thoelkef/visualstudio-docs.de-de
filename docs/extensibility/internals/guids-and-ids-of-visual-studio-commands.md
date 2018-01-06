---
title: GUIDs und IDs der Visual Studio-Befehle | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 44ae5ff7e9095d6c88d753342da30983b30b7364
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUIDs und IDs der Visual Studio-Befehle
Die GUID und ID-Werte in der integrierten Entwicklungsumgebung (IDE) von Visual Studio enthaltenen Befehle werden in der VSCT-Dateien definiert, die als Teil der Visual Studio-SDK installiert sind. Weitere Informationen finden Sie unter [IDE-Defined Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Weitere Informationen zum Arbeiten mit IDE-Objekte, die in der VSCT-Dateien definiert sind, finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="finding-a-command-definition"></a>Suchen eine Befehlsdefinition  
 Da mehr als tausend Befehle in Visual Studio definiert wird, ist es unpraktisch, alle hier aufgelistet. Stattdessen folgendermaßen Sie vor, um die Definition eines Befehls zu suchen.  
  
#### <a name="to-locate-a-command-definition"></a>Um eine Befehlsdefinition zu suchen.  
  
1.  Öffnen Sie in Visual Studio die folgenden Dateien in den *Visual Studio SDK-Installationspfad*\VisualStudioIntegration\Common\Inc\ Ordner: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.  
  
     Die meisten Visual Studio-Befehle werden in SharedCmdDef.vsct und ShellCmdDef.vsct definiert. VsDbgCmdUsed.vsct definiert Befehle, die der Debugger betreffen, und Venusmenu.vsct definiert Befehle, die für die Webentwicklung spezifisch sind.  
  
2.  Wenn der Befehl ein Menüelement ist, notieren Sie den genauen Text des Menüelements. Wenn der Befehl eine Schaltfläche auf einer Symbolleiste ist, beachten Sie den QuickInfo-Text, der angezeigt wird, wenn Sie darauf zeigen.  
  
3.  Drücken Sie STRG + F, öffnen Sie die **suchen** (Dialogfeld).  
  
4.  In der **Suchen nach** geben den notierten Text in Schritt 2.  
  
5.  Überprüfen Sie, ob **alle geöffneten Dokumente** wird angezeigt, der **Suchen in** Feld.  
  
6.  Klicken Sie auf die **Weitersuchen** so lange, bis der Text ausgewählt ist, in der `<Strings>` Abschnitt eine [Schaltflächenelement](../../extensibility/button-element.md).  
  
     Die `<Button>` Element, das in der Befehl angezeigt wird, ist der Befehlsdefinition.  
  
 Wenn Sie die Befehlsdefinition gefunden haben, können Sie eine Kopie des Befehls in einem anderen Menüs oder Symbolleisten einfügen, durch das Erstellen einer [CommandPlacement Element](../../extensibility/commandplacement-element.md) , hat die gleiche `guid` und `id` Werte wie der Befehl. Weitere Informationen finden Sie unter [erstellen Wiederverwendbarer Gruppen von Schaltflächen](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Sonderfälle  
 In den folgenden Fällen kann die Menütext oder QuickInfo-Text nicht exakt Neuigkeiten in der Befehlsdefinition.  
  
-   Menüelemente, die ein jeweils unterstrichene Zeichen, wie z. B. enthalten die **Drucken** Befehl die **Datei** Menü, in der die P unterstrichen ist.  
  
     Zeichen, die das Zeichen "&" im Menü Elementnamen vorangestellt werden angezeigt unterstrichen angezeigt. Allerdings werden VSCT-Dateien geschrieben, in XML, das das Zeichen "&" verwendet, um Sonderzeichen anzugeben und setzt voraus, dass ein kaufmännisches und-Zeichen, die angezeigt werden soll wie folgt buchstabiert werden muss als&amp;". Deshalb in einer VSCT-Datei die **P**Rint-Befehl angezeigt wird, als "&amp;drucken".  
  
-   Befehle, die dynamischen Text, z. B. verfügen **speichern** *aktuellen Dateinamen*, und dynamisch generierte Menüelemente, z. B. die Elemente auf der **zuletzt verwendeter Dateien** Liste.  
  
     Es ist keine zuverlässige Möglichkeit, dynamische Text gesucht werden soll. Eine Gruppe, die den gewünschten Befehl durch consulting hostet stattdessen suchen [GUIDs und IDs der Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) oder [GUIDs und IDs der Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md), und suchen Sie nach der ID dieser Gruppe. Verfügt der Befehlsdefinition nicht die Gruppe als seine [übergeordneten Elements](../../extensibility/parent-element.md), SharedCmdPlace.vsct und ShellCmdPlace.vsct (oder VsDbgCmdPlace.vsct für Debuggerbefehle) suchen eine `<CommandPlacement>` Element, das das übergeordnete Element des legt die -Befehl. AndVsDbgCmdPlace.vsct SharedCmdPlace.vsct ShellCmdPlace.vsct, befinden sich in der *Visual Studio SDK-Installationspfad*\VisualStudioIntegration\Common\Inc\ Ordner.  
  
## <a name="see-also"></a>Siehe auch  
 [MenuCommands im Vergleich zu OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)