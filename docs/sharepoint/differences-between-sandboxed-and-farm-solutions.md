---
title: Unterschiede zwischen Sandkasten-und Farm Lösungen | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967545"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Unterschiede zwischen Sandkasten-und Farm Lösungen
  Wenn Sie eine SharePoint-Lösung kompilieren, wird Sie auf dem SharePoint-Server bereitgestellt, und ein Debugger wird zum Debuggen angefügt. Der Prozess, der zum Debuggen der Projekt Mappe verwendet wird, hängt von der Einstellung der Sandkasten Lösungs Eigenschaft ab: Sandkasten Lösung oder Farm Lösung.

 Weitere Informationen finden Sie unter [Überlegungen zu Sandkasten Lösungen](../sharepoint/sandboxed-solution-considerations.md).

## <a name="farm-solutions"></a>Farm Lösungen
 Farm Lösungen, die im IIS-Arbeitsprozess (W3WP.exe) gehostet werden, führen Code aus, der sich auf die gesamte Farm auswirken kann. Wenn Sie ein SharePoint-Projekt Debuggen, dessen Sandbox-Projektmappeneigenschaft auf "Farm Lösung" festgelegt ist, wird der IIS-Anwendungs Pool des Systems wieder verwendet, bevor SharePoint die Funktion zurückzieht oder bereitstellt, um alle Dateien freizugeben, die vom IIS-Arbeitsprozess gesperrt sind. Nur der IIS-Anwendungs Pool für die Website-URL des SharePoint-Projekts wird wieder verwendet.

## <a name="sandboxed-solutions"></a>Sandkasten Lösungen
 Sandbox-Lösungen, die im SharePoint-Arbeitsprozess für Benutzercode Lösungen (SPUCWorkerProcess.exe) gehostet werden, führen Code aus, der sich nur auf die Website Sammlung der Projekt Mappe auswirkt. Da Sandkasten Lösungen nicht im IIS-Arbeitsprozess ausgeführt werden, muss weder der IIS-Anwendungs Pool noch der IIS-Server neu gestartet werden. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt den Debugger an den SPUCWorkerProcess-Prozess an, der vom spusercodev4 zuzulassen-Dienst in SharePoint automatisch ausgelöst und gesteuert wird. Es ist nicht erforderlich, dass der SPUCWorkerProcess-Prozess wieder verwendet wird, um die neueste Version der Lösung zu laden.

## <a name="either-type-of-solution"></a>Beide Arten von Projektmappen
 Bei jedem Lösungstyp [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt den Debugger auch an den Browser an, um das Client seitige Skript Debuggen zu aktivieren. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verwendet die Skript-debuggingengine zu diesem Zweck. Um das Skript Debugging zu aktivieren, müssen Sie die Standardbrowser Einstellungen ändern, wenn Sie dazu aufgefordert werden.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt den Debugger nur an die w3wp-oder SPUCWorkerProcess-Prozesse an, die die aktuelle Website ausführen. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Außerdem werden die verwalteten com Plus-und Workflow-debugengines angefügt.

## <a name="see-also"></a>Weitere Informationen
- [SharePoint-Lösungen Debuggen](../sharepoint/debugging-sharepoint-solutions.md)
- [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Überlegungen zu Sandkasten Lösungen](../sharepoint/sandboxed-solution-considerations.md)
