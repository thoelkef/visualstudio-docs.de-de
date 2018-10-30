---
title: Problembehandlung bei Help Viewer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3497d46ed4c9c5a04d8f40cc3056ea282593884
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934235"
---
# <a name="troubleshooting-the-help-viewer"></a>Problembehandlung bei Help Viewer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema werden Probleme behandelt, die bei der Verwendung des Help Viewers auftreten können.  
  
## <a name="audio-doesnt-work"></a>Audio funktioniert nicht.  
 Der Help Viewer enthält keinen Audioplayer. Wenn Sie Inhalte herunterladen, die Audiodaten enthalten, und nichts passiert, wenn Sie auf **Wiedergeben** klicken, installieren Sie einen Audioplayer.  
  
## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>Suche funktioniert nicht in Windows Server 2008, Windows Server 2008 mit SP1 oder Windows Server 2008 R2.  
 Für die Such- und Filterfunktionen in Help Viewer muss der Dienst Windows Search installiert und verfügbar sein. Standardmäßig ist dieser Dienst in Windows Server 2008, Windows Server 2008 mit Service Pack 1 (SP1) und Windows Server 2008 R2 deaktiviert.  
  
#### <a name="to-activate-windows-search-service"></a>So aktivieren Sie den Windows Search-Dienst  
  
1.  Starten Sie den Server-Manager.  
  
2.  Klicken Sie im linken Navigationsbereich auf **Rollen**.  
  
3.  Wählen Sie im Bereich „Rollenübersicht“ die Option **Rolle hinzufügen** aus.  
  
4.  Wählen Sie die Rolle „Dateidienste“ aus, und klicken Sie dann auf **Weiter**.  
  
5.  Wählen Sie den Windows Search-Rollendienst aus.  
  
## <a name="additional-resources"></a>Zusätzliche Ressourcen  
 Mithilfe der folgenden Ressourcen können Sie weitere Informationen abrufen und Feedback zum Help Viewer bereitstellen:  
  
- Sie können auf der Microsoft-Website unter [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) Feedback einreichen, oder Sie senden eine E-Mail an [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).  
  
- Weitere Informationen finden Sie unter den [Developer Documentation and Help System](http://go.microsoft.com/fwlink/?LinkId=232741) Forum und [The Help Guy](http://go.microsoft.com/fwlink/?LinkId=232743) Blog.  
  
## <a name="see-also"></a>Siehe auch  
 [Help Viewer 2.1-Administratorhandbuch](http://go.microsoft.com/fwlink/?LinkId=243985)



