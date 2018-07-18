---
title: Workflow-Designer - Tastenkombinationen im Workflow-Designer
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83664d6402c23da89adf332bc9cd34eac89384bb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977643"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Tastenkombinationen im Workflow-Designer

Alle von der Kernfunktionalität von Windows Workflow-Designer kann über die Tastatur zugegriffen werden.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Bedienen des Workflow-Designers mithilfe der Tastatur

In Visual Studio 2010 wenden die globalen Tastenkombinationen und debugging-Tastenkombinationen auf die Workflow-Designer. Darüber hinaus wurden eine Anzahl von bestimmten Workflow-Designer-Tastenkombinationen erstellt. In Visual Studio 2010 können alle Tastenkombinationen zugeordnet werden. In einer neu gehosteten Anwendung sind diese Tastenkombinationen jedoch hartcodiert.

### <a name="workflow-designer-keyboard-shortcuts"></a>Tastenkombinationen des Workflow-Designers

In der folgenden Tabelle werden die Standardtastenkombinationen zugewiesen, die auf Workflow-Designer-Befehle zusammengefasst.

|Verknüpfung|Zweck|
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

In der folgenden Liste sind die Gesten aufgeführt, mit denen ein Flussdiagramm mithilfe der Tastatur erstellt wurde. Wie in den Rest des Workflow-Designer werden der Designeroberfläche, die mit den globalen Toolbox-Tastenkombinationen, die mit Visual Studio 2010 bereitgestellten Aktivitäten hinzugefügt.

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

Standardmäßig gelten die Standardtastenkombinationen für Visual Basic-Textbearbeitung innerhalb des Ausdrucks-Editors im Workflow-Designer, mit folgenden Einschränkungen:

- Eine Neuzuordnung der Tastenkombinationen für die folgenden Befehle ist wirkungslos. Beim Bearbeiten eines Ausdrucks können Sie nur über die Standardtastenkombinationen auf diese Befehle zugreifen.

   - Ausschneiden
   - Kopieren
   - Einfügen
   - Alle auswählen
   - Rückgängigmachen
   - Wiederholen

- Um die Tastenkombinationen für Befehle zum Ausdruck bearbeiten im Workflow-Designer in Visual Studio 2010 neu zuzuordnen, bearbeiten Sie die Verknüpfungen im Workflow-Designer-Bereich. In den Text-Editor-Bereich vorgenommene Änderungen gelten nicht automatisch für Workflow-Designer. Wenn Sie Verknüpfungen an beiden Stellen neu zuordnen möchten, müssen Sie die Änderungen zweimal (einmal für jeden Bereich) vornehmen.