---
title: 'Vorgehensweise: Aufrufen des Workflow-Debuggers | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e702b402d5350641aa01d341106634efe5f6c6c4
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849270"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Vorgehensweise: Aufrufen des Workflow-Debuggers
Grundsätzlich debuggen Sie Workflows genau wie in anderen Visual Studio-Programmiersprachen geschriebene Programme. Sie können den Workflowdebugger auf folgende Weise starten:

- Wählen Sie im Menü **Debuggen** die Option **an den Prozess anhängen** aus, um den ausgesuchten Host Prozess für die Workflow Instanz auszuwählen. Dieses Verfahren entspricht dem Anhängen an einen Hostprozess in verwaltetem Code.

- Drücken Sie **F5** , um die Ausführung einer Instanz des Workflows zu starten, oder, um die Ausführung nach dem Erreichen eines Breakpoints fortzusetzen.

- Verwenden Sie Remotedebuggen. Weitere Informationen zur Verwendung des Remote Debuggens finden Sie unter Gewusst [wie: Aktivieren des Remote Debuggens](https://msdn.microsoft.com/library/febz73k0.aspx).

    > [!NOTE]
    > Wenn die Workflow Anwendung die x86-Architektur als Ziel verwendet und auf einem Computer gehostet wird, auf dem ein 64-Bit-Betriebssystem ausgeführt wird, funktioniert das Remote Debuggen nur dann, wenn [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] auf dem Remote Computer installiert ist oder das Ziel für die Workflow Anwendung in eine **beliebige CPU**geändert wird.

### <a name="stepping-through-code"></a>Schrittweises Durchlaufen des Codes

- Einzel **Schritt**: Sie können mit **F11**eine Aktivität in Einzelschritten ausführen. Der Debugger führt alle definierten Handler in Einzelschritten aus. Ist kein Handler definiert, wird die Aktivität übersprungen. Bei zusammengesetzten Aktivitäten, die andere Aktivitäten enthalten, führen Sie die erste ausgeführte Aktivität in einem Einzelschritt aus.

- Rück **Sprung:** Sie können eine Aktivität mit **UMSCHALT + F11**schrittweise ausführen. Mit dem Verlassen einer Aktivität werden die aktuelle Aktivität und alle dazugehörigen gleichgeordneten Aktivitäten bis zum Abschluss ausgeführt. Der Debugger wird dann auf dem übergeordneten Element der aktuellen Aktivität unterbrochen. Bei der Ausführung bis zum Rücksprung von einem Codehandler unterbricht der Debugger an der Aktivität, der der Handler zugewiesen ist.

- Prozedur **Schritt**: Sie können eine Aktivität mithilfe von **F10**überspringen. Wird ein Prozedurschritt für eine zusammengesetzte Aktivität ausgeführt, unterbricht der Debugger an der ersten ausführbaren untergeordneten Komponente der zusammengesetzten Aktivität. Wird ein Prozedurschritt für eine nicht zusammengesetzte Aktivität ausgeführt, zum Beispiel eine <xref:System.Activities.Statements.Assign>-Aktivität, führt der Debugger die Aktivität und die dazugehörigen Handler aus und unterbricht an der nächsten Aktivität. Handelt es sich bei der ausgeführten Aktivität um die letzte untergeordnete Aktivität einer zusammengesetzten Aktivität, hält der Debugger nach der Ausführung an der übergeordneten Aktivität an.

### <a name="debugging-with-f5"></a>Debuggen mit F5

- Wenn Sie ein Konsolen Anwendungsprojekt für einen Workflow entwickeln, drücken Sie einfach **F5** , um das Debuggen in Ihre Anwendung und den Workflow zu starten. Wenn Sie eine Aktivitätsbibliothek erstellen, muss eine ausführbare Hostanwendung als Startprojekt gegeben sein. Wenn Sie ein Startprojekt in **Projektmappen-Explorer**festlegen möchten, klicken Sie mit der rechten Maustaste auf den Projektnamen des Hosts, und wählen Sie **als Startprojekt festlegen**aus.

## <a name="see-also"></a>Siehe auch
 Gewusst [wie: Festlegen von Haltepunkten in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [Debuggen von Workflows mit dem Workflow-Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
