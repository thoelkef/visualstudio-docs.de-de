---
redirect_url: /visualstudio/ide/microsoft-help-viewer
ms.openlocfilehash: c0b1a114eb157860dd70873929727cc56f1d6514
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
title: "Problembehebung bei Help Viewer | Microsoft-Dokumentation" ms.custom: "" ms.date: "4.11.2016" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "Artikel" helpviewer_keywords: 
  - "Problembehebung [Help Viewer]"
  - "Help Viewer, Problembehebung" ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12 caps.latest.revision: 13 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="troubleshooting-the-help-viewer"></a>Problembehandlung bei Help Viewer
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
  
-   Sie können auf der Microsoft-Website unter [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) Feedback einreichen, oder Sie senden eine E-Mail an [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).  
  
-   Weitere Informationen finden Sie im Forum [Developer Documentation and Help System (Entwicklerdokumentation und Hilfe)](http://go.microsoft.com/fwlink/?LinkId=232741).  
  
## <a name="see-also"></a>Siehe auch
[Help Viewer-Administratorhandbuch](http://go.microsoft.com/fwlink/?LinkId=243985)