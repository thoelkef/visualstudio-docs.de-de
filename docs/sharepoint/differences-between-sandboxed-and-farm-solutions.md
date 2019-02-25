---
title: Unterschiede zwischen Sandkasten- und Farmlösungen | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 073e62b473ebfcec5f71ae1907e8f9e385333411
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596646"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Unterschiede zwischen Sandkasten- und farmlösungen
  Beim Kompilieren einer SharePoint-Lösung auf der SharePoint-Server bereitgestellt, und fügt ein Debugger zum Debuggen. Der Prozess zum Debuggen der Projektmappe verwendet, hängt von der Einstellung der Eigenschaft der Sandkastenlösung: sandkastenlösung oder farmlösung.

 Weitere Informationen finden Sie unter [Überlegungen zu sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).

## <a name="farm-solutions"></a>Farmlösungen
 Farmlösungen, die in der IIS-Arbeitsprozess (W3WP.exe) gehostet werden, führen Sie Code, der die gesamte Farm auswirken kann. Wenn Sie ein SharePoint-Projekt debuggen, dessen Eigenschaft der Sandkastenlösung auf "farmlösung" festgelegt ist, werden des Systems IIS-Anwendungspool wird wiederverwendet, bevor SharePoint zurückgezogen oder die Funktion stellt, um alle Dateien, die von der IIS-Arbeitsprozess gesperrt freizugeben. Nur der IIS-Anwendungspool für das SharePoint-Projekt-Site-URL wird wiederverwendet.

## <a name="sandboxed-solutions"></a>Sandbox-Lösungen
 Sandbox-Lösungen, die in der SharePoint User Code Lösung Worker-Prozess (SPUCWorkerProcess.exe) gehostet werden, führen Sie Code, der nur die Websitesammlung in der Lösung auswirken kann. Weil Sandbox-Lösungen nicht in der IIS-Arbeitsprozess ausgeführt werden, muss weder den IIS-Server als auch der IIS-Anwendungspool neu starten. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt den Debugger an den SPUCWorkerProcess-Prozess, der SPUserCodeV4-Dienst in SharePoint automatisch ausgelöst, und die Steuerelemente an. Es ist nicht erforderlich, für den Prozess SPUCWorkerProcess wiederzuverwenden, um die neueste Version der Projektmappe zu laden.

## <a name="either-type-of-solution"></a>Beide Arten von Projektmappen
 Mit beiden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt auch den Debugger an den Browser So aktivieren Sie clientseitiges Skript zu debuggen. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verwendet das Skript-Engine für diesen Zweck zu debuggen. Zum Debuggen von Skripts zu aktivieren, müssen Sie die Standardeinstellungen für den Browser ändern, wenn Sie aufgefordert werden.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt den Debugger nur an die W3WP oder SPUCWorkerProcess Prozesse, die mit dem aktuellen Standort an. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Außerdem fügt die verwaltete COM Plus und den Workflow, die Debug-Engines.

## <a name="see-also"></a>Siehe auch
- [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md)
- [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Überlegungen zu sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md)
