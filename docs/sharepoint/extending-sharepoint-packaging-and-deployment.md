---
title: Erweitern von SharePoint-Packen und-bereitstellen | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1f18c88e72a40d3070d9a366e0c6c4e0f3888565
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628389"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>Erweitern von SharePoint-Packen und-bereitstellen
  Sie können den Paketerstellungs- und Bereitstellungsprozess für SharePoint-Projekte erweitern.

## <a name="create-deployment-steps"></a>Erstellen von Bereitstellungsschritten
 Wenn Sie ein SharePoint-Projekt bereitstellen, führt [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] eine Reihe von Schritten zur Bereitstellung aus. Visual Studio umfasst integrierte Bereitstellungsschritte für viele Aufgaben wie das Zurückziehen und Hinzufügen von Projektmappen. Sie können jedoch auch eigene Bereitstellungsschritte erstellen.

 Eine exemplarische Vorgehensweise, die zeigt, wie Sie einen Bereitstellungsschritt zu erstellen, finden Sie unter [Exemplarische Vorgehensweise: Erstellen ein benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="create-deployment-configurations"></a>Erstellen von Konfigurationen der dienstbereitstellung
 Bei einer Bereitstellungskonfiguration handelt es sich um eine Reihe von Bereitstellungsschritten. Sie werden für ein angegebenes Projekt ausgeführt, können sich aber auf alle SharePoint-Projektelemente auswirken. Jede Bereitstellungskonfiguration umfasst einen Satz an Schritten, der beim Bereitstellen des Projekts ausgeführt wird, und einen anderen Satz, der ausgeführt wird, wenn das Projekt zurückgezogen wird. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] enthält zwei integrierte Bereitstellungskonfigurationen, aber Sie können auch eigene erstellen. Beim Erstellen einer Bereitstellungskonfiguration können Sie integrierte und von Ihnen erstellte Bereitstellungsschritte einbeziehen.

 Eine exemplarische Vorgehensweise zum Erstellen einer Bereitstellungskonfiguration, veranschaulicht, finden Sie unter [Exemplarische Vorgehensweise: Erstellen ein benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Ausführen von Code bei eine SharePoint-Lösung bereitgestellt oder zurückgezogen wird
 Sie können Ereignisse verarbeiten, um zusätzliche Aufgaben auszuführen, wenn eine SharePoint-Lösung bereitgestellt oder zurückgezogen wird. Visual Studio löst Ereignisse aus, die Sie in den folgenden Szenarien behandeln können:

-   Vor und nach der Ausführung jedes Bereitstellungsschritts für ein SharePoint-Projektelement. Weitere Informationen finden Sie unter [Vorgehensweise: Ausführen von Code bei der Bereitstellung ausgeführt werden](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).

-   Vor und nach der Bereitstellung oder Zurückziehung eines SharePoint-Projekts. Weitere Informationen finden Sie unter [Vorgehensweise: Ausführen von Code beim Bereitstellen oder Zurückziehen ein SharePoint-Projekts](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).

## <a name="handle-deployment-conflicts"></a>Behandeln von Bereitstellungskonflikten
 Einige SharePoint-Projektelementtypen, einschließlich Module, Webparts, Listeninstanzen und Inhaltstypen, bieten eine integrierte Bereitstellungskonfliktlösung. Beim Bereitstellen einer Lösung, die eins dieser Projektelemente enthält, prüft Visual Studio zunächst, ob eine Datei bereits auf der SharePoint-Website mit demselben Namen, der URL oder ID wie die Datei im Element vorhanden ist, die Sie bereitstellen. Wenn ein Konflikt vorhanden ist, kann Visual Studio den Konflikt automatisch lösen, alternativ kann es Sie auffordern zu bestimmen, ob Visual Studio den Konflikt beheben oder ob die Bereitstellung abgebrochen werden soll. Weitere Informationen finden Sie unter [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

 Sie können diese Funktion erweitern, indem Sie Ihren eigenen Code bereitstellen, der nach Bereitstellungskonflikten sucht und diese behebt. Weitere Informationen finden Sie unter [Vorgehensweise: Behandeln von Bereitstellungskonflikten](../sharepoint/how-to-handle-deployment-conflicts.md).

## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Ausführen von Vorgängen vor oder nach der Bereitstellung eines Projekts
 Wenn Sie beim Bereitstellen einer SharePoint-Lösung einen Befehlszeilenvorgang ausführen möchten, können Sie die Eigenschaften <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>-Objekts festlegen. Visual Studio führt diese Befehle vor und nach der Bereitstellung des Projekts aus.

 In einigen Fällen werden möglicherweise Bereitstellungskonflikte angezeigt. Es gibt mehrere Möglichkeiten, Konflikte zu lösen. Weitere Informationen finden Sie unter [Problembehandlung bei SharePoint-Packen und-Bereitstellen](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="customize-validation-rules"></a>Anpassen von Validierungsregeln
 Vor dem Bereitstellen eines Lösungspakets (.wsp) können Sie benutzerdefinierte Funktions- und Paketvalidierungsregeln erstellen, um sicherzustellen, dass die Funktion oder das Paket gültig ist. Beispielsweise können Sie Entwicklern Informationen, Warnungen oder Fehler melden, um sie beim Beheben von Validierungsproblemen zu unterstützen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen, benutzerdefinierte Funktions- und Paketvalidierungsregeln für SharePoint-Lösungen](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Ausführen von Code bei der Bereitstellung ausgeführt werden](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Vorgehensweise: Erstellen Sie, benutzerdefinierte Funktions- und Paketvalidierungsregeln für SharePoint-Lösungen](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)
- [Erweitern von SharePoint-Projektsystem](../sharepoint/extending-the-sharepoint-project-system.md)
