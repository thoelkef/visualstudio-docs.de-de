---
title: Debuggen von Workflows mit dem Workflow-Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b06ee7101dcb6b227f8e7f0228730fb0668695b4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998845"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>Debuggen von Workflows mit Workflow-Designer

Die **Workflow-Designer** bietet die Möglichkeit zum Debuggen von Workflows und benutzerdefinierte Aktivitäten. Vorgang und Verhalten sind vergleichbar mit der standardmäßigen Visual Studio-Debugger.

## <a name="invoke-the-workflow-debugger"></a>Aufrufen des Workflow-Debuggers

Grundsätzlich debuggen Sie Workflows genau wie in anderen Visual Studio-Programmiersprachen geschriebene Programme. Sie können den Workflowdebugger auf folgende Weise starten:

- Wählen Sie **an den Prozess anhängen** auf die **Debuggen** Menü Wählen Sie den ausgeführten Hostprozess für Ihre Workflowinstanz. Dieses Verfahren entspricht dem Anhängen an einen Hostprozess in verwaltetem Code.

- Drücken Sie **F5** um eine Instanz des Workflows zu starten oder weiter ausgeführt, nachdem ein Haltepunkt erreicht wurde.

- Verwenden Sie Remotedebuggen. Weitere Informationen zur Verwendung des Remotedebuggens finden Sie unter [Vorgehensweise: Aktivieren des Remotedebuggens](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > Wenn die workflowanwendung die X86 abzielt Architektur und gehostet wird, auf einem Computer unter einem 64-Bit-Betriebssystem, das Remotedebuggen nicht funktioniert, wenn Visual Studio auf dem Remotecomputer installiert ist, oder das Ziel für die workflowanwendung in geändertwird **Beliebige CPU**.

## <a name="step-through-code"></a>Schritt-für-Schritt-Ausführung des Codes

- **Schritt**: Einzelschritt in eine Aktivität durch Drücken von **F11**. Der Debugger führt alle definierten Handler in Einzelschritten aus. Ist kein Handler definiert, wird die Aktivität übersprungen. Bei zusammengesetzten Aktivitäten, die andere Aktivitäten enthalten, führen Sie die erste ausgeführte Aktivität in einem Einzelschritt aus.

- **Ausführen Sie bis Rücksprung aus:** Prozedurschritt aus einer Aktivität, durch Drücken von **UMSCHALT**+**F11**. Mit dem Verlassen einer Aktivität werden die aktuelle Aktivität und alle dazugehörigen gleichgeordneten Aktivitäten bis zum Abschluss ausgeführt. Der Debugger wird dann auf dem übergeordneten Element der aktuellen Aktivität unterbrochen. Bei der Ausführung bis zum Rücksprung von einem Codehandler unterbricht der Debugger an der Aktivität, der der Handler zugewiesen ist.

- **Prozedurschritt**: Überspringen einer Aktivität durch Drücken von **F10**. Wird ein Prozedurschritt für eine zusammengesetzte Aktivität ausgeführt, unterbricht der Debugger an der ersten ausführbaren untergeordneten Komponente der zusammengesetzten Aktivität. Wird ein Prozedurschritt für eine nicht zusammengesetzte Aktivität ausgeführt, zum Beispiel eine <xref:System.Activities.Statements.Assign>-Aktivität, führt der Debugger die Aktivität und die dazugehörigen Handler aus und unterbricht an der nächsten Aktivität. Handelt es sich bei der ausgeführten Aktivität um die letzte untergeordnete Aktivität einer zusammengesetzten Aktivität, hält der Debugger nach der Ausführung an der übergeordneten Aktivität an.

## <a name="debug-with-f5"></a>Debuggen mit F5

Wenn Sie eine Workflow-Konsolen-app erstellen, drücken Sie einfach **F5** um Debuggen der Anwendung und den Workflow zu starten. Wenn Sie selbstständig eine Aktivitätsbibliothek erstellen, müssen Sie eine ausführbare hostanwendung als Startprojekt angeben. Zum Festlegen eines Startprojekts im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektnamen, der den Host, und wählen Sie **als Startprojekt festlegen**.