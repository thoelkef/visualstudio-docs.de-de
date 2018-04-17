---
title: Tastenkombinationen im Workflow-Designer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29d96eb6d738fbf23749bec601743002a451ad06
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Tastenkombinationen im Workflow-Designer

Alle von der Kernfunktionalität von Windows Workflow-Designer kann über die Tastatur zugegriffen werden.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Bedienen des Workflow-Designers mithilfe der Tastatur

In [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] gelten die globalen Tastenkombinationen und Debugging-Tastenkombinationen für [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Es wurde auch eine Reihe von Tastenkombinationen erstellt, die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] eigen sind. In [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] können alle Tastenkombinationen neu zugeordnet werden. In einer neu gehosteten Anwendung sind diese Tastenkombinationen jedoch hartcodiert.

### <a name="workflow-designer-keyboard-shortcuts"></a>Tastenkombinationen des Workflow-Designers

In der folgenden Tabelle werden die Standardtastenkombinationen zusammengefasst, die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]-Befehlen zugewiesenen sind.

|Tastenkombination|Zweck|
|--------------|-------------|
|STRG+E, A|Argument-Designer anzeigen oder ausblenden.|
|STRG+E, C|Die ausgewählte Aktivität direkt reduzieren.|
|STRG+E, E|Die ausgewählte Aktivität direkt erweitern.|
|STRG+E, F|Die ausgewählten Aktivitäten in einem Flussdiagramm verbinden.|
|CTRL+E+I|Imports-Designer anzeigen oder ausblenden.|
|STRG+E, M|Der Tastaturfokus wechselt zum nächsten Element in der Aktivierreihenfolge.|
|STRG+E, N|Eine neue Variable im Bereich der ausgewählten Aktivität (oder der nächsten Aktivität) erstellen.|
|STRG+E, O|Die Übersichtskarte anzeigen oder ausblenden.|
|STRG+E, P|Zum übergeordneten Element der ausgewählten Aktivität wechseln. In der Brotkrümelnavigation eine Ebene nach oben gehen und die Stammaktivität auf der Designeroberfläche ändern.|
|STRG+E, S|Das Element der aktuellen Auswahl mit dem Tastaturfokus hinzufügen.|
|STRG+E, V|Variablen-Designer anzeigen oder ausblenden.|
|STRG+E, X|Alle Aktivitäten im Workflow erweitern.|
|STRG+ALT+F6|Den Tastaturfokus im aktuellen Benutzeroberflächenbereich auf den nächsten Bereich der Folge verschieben. Die Reihenfolge ist wie folgt definiert:<br /><br /> 1.  Brotkrümelnavigationsleiste.<br />2.  Designeroberfläche<br />3.  Argumente/Variablen/Import-Designer, sofern geöffnet<br />4.  Shell|

### <a name="flowchart"></a>Flussdiagramm

In der folgenden Liste sind die Gesten aufgeführt, mit denen ein Flussdiagramm mithilfe der Tastatur erstellt wurde. Wie in den restlichen Teilen von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] werden der Designeroberfläche Aktivitäten mit den globalen Toolbox-Tastenkombinationen, die in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] verfügbar sind, hinzugefügt.

- Um eine Aktivität zu verschieben, markieren Sie die Aktivität, und ordnen Sie sie mithilfe der PFEILTASTEN neu an.

- Um die Größe eines Flussdiagramms zu ändern, schieben Sie eine Aktivität mit den PFEILTASTEN über den aktuellen Rahmen des Flussdiagramms hinaus. Die Größe des Flussdiagramms wird automatisch geändert.

- Um eine Aktivität als Startknoten festzulegen, verwenden die **als Startknoten festlegen** im Kontextmenü den Befehl.

- So verbinden Sie Aktivitäten:

    1.  Wählen Sie die Quellaktivität durch Drücken der TAB-TASTE aus.

    2.  Drücken Sie STRG+E, M so oft wie erforderlich, um den Tastaturfokus auf die Zielaktivität zu verschieben.

    3.  Drücken Sie STRG+E, S, um die Zielaktivität der Auswahl hinzuzufügen.

    4.  Drücken Sie STRG+E, F, um den Connector von der Quelle zum Ziel hinzuzufügen.

Hinweise zum Verbinden von Aktivitäten mithilfe der Tastatur:

- Sie können gleichzeitig mehrere Verbindungen herstellen, indem Sie der Auswahl mehrere Aktivitäten hinzufügen, bevor Sie STRG+E, F drücken. Die Verbindungen werden in der Reihenfolge hergestellt, in der die Aktivitäten der Auswahl hinzugefügt wurden.

- Selbst wenn ein Aktivitätenpaar nicht verbunden werden kann, z. B. wenn die Quellaktivität bereits über eine ausgehende Verbindung verfügt, werden die anderen Verbindungen zwischen Aktivitäten in der Auswahl noch hergestellt, sofern dies möglich ist.

- Wenn eine **FlowDecision** in der Auswahl enthalten ist und die **FlowDecision** keine ausgehenden Connectors besitzt, der Connector befindet sich auf die **"true"** Verzweigung.

### <a name="expression-editing"></a>Ausdrucksbearbeitung

Standardmäßig sind die Standardtastenkombinationen für die Textbearbeitung in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] auch im Ausdrucks-Editor in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] gültig, wobei den folgenden Einschränkungen gelten:

- Eine Neuzuordnung der Tastenkombinationen für die folgenden Befehle ist wirkungslos. Beim Bearbeiten eines Ausdrucks können Sie nur über die Standardtastenkombinationen auf diese Befehle zugreifen.

   - Ausschneiden
   - Kopieren
   - Einfügen
   - Alle auswählen
   - Rückgängigmachen
   - Wiederholen

- Um die Tastenkombinationen für die Befehle zur Bearbeitung von Ausdrücken in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] neu zuzuordnen, bearbeiten Sie die Verknüpfungen im Geltungsbereich von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Im Geltungsbereich von Text-Editor vorgenommene Änderungen gelten nicht automatisch für [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Wenn Sie Verknüpfungen an beiden Stellen neu zuordnen möchten, müssen Sie die Änderungen zweimal (einmal für jeden Bereich) vornehmen.