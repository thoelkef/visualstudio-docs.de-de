---
title: Auswählen einer Strategie für die ClickOnce-Bereitstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c70490420855bdd160384b75d08cc27fd73e966a
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079573"
---
# <a name="choose-a-clickonce-deployment-strategy"></a>Wählen Sie eine Strategie für die ClickOnce-Bereitstellung
Es gibt drei verschiedene Strategien zum Bereitstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Anwendung. Es hängt primär von der Art der bereitzustellenden Anwendung ab, welche Strategie Sie auswählen. Folgende Strategien sind verfügbar:  
  
-   Installation aus dem Web oder einer Netzwerkfreigabe  
  
-   Installation von einer CD  
  
-   Starten der Anwendung aus dem Web oder einer Netzwerkfreigabe  
  
    > [!NOTE]
    >  Neben einer Bereitstellungsstrategie empfiehlt es sich außerdem, eine Strategie zum Bereitstellen von Anwendungsupdates auszuwählen. Weitere Informationen finden Sie unter [auswählen eine Strategie für ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="install-from-the-web-or-a-network-share"></a>Aus dem Web oder einer Netzwerkfreigabe installieren  
 Bei dieser Strategie wird die Anwendung auf einem Webserver oder in einer Dateifreigabe im Netzwerk bereitgestellt. Benutzer installieren die Anwendung, indem sie auf ein Symbol auf einer Webseite klicken oder auf ein Symbol in der Dateifreigabe doppelklicken. Die Anwendung wird dann auf den Computer des Endbenutzers heruntergeladen, installiert und gestartet. Elemente werden hinzugefügt, um die **starten** im Menü und **Programme hinzufügen oder entfernen** in **Systemsteuerung**.  
  
 Da diese Strategie von einer Netzwerkverbindung abhängt, funktioniert sie am besten bei Anwendungen, die für Benutzer bereitgestellt werden, die Zugriff auf ein lokales Netzwerk haben oder eine Internetverbindung mit hoher Geschwindigkeit besitzen.  
  
 Wenn Sie die Anwendung aus dem Web bereitstellen, können Sie Argumente in die Anwendung übergeben, wenn sie mit einer URL aktiviert wird. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen von Abfragezeichenfolgen-Informationen in einer online-ClickOnce-Anwendung](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Sie können keine Argumente in eine Anwendung übergeben, die mit einer der anderen in diesem Dokument beschriebenen Methoden aktiviert wird.  
  
 So aktivieren Sie diese Bereitstellungsstrategie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], klicken Sie auf **aus dem Internet** oder **von UNC-Pfad oder Dateifreigabe** auf die **Installationsart** Seite des Webpublishing-Assistenten.  
  
 Dies ist die Standardbereitstellungsstrategie.  
  
## <a name="start-the-application-from-the-web-or-a-network-share"></a>Starten Sie die Anwendung aus dem Web oder einer Netzwerkfreigabe  
 Diese Strategie ähnelt der ersten Strategie. Die Anwendung verhält sich jedoch wie eine Webanwendung. Wenn der Benutzer auf einer Webseite auf einen Link klickt (oder in einer Dateifreigabe auf ein Symbol doppelklickt), wird die Anwendung gestartet. Wenn Benutzer die Anwendung schließen, ist es nicht mehr auf ihrem lokalen Computer zur Verfügung; wird nichts hinzugefügt, um die **starten** im Menü oder **Software** in **Systemsteuerung**.  
  
> [!NOTE]
>  Technisch gesehen wird die Anwendung in einen Anwendungscache auf dem lokalen Computer heruntergeladen und dort installiert, genauso wie eine Webanwendung in den Webcache heruntergeladen wird. Wie beim Webcache werden die Dateien letztendlich aus dem Anwendungscache gelöscht. Der Benutzer empfindet es jedoch so, als ob die Anwendung aus dem Web oder der Dateifreigabe ausgeführt wird.  
  
 Diese Strategie funktioniert am besten bei Anwendungen, die selten verwendet werden, z. B. ein Tool zum Berechnen von Lohnzusatzleistungen für Angestellte, das i. d. R. nur einmal im Jahr ausgeführt wird.  
  
 So aktivieren Sie diese Bereitstellungsstrategie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], klicken Sie auf **installieren Sie die Anwendung nicht** auf die **Web installieren oder Ausführen von** Seite des Webpublishing-Assistenten.  
  
 Um diese Bereitstellungsstrategie manuell zu aktivieren, Ändern der **installieren** -Tag im Bereitstellungsmanifest. (Die Werte sind möglich **"true"** oder **"false"**. In *Mage.exe*, verwenden Sie die **nur Online** option die **Anwendungstyp** Liste.)  

## <a name="install-from-a-cd"></a>Installation von einer CD  
 Bei dieser Strategie wird die Anwendung auf einem Wechseldatenträger bereitgestellt, z. B. auf einer CD-ROM oder einer DVD. Wie bei der vorherigen Option, wenn der Benutzer entscheidet, die die Anwendung zu installieren, es installiert und gestartet wird und Elemente hinzugefügt werden die **starten** Menü und **Software** in **Steuerelement Bereich**.  
  
 Diese Strategie funktioniert am besten bei Anwendungen, die für Benutzer bereitgestellt werden, die nicht dauerhaft über eine Netzwerkverbindung oder über eine Verbindung mit niedriger Bandbreite verfügen. Da die Anwendung von einem Wechseldatenträger installiert wird, ist bei der Installation keine Netzwerkverbindung erforderlich. Sie benötigen jedoch eine Netzwerkverbindung für Anwendungsupdates.  
  
 So aktivieren Sie diese Bereitstellungsstrategie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], klicken Sie auf **von CD-ROM oder DVD-ROM** auf die **Installationsart** Seite des Webpublishing-Assistenten.  
  
 Um diese Bereitstellungsstrategie manuell zu aktivieren, Ändern der **"deploymentProvider"** -Tag im Bereitstellungsmanifest. (In Visual Studio diese Eigenschaft verfügbar gemacht wird als **Installations-URL** auf die **veröffentlichen** im Projekt-Designer auf der Seite. In *Mage.exe* ist **Startposition**.)  
  
## <a name="web-browser-support"></a>Webbrowserunterstützung  
 Anwendungen, die auf .NET Framework 3.5 ausgerichtet sind, können mit jedem Browser installiert werden.  
  
 Anwendungen, die auf .NET Framework 2.0 ausgerichtet sind, erfordern Internet Explorer.  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Auswählen einer Strategie für ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Gewusst wie: veröffentlichen eine ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)