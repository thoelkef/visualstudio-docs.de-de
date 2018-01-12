---
title: "Unterschiede zwischen Sandkasten- und Farmlösungen | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c9123f028bab5319f47e4bdc0ada0dbbee49bc2c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Unterschiede zwischen Sandkasten- und Farmlösungen
  Beim Kompilieren einer SharePoint-Lösung bereitgestellt wird, auf dem SharePoint-Server und ein Debugger angehängt, um es zu debuggen. Der Prozess zum Debuggen der Projektmappe verwendet, hängt von der Einstellung der Eigenschaft Sandkastenlösung: sandkastenlösung oder farmlösung.  
  
 Weitere Informationen finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Farmlösungen  
 Farmlösungen, die in der IIS-Arbeitsprozess (W3WP.exe) gehostet werden, führen Sie Code, der die gesamte Farm auswirken kann. Wenn Sie ein SharePoint-Projekt debuggen, deren Sandkastenlösung-Eigenschaft auf "farmlösung" festgelegt ist, verwendet das System IIS-Anwendungspool wieder, bevor SharePoint zurückgezogen oder die Funktion stellt, um alle vom IIS-Arbeitsprozess gesperrte Dateien freigegeben. Nur der IIS-Anwendungspool für die Website-URL der SharePoint-Projekt wird wiederverwendet.  
  
## <a name="sandboxed-solutions"></a>Sandkastenlösungen  
 Sandkastenlösungen, die in SharePoint Benutzer Code Lösung Worker Prozess (SPUCWorkerProcess.exe) gehostet werden, führen Sie Code, der nur die Websitesammlung der Lösung auswirken kann. Weil sandkastenlösungen nicht in der IIS-Arbeitsprozess ausgeführt werden, muss weder den IIS-Server als auch der IIS-Anwendungspool neu starten. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Fügt der Debugger an den SPUCWorkerProcess-Prozess, der der SPUserCodeV4-Dienst in SharePoint automatisch ausgelöst und die Steuerelemente. Es ist nicht erforderlich, für den SPUCWorkerProcess-Prozess wiederverwendet, um die neueste Version der Projektmappe zu laden.  
  
## <a name="either-type-of-solution"></a>Geben Sie entweder der Lösung  
 Mit beiden Lösungstyp [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wird auch der Debugger an den Browser anzuweisen, clientseitiges Skriptdebuggen zu aktivieren. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Das Skript Debugmodul für diesen Zweck verwendet. Um Debuggen zu aktivieren, müssen Sie die Standardeinstellungen für den Browser ändern, wenn Sie aufgefordert werden.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Fügt der Debugger nur an die W3WP oder SPUCWorkerProcess-Prozesse, die mit dem aktuellen Standort an. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Außerdem fügt der verwalteten COM-Plus- und Debugmodule Workflow.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md)   
 [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md)  
  
  