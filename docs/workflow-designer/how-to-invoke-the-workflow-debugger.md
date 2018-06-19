---
title: 'Workflow-Designer - Vorgehensweise: Aufrufen den Workflow-Debugger'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3fb48ee50ebc7c1e211634082cfc51dcb170a3de
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975673"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Vorgehensweise: Aufrufen des Workflow-Debuggers

Grundsätzlich debuggen Sie Workflows genau wie in anderen Visual Studio-Programmiersprachen geschriebene Programme. Sie können den Workflowdebugger auf folgende Weise starten:

-   Wählen Sie **an den Prozess anhängen** auf die **Debuggen** Menü, um den ausgeführten Hostprozess für die Workflowinstanz auszuwählen. Dieses Verfahren entspricht dem Anhängen an einen Hostprozess in verwaltetem Code.

-   Drücken Sie **F5** um mit einer Instanz des Workflows neu auszuführen oder weiter auszuführen, nachdem ein Haltepunkt erreicht wurde.

-   Verwenden Sie Remotedebuggen. Informationen zur Verwendung des Remotedebuggens finden Sie unter [Vorgehensweise: Aktivieren von Remotedebuggen](http://go.microsoft.com/fwlink/?LinkId=196257).

    > [!NOTE]
    > Wenn die workflowanwendung für die X86 diejenige Architektur und auf einem Computer mit einem 64-Bit-Betriebssystem gehostet wird, Remotedebuggen nicht verwendet werden, es sei denn, die Visual Studio auf dem Remotecomputer installiert ist oder das Ziel für die workflowanwendung in geändert wird **Beliebige CPU**.

## <a name="stepping-through-code"></a>Schrittweises Durchlaufen des Codes

-   **Schritt In**: Sie können in eine Aktivität mit einem Einzelschritt **F11**. Der Debugger führt alle definierten Handler in Einzelschritten aus. Ist kein Handler definiert, wird die Aktivität übersprungen. Bei zusammengesetzten Aktivitäten, die andere Aktivitäten enthalten, führen Sie die erste ausgeführte Aktivität in einem Einzelschritt aus.

-   **Ausführen bis Rücksprung:** können Sie eine Aktivität mit schrittweise **UMSCHALT + F11**. Mit dem Verlassen einer Aktivität werden die aktuelle Aktivität und alle dazugehörigen gleichgeordneten Aktivitäten bis zum Abschluss ausgeführt. Der Debugger wird dann auf dem übergeordneten Element der aktuellen Aktivität unterbrochen. Bei der Ausführung bis zum Rücksprung von einem Codehandler unterbricht der Debugger an der Aktivität, der der Handler zugewiesen ist.

-   **Prozedurschritt**: Sie können eine Aktivität mit Prozedurschritt **F10**. Wird ein Prozedurschritt für eine zusammengesetzte Aktivität ausgeführt, unterbricht der Debugger an der ersten ausführbaren untergeordneten Komponente der zusammengesetzten Aktivität. Wird ein Prozedurschritt für eine nicht zusammengesetzte Aktivität ausgeführt, zum Beispiel eine <xref:System.Activities.Statements.Assign>-Aktivität, führt der Debugger die Aktivität und die dazugehörigen Handler aus und unterbricht an der nächsten Aktivität. Handelt es sich bei der ausgeführten Aktivität um die letzte untergeordnete Aktivität einer zusammengesetzten Aktivität, hält der Debugger nach der Ausführung an der übergeordneten Aktivität an.

## <a name="debugging-with-f5"></a>Debuggen mit F5

-   Wenn Sie ein Workflow-Konsolenanwendungsprojekt erstellen, drücken Sie einfach **F5** zum Debuggen der Anwendung und den Workflow zu starten. Wenn Sie eine Aktivitätsbibliothek erstellen, muss eine ausführbare Hostanwendung als Startprojekt gegeben sein. Zum Festlegen eines Startprojekts im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektnamen des Hosts, und wählen Sie **als Startprojekt festlegen**.

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Festlegen von Haltepunkten in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Debuggen von Workflows mit dem Workflow-Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)