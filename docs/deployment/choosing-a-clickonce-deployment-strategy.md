---
title: "Auswählen einer Strategie für die ClickOnce-Bereitstellung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
caps.latest.revision: "19"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: fffb73fac64aad880531fb8ea51904fb5ac71b16
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="choosing-a-clickonce-deployment-strategy"></a>Auswählen einer Strategie für die ClickOnce-Bereitstellung
Es gibt drei verschiedene Strategien zum Bereitstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Anwendung. Es hängt primär von der Art der bereitzustellenden Anwendung ab, welche Strategie Sie auswählen. Folgende Strategien sind verfügbar:  
  
-   Installation aus dem Web oder einer Netzwerkfreigabe  
  
-   Installation von einer CD  
  
-   Starten der Anwendung aus dem Web oder einer Netzwerkfreigabe  
  
    > [!NOTE]
    >  Neben einer Bereitstellungsstrategie empfiehlt es sich außerdem, eine Strategie zum Bereitstellen von Anwendungsupdates auszuwählen. Weitere Informationen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="install-from-the-web-or-a-network-share"></a>Installation aus dem Web oder einer Netzwerkfreigabe  
 Bei dieser Strategie wird die Anwendung auf einem Webserver oder in einer Dateifreigabe im Netzwerk bereitgestellt. Benutzer installieren die Anwendung, indem sie auf ein Symbol auf einer Webseite klicken oder auf ein Symbol in der Dateifreigabe doppelklicken. Die Anwendung wird dann auf den Computer des Endbenutzers heruntergeladen, installiert und gestartet. Elemente werden hinzugefügt, um die **starten** im Menü und **Software** in **Systemsteuerung**.  
  
 Da diese Strategie von einer Netzwerkverbindung abhängt, funktioniert sie am besten bei Anwendungen, die für Benutzer bereitgestellt werden, die Zugriff auf ein lokales Netzwerk haben oder eine Internetverbindung mit hoher Geschwindigkeit besitzen.  
  
 Wenn Sie die Anwendung aus dem Web bereitstellen, können Sie Argumente in die Anwendung übergeben, wenn sie mit einer URL aktiviert wird. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen von Abfragezeichenfolgen-Informationen in einer Online-ClickOnce-Anwendung](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Sie können keine Argumente in eine Anwendung übergeben, die mit einer der anderen in diesem Dokument beschriebenen Methoden aktiviert wird.  
  
 So aktivieren Sie diese Bereitstellungsstrategie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], klicken Sie auf **aus dem Internet** oder **von UNC-Pfad oder Dateifreigabe** auf die **Installationsart** Seite des Veröffentlichungs-Assistenten.  
  
 Dies ist die Standardbereitstellungsstrategie.  
  
## <a name="install-from-a-cd"></a>Installation von einer CD  
 Bei dieser Strategie wird die Anwendung auf einem Wechseldatenträger bereitgestellt, z. B. auf einer CD-ROM oder einer DVD. Wie bei der vorausgegangenen Option, wenn der Benutzer entscheidet, die Anwendung zu installieren, installiert und gestartet und Elemente hinzugefügt werden die **starten** Menü und **Software** in **Steuerelement Bereich**.  
  
 Diese Strategie funktioniert am besten bei Anwendungen, die für Benutzer bereitgestellt werden, die nicht dauerhaft über eine Netzwerkverbindung oder über eine Verbindung mit niedriger Bandbreite verfügen. Da die Anwendung von einem Wechseldatenträger installiert wird, ist bei der Installation keine Netzwerkverbindung erforderlich. Sie benötigen jedoch eine Netzwerkverbindung für Anwendungsupdates.  
  
 So aktivieren Sie diese Bereitstellungsstrategie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], klicken Sie auf **von CD-ROM oder DVD-ROM** auf die **Installationsart** Seite des Veröffentlichungs-Assistenten.  
  
 Um diese Bereitstellungsstrategie manuell zu aktivieren, Ändern der **"deploymentProvider"** -Tag im Bereitstellungsmanifest. (In Visual Studio diese Eigenschaft verfügbar gemacht wird als **Installations-URL** auf die **veröffentlichen** Seite im Projekt-Designer. In Mage.exe lautet **Startspeicherort**.)  
  
## <a name="start-the-application-from-the-web-or-a-network-share"></a>Starten der Anwendung aus dem Web oder einer Netzwerkfreigabe  
 Diese Strategie ähnelt der ersten Strategie. Die Anwendung verhält sich jedoch wie eine Webanwendung. Wenn der Benutzer auf einer Webseite auf einen Link klickt (oder in einer Dateifreigabe auf ein Symbol doppelklickt), wird die Anwendung gestartet. Wenn Benutzer die Anwendung schließen, ist nicht mehr auf ihren lokalen Computer verfügbar. nichts hinzugefügt der **starten** Menü oder **Software** in **Systemsteuerung**.  
  
> [!NOTE]
>  Technisch gesehen wird die Anwendung in einen Anwendungscache auf dem lokalen Computer heruntergeladen und dort installiert, genauso wie eine Webanwendung in den Webcache heruntergeladen wird. Wie beim Webcache werden die Dateien letztendlich aus dem Anwendungscache gelöscht. Der Benutzer empfindet es jedoch so, als ob die Anwendung aus dem Web oder der Dateifreigabe ausgeführt wird.  
  
 Diese Strategie funktioniert am besten bei Anwendungen, die selten verwendet werden, z. B. ein Tool zum Berechnen von Lohnzusatzleistungen für Angestellte, das i. d. R. nur einmal im Jahr ausgeführt wird.  
  
 So aktivieren Sie diese Bereitstellungsstrategie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], klicken Sie auf **installieren Sie die Anwendung nicht** auf die **Web installieren oder Ausführen von** Seite des Veröffentlichungs-Assistenten.  
  
 Um diese Bereitstellungsstrategie manuell zu aktivieren, Ändern der **installieren** -Tag im Bereitstellungsmanifest. (Der Wert kann **"true"** oder **"false"**. Verwenden Sie in Mage.exe die **nur Online** -Option in der **Anwendungstyp** Liste.)  
  
## <a name="web-browser-support"></a>Unterstützung für Internetbrowser  
 Anwendungen, die auf .NET Framework 3.5 ausgerichtet sind, können mit jedem Browser installiert werden.  
  
 Anwendungen, die auf .NET Framework 2.0 ausgerichtet sind, erfordern Internet Explorer.  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)