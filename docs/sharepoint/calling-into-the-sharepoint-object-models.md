---
title: Aufrufe in der SharePoint-Objektmodelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3afb988b226ccf62fae92ab02d8380d20b19605b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853428"
---
# <a name="call-into-the-sharepoint-object-models"></a>Rufen Sie in der SharePoint-Objektmodelle
  Wenn Sie Erweiterungen für die SharePoint-Tools in Visual Studio erstellen, müssen Sie möglicherweise zum Aufrufen der SharePoint-APIs, um bestimmte Aufgaben ausführen. Bei der Erstellung eines benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte möglicherweise Sie z. B. SharePoint-APIs zum Ausführen einiger Aufgaben zum Bereitstellen von Lösungen aufgerufen.  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] und [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] bieten zwei unterschiedliche Objektmodelle, die Sie in der SharePoint-Tools-Erweiterungen verwenden können: ein Serverobjektmodell und ein Clientobjektmodell. Beide Objektmodelle haben vor- und Nachteile im Kontext der SharePoint-Tools-Erweiterungen.  
  
 Eine Übersicht über die SharePoint-Objektmodelle, finden Sie unter [Übersicht über das Programmiermodell von SharePoint-tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="use-the-client-object-model-in-extension-projects"></a>Verwenden Sie das Clientobjektmodell in Erweiterungsprojekten
 Wenn Sie eine Erweiterung für die SharePoint-Tools entwickeln, können Sie das Clientobjektmodell in Ihrem Projekt wie jeden anderen Satz von verwalteten APIs. Sie können Verweise auf Assemblys in das Clientobjektmodell zu Ihrem Projekt hinzufügen, und Sie können die APIs in das Clientobjektmodell aufrufen, direkt aus Ihrem Code.  
  
 Das Clientobjektmodell hat jedoch zwei Nachteile im Kontext der SharePoint-Tools-Erweiterungen:  
  
- Das Client-Objektmodell bietet nur eine Teilmenge des Server-Objektmodells. Wenn Sie SharePoint-Funktionen verwenden, die nicht im Client-Objektmodell verfügbar gemacht haben, müssen Sie das Serverobjektmodell verwenden.  
  
- Aber verwenden das Clientobjektmodell in SharePoint-Tools-Erweiterungen in den meisten Fällen funktionieren sollte, können einige Szenarien auftreten, in denen Aufrufe an die Client-Objektmodell nicht wie erwartet funktionieren. Das Clientobjektmodell ist in Clientanwendungen zum Aufrufen der SharePoint-Websites auf einem Remoteserver oder die Farm verwendet werden soll. SharePoint-Tools in Visual Studio funktionieren nur mit einer lokalen SharePoint-Installation auf dem Entwicklungscomputer. Aus diesem Grund, wenn Sie das Clientobjektmodell in einer SharePoint-Tools-Erweiterung verwenden, rufen Sie in einer SharePoint-Website auf dem lokalen Computer, handelt es sich nicht wie das Clientobjektmodell entworfen wurde, verwendet werden soll.  
  
  Eine exemplarische Vorgehensweise, die zeigt, wie Sie das Clientobjektmodell in eine Erweiterung der SharePoint-Tools in Visual Studio verwenden, finden Sie unter [Exemplarische Vorgehensweise: Rufen Sie in der SharePoint-Clientobjektmodell innerhalb einer Server-explorererweiterung](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="use-the-server-object-model-in-extension-projects"></a>Verwenden Sie das Serverobjektmodell in Erweiterungsprojekten
 Das Serverobjektmodell ist eine Obermenge des Client-Objektmodells. Wenn Sie das Serverobjektmodell verwenden, können Sie alle Funktionen, die [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] und [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] programmgesteuert verfügbar machen.  

 SharePoint-Tools-Erweiterungen können APIs in das Serverobjektmodell verwenden, aber sie können die APIs direkt aufrufen. Das Serverobjektmodell kann nur von einem 64-Bit-Prozess, der .NET Framework 3.5 abzielt aufgerufen werden. SharePoint-Tools-Erweiterungen erfordern jedoch die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und sie werden in der 32-Bit-Visual Studio-Prozess ausgeführt. Dadurch wird verhindert, dass SharePoint-Tools-Erweiterungen verweisen Sie direkt auf die Assemblys in der SharePoint-Serverobjektmodell.  
  
 Wenn Sie das Serverobjektmodell in einer SharePoint-Tools-Erweiterung verwenden möchten, müssen Sie erstellen eine benutzerdefinierte *SharePoint-Befehls* zum Aufrufen der API. Sie definieren den SharePoint-Befehl in einer sekundären Assembly, die direkt in das Serverobjektmodell aufrufen können. In Ihrem Erweiterungsprojekt, Sie rufen den SharePoint-Befehl indirekt mit der ExecuteCommand-Methode der ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> Objekt.  
  
 Weitere Informationen zum Erstellen und verwenden die SharePoint-Befehle finden Sie unter [Vorgehensweise: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md) und [wie: Ausführen einer SharePoint-Befehls](../sharepoint/how-to-execute-a-sharepoint-command.md). Informationen zum Bereitstellen von SharePoint-Befehle finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Exemplarische Vorgehensweisen, die veranschaulichen, wie zum Erstellen und verwenden die SharePoint-Befehle finden Sie unter [Exemplarische Vorgehensweise: erstellen ein benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) und [Exemplarische Vorgehensweise: Server-Explorer erweitern, um die Anzeige von Webparts ](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### <a name="understand-how-sharepoint-commands-are-executed"></a>Verstehen Sie, wie die SharePoint-Befehle ausgeführt werden
 Assemblys, die SharePoint-Befehle definieren werden geladen, in einem 64-Bit-Hostprozess, der mit dem Namen *vssphost4.exe*. Nach dem Aufruf eines SharePoint-Befehls in einer SharePoint-Tools-Erweiterung wird der Befehl ausgeführt, indem *vssphost4.exe* statt an den 32-Bit-Visual Studio-Prozess (*devenv.exe*). Sie können steuern, einige Aspekte wie SharePoint-Befehle ausgeführt werden, indem Sie Werte in der Registrierung festlegen. Weitere Informationen finden Sie unter [-Erweiterungen für SharePoint-Tools in Visual Studio Debuggen](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch
 [Gewusst wie: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Gewusst wie: Ausführen einer SharePoint-Befehls](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Übersicht über das Programmiermodell von SharePoint-tools extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
