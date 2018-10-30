---
title: GUIDs und IDs der Visual Studio-Befehle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4aa34194933a63206133685b52def81b784b6154
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219828"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUIDs und IDs der Visual Studio-Befehle
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die GUID und ID-Werte in der integrierten Entwicklungsumgebung (IDE) von Visual Studio enthaltenen Befehle werden in der VSCT-Dateien definiert, die als Teil der Visual Studio SDK installiert sind. Weitere Informationen finden Sie unter [IDE-Defined Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Weitere Informationen zum Arbeiten mit IDE-Objekten, die in der VSCT-Dateien definiert sind, finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="finding-a-command-definition"></a>Suchen eine Befehlsdefinition  
 Da Visual Studio mehr als tausend Befehle definiert, ist es unpraktisch, dass sie alle hier aufgeführt. Stattdessen folgendermaßen Sie vor, um die Definition eines Befehls zu suchen.  
  
#### <a name="to-locate-a-command-definition"></a>Um eine Befehlsdefinition zu suchen.  
  
1. In Visual Studio, öffnen Sie die folgenden Dateien in die *Visual Studio SDK-Installationspfad*\VisualStudioIntegration\Common\Inc\ Ordner: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.  
  
    Die meisten Visual Studio-Befehle werden in SharedCmdDef.vsct und ShellCmdDef.vsct definiert. VsDbgCmdUsed.vsct definiert Befehle, die sich an den Debugger zu beziehen und Venusmenu.vsct definiert Befehle, die spezifisch für die Web-Entwicklung sind.  
  
2. Wenn der Befehl ein Menüelement ist, notieren Sie den genauen Text des Menüelements. Wenn der Befehl eine Schaltfläche auf einer Symbolleiste ist, beachten Sie den QuickInfo-Text, der angezeigt wird, wenn Sie darauf anhalten.  
  
3. Drücken Sie STRG + F, zum Öffnen der **finden** Dialogfeld.  
  
4. In der **Suchen nach** Feld, und geben Sie in Schritt 2 den Text, die Sie notiert haben.  
  
5. Überprüfen Sie, ob **alle geöffneten Dokumente** wird angezeigt, der **Suchen in** Feld.  
  
6. Klicken Sie auf die **Weitersuchen** so lange, bis der Text ausgewählt ist, in der `<Strings>` Teil einer [Button-Element](../../extensibility/button-element.md).  
  
    Die `<Button>` -Element, das in der Befehl angezeigt wird, wird der Befehlsdefinition.  
  
   Wenn Sie die Befehlsdefinition gefunden haben, können Sie eine Kopie des Befehls in einem anderen Menü oder Symbolleiste einfügen, durch das Erstellen einer [CommandPlacement-Element](../../extensibility/commandplacement-element.md) verfügt, die über die gleiche `guid` und `id` Werte wie für den Befehl. Weitere Informationen finden Sie unter [Erstellen von Wiederverwendbaren Gruppen von Schaltflächen](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Sonderfälle  
 In den folgenden Fällen den Menütext oder QuickInfo-Text entspricht möglicherweise nicht exakt neuerungen in der Befehlsdefinition.  
  
-   Menüelemente, die ein unterstrichenes Zeichen, z. B. enthalten die **Drucken** Befehl die **Datei** Menü in der die P unterstrichen ist.  
  
     Zeichen, die durch das Zeichen "&" im Menü Elementnamen vorangestellt werden angezeigt, unterstrichen angezeigt. VSCT-Dateien wurden jedoch in XML, das das Zeichen "&" verwendet, um Sonderzeichen anzugeben und erfordert, dass ein kaufmännisches und-Zeichen, das angezeigt werden soll geschrieben werden muss als&amp;". Aus diesem Grund in einer VSCT-Datei die **Drucken** -Befehl angezeigt wird, als "&amp;drucken".  
  
-   Befehle, die dynamischer Text, z. B. auf **speichern** *aktuellen Dateinamen*, und dynamisch generierte Menüelemente, z. B. die Elemente auf der **zuletzt verwendeten Dateien** Liste.  
  
     Es ist keine zuverlässige Möglichkeit, die dynamischer Text suchen. Stattdessen finden Sie eine Gruppe, die den gewünschten Befehl von consulting hostet [GUIDs und IDs der Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) oder [GUIDs und IDs der Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md), und suchen Sie auf die ID dieser Gruppe. Verfügt die Befehlsdefinition nicht die Gruppe als seine [übergeordnetes Element](../../extensibility/parent-element.md), SharedCmdPlace.vsct und ShellCmdPlace.vsct (oder VsDbgCmdPlace.vsct für Debuggerbefehle) Suchen einer `<CommandPlacement>` -Element, das das übergeordnete Element der legt diesen fest der -Befehl. SharedCmdPlace.vsct, ShellCmdPlace.vsct, andVsDbgCmdPlace.vsct befinden sich in der *Visual Studio SDK-Installationspfad*\VisualStudioIntegration\Common\Inc\-Ordner.  
  
## <a name="see-also"></a>Siehe auch  
 [MenuCommands im Vergleich zu OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)

