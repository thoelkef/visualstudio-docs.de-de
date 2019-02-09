---
title: Workflow-Designer - Tastenkombinationen im Workflow-Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c8d86c206eca3ecb1e1fc43e9540485cd83f93a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55918428"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Tastenkombinationen im Workflow-Designer

Alle die Kernfunktionen des Workflow-Designers kann über die Tastatur zugegriffen werden.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Bedienen des Workflow-Designers mithilfe der Tastatur

In Visual Studio gelten die globalen Tastenkombinationen und debugging-Tastenkombinationen für die Workflow-Designer ein. Darüber hinaus wurden eine Anzahl von bestimmten Workflow-Designer-Tastenkombinationen erstellt. In Visual Studio können alle Tastenkombinationen neu, zugeordnet werden. In einer neu gehosteten Anwendung sind diese Tastenkombinationen jedoch hartcodiert.

### <a name="workflow-designer-keyboard-shortcuts"></a>Tastenkombinationen des Workflow-Designers

Die folgende Tabelle enthält die Standardtastenkombinationen für Workflow-Designer Befehle zugewiesen.

|Verknüpfung|Zweck|
|-|-------------|
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

In der folgenden Liste sind die Gesten aufgeführt, mit denen ein Flussdiagramm mithilfe der Tastatur erstellt wurde. Aktivitäten werden wie in den Rest des Workflow-Designers die Oberfläche des Designers mit der globalen Toolbox-Tastenkombinationen, die die in Visual Studio hinzugefügt.

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

- Wenn eine **FlowDecision** befindet sich in der Auswahl und die **FlowDecision** keine ausgehenden Connectors besitzt, der Connector befindet sich auf die **"true"** Branch.

### <a name="expression-editing"></a>Ausdrucksbearbeitung

Standardmäßig gelten die Standardtastenkombinationen zum Bearbeiten von Text in Visual Basic in der Ausdrucks-Editor im Workflow-Designer, mit folgenden Einschränkungen:

- Eine Neuzuordnung der Tastenkombinationen für die folgenden Befehle ist wirkungslos. Beim Bearbeiten eines Ausdrucks können Sie nur über die Standardtastenkombinationen auf diese Befehle zugreifen.

   - Ausschneiden
   - Kopieren
   - Einfügen
   - Alle auswählen
   - Rückgängigmachen
   - Wiederholen

- Um die Tastenkombinationen für Befehle zum Ausdruck bearbeiten im Workflow-Designer in Visual Studio neu zuordnen, bearbeiten Sie die Tastenkombinationen im Workflow-Designer-Bereich. In den Text-Editor-Bereich vorgenommene Änderungen gelten nicht automatisch für Workflow-Designer. Wenn Sie Verknüpfungen an beiden Stellen neu zuordnen möchten, müssen Sie die Änderungen zweimal (einmal für jeden Bereich) vornehmen.